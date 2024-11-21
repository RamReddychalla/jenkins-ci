# How to Create a GitHub PAT and Integrate Jenkins with GitHub  

## Overview  
This guide will help you create a **Personal Access Token (PAT)** on GitHub and configure it for Jenkins integration using a **classic GitHub PAT** and Jenkins hosted at `localhost:8080`. The guide assumes a `Jenkinsfile` exists in your Git repository to define the pipeline.  

## Stage 1: On GitHub  

### Step-by-Step Instructions  

1. **Login to GitHub**  
   - Log in to your personal GitHub account.  
   - Navigate to the following URL:  
     [https://github.com/settings/tokens](https://github.com/settings/tokens).  

2. **Generate a New Token**  
   - Click the **"Generate new token (classic)"** button.  
   - GitHub will prompt you to enter your password. Enter your password to continue.  

3. **Provide Token Details**  
   - **Name your Token**:  
     Enter a meaningful name for the token. Example: `T7`.  

4. **Set Permissions**  
   - Select the following permissions:  
     - **repo**: Full control of private repositories.  
     - **user:email**: Access to user email addresses.  

5. **Generate the Token**  
   - Click the **"Generate token"** button.  
   - Copy the token displayed on the screen into a secure location (e.g., Notepad).  

> **Important**: You will not be able to view the token again once you leave the page.  

## Stage 2: Configuring Jenkins with GitHub PAT using Blue Ocean  

### Add the GitHub PAT to Jenkins  

1. **Log in to Jenkins**  
   Access your Jenkins instance at [http://localhost:8080](http://localhost:8080).  

2. **Navigate to Blue Ocean**  
   - Click the **Blue Ocean** button from the Jenkins dashboard (or navigate to [http://localhost:8080/blue](http://localhost:8080/blue)).  

3. **Create a New Pipeline**  
   - Select **Create a new pipeline**.  
   - Choose **GitHub** as the source provider.  

4. **Authenticate with GitHub**  
   - If prompted, add a new GitHub credential:  
     - Use the previously generated PAT as the **Token**.  
     - Save the credential with an appropriate ID (e.g., `github-classic-pat`).  

5. **Select Your Repository**  
   - Choose the repository containing the `Jenkinsfile`. Example: `Sample Library API`.  

6. **Scan Repository**  
   - Jenkins will scan the repository and detect the `Jenkinsfile`.  
   - Review the pipeline stages and confirm the configuration.  

7. **Run the Pipeline**  
   - Start the pipeline to build the project.  
