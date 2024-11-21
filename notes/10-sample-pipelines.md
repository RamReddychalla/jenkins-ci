## Sample Jenkins Pipelines

### .Net 8 projects

```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-repo/your-dotnet-project.git'
            }
        }
        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build') {
            steps {
                bat 'dotnet build -c Release'
            }
        }
        stage('Test') {
            steps {
                bat 'dotnet test --no-restore --verbosity normal'
            }
        }
        stage('Publish') {
            steps {
                bat 'dotnet publish -c Release -o ./publish'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: './publish/**', fingerprint: true
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}

```

## React (JS) project using NodeJS Platform for build

```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-repo/your-react-project.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment steps here
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
```

## Python `flask` web project

```groovy
pipeline {
    agent any
    environment {
        VENV_DIR = 'venv'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-repo/your-flask-app.git'
            }
        }
        stage('Setup Python Environment') {
            steps {
                sh '''
                    python3 -m venv $VENV_DIR
                    . $VENV_DIR/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Linting') {
            steps {
                sh '''
                    . $VENV_DIR/bin/activate
                    flake8 .
                '''
            }
        }
        stage('Testing') {
            steps {
                sh '''
                    . $VENV_DIR/bin/activate
                    pytest
                '''
            }
        }
        stage('Packaging') {
            steps {
                sh '''
                    . $VENV_DIR/bin/activate
                    python setup.py sdist bdist_wheel
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment steps here, such as uploading to a server
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed.'
        }
        cleanup {
            sh 'rm -rf $VENV_DIR'
        }
    }
}
```