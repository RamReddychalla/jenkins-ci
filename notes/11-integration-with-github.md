# How to Create a GitHub PAT and Integrate Jenkins with GitHub

## Overview
This guide will help you create a **Personal Access Token (PAT)** on GitHub and configure it for Jenkins integration using **Jenkins Blue Ocean**.

## Stage 1: On GitHub

### Step-by-Step Instructions

1. **Login to GitHub**  
   - Log in to your personal GitHub account.  
   - Navigate to the following URL:  
     [https://github.com/settings/tokens?type=beta](https://github.com/settings/tokens?type=beta)

2. **Generate a New Token**  
   - Click the **"Generate New Token"** button.  
   - GitHub will prompt you to enter your password. Enter your password to continue.

3. **Provide Token Details**  
   - **Name your Token**:  
     Enter a meaningful name for the token. Example: `T5`.  
   - **Set Repository Access**:  
     Under **"Repository Access"**, select:  
     `Only Selected Repositories`.  

4. **Select Repositories**  
   - From the list of repositories, select the repository you want to integrate with Jenkins. Example: `Sample Library API`.

5. **Set Permissions**  
   - Under **Permissions**, expand **Repository Permissions** and set:  
     - **Contents**: `Read & Write`.

6. **Generate the Token**  
   - Click the **"Generate Token"** button.  
   - Copy the token displayed on the screen into a secure location (e.g., Notepad).

> **Note**: You will not be able to view the token again once you leave the page.


## Stage 2: Configuring Jenkins with GitHub PAT using Blue Ocean

### Add the GitHub PAT to Jenkins

1. **Log in to Jenkins**  
   Access your Jenkins instance at `http://localhost:8080`.

2. **Navigate to Blue Ocean**  
   - Click the **Blue Ocean** button from the Jenkins dashboard (or navigate to `http://localhost:8080/blue`).

3. **Create a New Pipeline**  
   - Select **Create a new pipeline**.  
   - Choose **Git** as the source provider.

4. **Enter Your Repository URL**  
   - Enter the repository URL (containing the `Jenkinsfile`). Example: `https://github.com/mahendra-shinde/sample-library-api`.

5. **Authenticate with Git Repository**  
   - If prompted, add a new GitHub credential:
     - Use your GitHub username
     - Use the previously generated PAT as the **Password**.  
     
6. **Scan Repository**  
   - Jenkins will scan the repository and detect the `Jenkinsfile`.  
   - Review the pipeline stages and confirm the configuration.

7. **Run the Pipeline**  
   - Start the pipeline to build the project.
