## Declarative Pipelines in Jenkins

**Declarative Pipelines** in Jenkins are a more recent and user-friendly way to define pipelines. They provide a simpler and more structured syntax compared to Scripted Pipelines. Here are some key points:

### Structure
Declarative Pipelines are defined within a `pipeline` block. The basic structure looks like this:

```groovy
pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
```

### Sections

-  **agent**: Specifies where the pipeline or a specific stage will run.

-  **stages**: Defines the stages of the pipeline.

-  **steps**: Contains the actual steps to be executed within a stage.

### Directives

Declarative Pipelines use high-level directives to include additional logic, such as setting environment variables, parameters, and triggers.

#### Advantages

1.  **Simplicity**: Easier to read and write compared to Scripted Pipelines.

1.  **Structure**: Provides a clear structure, making it easier to understand and maintain.

1.  **Error Handling**: Built-in support for error handling and retry mechanisms.

### Example

Here's a simple example

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo Building...'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Testing...'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploying...'
            }
        }
    }
}
```
