## Jenkins Job: Freestyle Project

### Overview
A Freestyle Project in Jenkins is the simplest way to configure and run a job. It provides a flexible, easy-to-use interface for defining a variety of tasks, from building code to running scripts and automating processes. 

### Key Features
- **Source Code Management**: Integrate with various SCM systems like Git, Subversion, etc.
- **Build Triggers**: Configure how and when the job should be triggered. Options include scheduling (cron), SCM changes, upstream/downstream projects, and manual triggers.
- **Build Environment**: Set up the environment required for the build, such as preparing the workspace or setting environment variables.
- **Build Steps**: Define one or more steps to execute during the build process. These can include running shell scripts, invoking other build tools like Ant or Maven, and more.
- **Post-build Actions**: Specify actions to perform after the build completes. This can include archiving artifacts, sending notifications, and running downstream projects.

### Example Configuration
Here’s a simple example of how you might configure a Freestyle Project:

1. **Project Name**: Give your project a meaningful name, like "Job1".
2. **Source Code Management (SCM)**:
    - For this demo, select "NONE" 
3. **Build Triggers**:
    - Set up how the build should be triggered. For example, select "Poll SCM" and specify a schedule using cron syntax.
    - for this demo, we should not use any trigger!
4. **Build Environment**:
    - Configure any environment settings needed for the build, such as environment variables.
    - This basic demo, we have no environment variables.
5. **Build Steps**:
    - Add a build step to execute a Windows Batch command.
    - Example: `echo "Hello World"`
6. **Post-build Actions**:
    - Add actions such as "Archive the artifacts" to save the build outputs.
    - Configure notifications like email alerts to notify stakeholders of the build results.
    - This demo we should skip this option as well.

### Advantages
- **Simplicity**: Easy to set up and use, even for those new to Jenkins.
- **Flexibility**: Can accommodate a wide range of build and automation tasks.
- **Extensibility**: Integrates well with various plugins and tools, allowing for extensive customization.

### Limitations
- **Scalability**: While suitable for simple builds, complex build processes might benefit from more advanced project types like Pipeline projects.
- **Modularity**: Less modular compared to Pipeline projects, which allow for more reusable and maintainable configurations.


### Jenkins Home Directory Structure for Jobs

- JENKINS_HOME/jobs: Contains all job-specific directories.

- JENKINS_HOME/jobs/&lt;job-name&gt;: Each job has its own directory named after the job.

- JENKINS_HOME/jobs/&lt;job-name&gt;/builds: Contains directories for each build of the job.

- JENKINS_HOME/jobs/&lt;job-name&gt;/builds/&lt;build_number&gt;: Each build directory is named after its build number and contains specific build-related files:

- JENKINS_HOME/jobs/&lt;job-name&gt;/builds/&lt;build_number&gt;/build.xml: Contains detailed information about the build.

- JENKINS_HOME/jobs/&lt;job-name&gt;/builds/&lt;build_number&gt;/changelog.xml: Contains the changelog for the build.

- JENKINS_HOME/jobs/&lt;job-name&gt;/builds/&lt;build_number&gt;/log: The console output for the build.

- JENKINS_HOME/workspace/&lt;job-name&gt;: Temporary workspace used during the build process.

### Conclusion
Freestyle Projects are a great starting point for Jenkins users, offering a straightforward way to configure and run jobs. As your needs grow, you may explore more advanced job types like Pipelines for better scalability and maintainability.

