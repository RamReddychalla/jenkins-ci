# Jenkins Plugins

Jenkins plugins are the primary means of extending the functionality of Jenkins[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/). They allow you to integrate various tools, automate tasks, and customize your Jenkins environment to suit your specific needs[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/). There are over a thousand plugins available, covering a wide range of functionalities[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).

## Managing Plugins

### Installing Plugins
1. **Using the Web UI**:
   - Navigate to **Manage Jenkins** > **Manage Plugins**[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Go to the **Available** tab and search for the desired plugin[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Check the box next to the plugin and click **Install without restart**[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Restart Jenkins if required[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).

2. **Using the Jenkins CLI**:
   - Use the `install-plugin` command to install plugins from the command line[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Example:
    
   ```sh
   java -jar jenkins-cli.jar -s http://localhost:8080/ install-plugin <plugin-name>
   ```

### Updating Plugins
1. **Using the Web UI**:
   - Navigate to **Manage Jenkins** > **Manage Plugins**[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Go to the **Installed** tab and click **Update Now**[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Restart Jenkins if required[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).

2. **Using the Jenkins CLI**:
   - Use the `upgrade-plugin` command to update plugins from the command line[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Example:
     ```sh
     java -jar jenkins-cli.jar -s http://localhost:8080/ upgrade-plugin <plugin-name>
     ```

### Removing Plugins
1. **Using the Web UI**:
   - Navigate to **Manage Jenkins** > **Manage Plugins**[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Go to the **Installed** tab and select the plugin to be removed[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Click **Uninstall** and restart Jenkins if required[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).

2. **Using the Jenkins CLI**:
   - Use the `remove-plugin` command to remove plugins from the command line[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
   - Example:
     ```sh
     java -jar jenkins-cli.jar -s http://localhost:8080/ remove-plugin <plugin-name>
     ```

## Popular Plugins

- **Git**: Integrates Jenkins with Git repositories[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
- **Maven**: Supports building projects with Maven[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
- **Junit**: Publishes JUnit test results[Managing Plugins - Jenkins](https://www.jenkins.io/doc/book/managing/plugins/).
- **Pipeline**: Allows defining build pipelines as code[Jenkins User Documentation](https://www.jenkins.io/doc/).
- **Blue Ocean**: Provides a modern user interface for Jenkins[Jenkins User Documentation](https://www.jenkins.io/doc/).

## Resources
- [Jenkins User Documentation](https://www.jenkins.io/doc/)
- [Managing Plugins](https://www.jenkins.io/doc/book/managing/plugins/)
- [Jenkins Plugins](https://plugins.jenkins.io/)

