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
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo `Deploying...'
            }
        }
    }
}
```

### How to create pipeline project 

1.  In Jenkins Dashboard, click on `New Item`
1.  In `Item name` enter `Job5`. In `Item Type` select `Pipeline`

    > If you cant see item type `Pipeline` then you must install `Pipeline` plugin first!

1.  Click `OK` button
1.  In `Pipeline` type items, you get only three sections

    - General : Similar to `Freestyle` items
    - Advanced Project Options: Depends on Plugins installed, Only display name is available by default.
    - Pipeline: You can either provide `Pipeline Text` or Pick pipeline from SCM

1.  Choose `Pipeline Script` from dropdown box.
1.  Copy following text:

    ```groovy
    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    echo 'Building...'
                }
            }
            stage('Test') {
                steps {
                    echo 'Testing...'
                }
            }
            stage('Deploy') {
                steps {
                    echo 'Deploying...'
                }
            }
        }
    }
    ```

1.  Click `Save` Button and then `Build Now`
1.  Click on Recent build number and use either one option:

    - Open BlueOcean
    - Pipeline Console
