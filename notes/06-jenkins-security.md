## Security in Jenkins

### Enabling Security
Starting with Jenkins 2.214 and Jenkins LTS 2.222.1, the "Enable Security" checkbox has been removed. Jenkins uses its own user database as the default security realm. It's crucial to enable security for any non-local Jenkins environment.

### Access Control
Access control is the primary mechanism for securing a Jenkins environment. It involves two main components:
1. **Security Realm**: Determines how and where to pull user information from. This is also known as authentication.
2. **Authorization Strategy**: Determines which users and/or groups can access which aspects of Jenkins and to what extent.

### Protecting Jenkins Against External Threats
To protect Jenkins from external threats, consider the following best practices:
- **Use Strong Authentication Mechanisms**: Implement mechanisms like two-factor authentication (2FA).
- **Limit Access and Privileges**: Restrict access and privileges based on user roles.
- **Regular Updates**: Keep Jenkins and its plugins up to date with security patches.

### Securing Credentials
To secure credentials in Jenkins, follow these best practices:
- **Segment Jenkins Jobs**: Organize jobs according to credential usage.
- **Least Exposure Principle**: Limit credentials exposure by making them visible only to the minimum number of users and processes necessary.

### Additional Security Features
- **TCP Port Access Control**: Manage inbound agents using TCP ports or WebSocket transport.
- **CSRF Protection**: Protect against Cross-Site Request Forgery (CSRF) attacks.
- **Agent/Master Access Control**: Control access between Jenkins agents and the master server.

## Jenkins Security Realms

### Overview
A security realm in Jenkins determines the method of authentication and where Jenkins gets its user information. In other words, it specifies how users can log in and how Jenkins manages user identities. Here are some common security realms used in Jenkins:

### 1. Jenkins' Own User Database
Jenkins comes with a built-in user database which is used by default for authentication.

#### Example:
To configure Jenkins' own user database:
- Go to **Manage Jenkins** > **Configure Global Security**.
- Under **Security Realm**, select **Jenkins’ own user database**.
- Ensure the checkbox **Allow users to sign up** is checked if you want to allow new users to register.

### 2. LDAP (Lightweight Directory Access Protocol)
Integrating Jenkins with LDAP allows Jenkins to authenticate users against an LDAP server, which is often used in enterprise environments.

#### Example:
To configure LDAP:
- Go to **Manage Jenkins** > **Configure Global Security**.
- Under **Security Realm**, select **LDAP**.
- Fill in the **Server** and **Root DN** fields with your LDAP server details.
- Optionally, configure the **User Search Base** and **User Search Filter** to refine the search query.

### 3. Active Directory
If your organization uses Active Directory (AD), Jenkins can use it for authentication.

> You must install `Active Directory` plugin for this option to be available.

#### Example:
To configure Active Directory:
- Go to **Manage Jenkins** > **Configure Global Security**.
- Under **Security Realm**, select **Active Directory**.
- Enter the **Domain** name and other necessary details like **Domain Controllers**.
- Optionally, provide the **Bind DN** and **Bind Password** if required.

### 4. Github Authentication
Jenkins can authenticate users against GitHub, allowing users to log in with their GitHub accounts.

#### Example:
To configure GitHub authentication:
- Install the **GitHub Authentication Plugin** from the Jenkins update center.
- Go to **Manage Jenkins** > **Configure Global Security**.
- Under **Security Realm**, select **GitHub Authentication**.
- Configure your **Client ID** and **Client Secret** from GitHub.
- Optionally, configure the **OAuth scopes** and **Organization** if needed.

### Conclusion
Choosing the right security realm depends on your organization's requirements and existing infrastructure. By configuring appropriate security realms, you can ensure that your Jenkins instance is secure and accessible to authorized users only.

## Jenkins Authorization Options

Authorization in Jenkins determines what actions users can perform once they have been authenticated. Jenkins provides several strategies for defining these permissions. Here are the common authorization options:

### 1. **Anyone can do anything**
This is the most permissive mode where any user, including anonymous users, has full control over the Jenkins instance.

#### Example:
- **Use Case**: Suitable for testing purposes or small, internal projects where security is not a primary concern.
- **Configuration**: No special configuration needed. Simply select this option under **Manage Jenkins** > **Configure Global Security**.

### 2. **Legacy mode**
This mode offers basic, outdated security settings for backward compatibility. It is not recommended for new installations.

#### Example:
- **Use Case**: Rarely used, mainly for legacy systems.
- **Configuration**: Select **Legacy Mode** under **Manage Jenkins** > **Configure Global Security**.

### 3. **Logged-in users can do anything**
In this mode, all authenticated users have full control over the Jenkins instance. Anonymous users have no permissions.

#### Example:
- **Use Case**: Suitable for small teams or internal projects where all users are trusted.
- **Configuration**: Select **Logged-in users can do anything** under **Manage Jenkins** > **Configure Global Security**.

### 4. **Matrix-based security**
This is a flexible and fine-grained authorization strategy that allows assigning specific permissions to individual users or groups.

#### Example:
- **Use Case**: Ideal for larger teams where different roles need different permissions.
- **Configuration**:
  - Go to **Manage Jenkins** > **Configure Global Security**.
  - Select **Matrix-based security**.
  - Add users or groups and assign specific permissions (e.g., read, build, admin).

### 5. **Project-based Matrix Authorization**
Similar to matrix-based security, but permissions can be defined per project, allowing more granular control.

#### Example:
- **Use Case**: Useful for multi-project environments where different projects have different security requirements.
- **Configuration**:
  - Go to **Manage Jenkins** > **Configure Global Security**.
  - Select **Project-based Matrix Authorization**.
  - Configure permissions for each project individually under each project's configuration page.

### 6. **Role-Based Strategy**
This strategy uses the Role Strategy Plugin to define roles with specific permissions and assign users to these roles.

#### Example:
- **Use Case**: Ideal for organizations with a structured role hierarchy.
- **Configuration**:
  - Install the **Role Strategy Plugin** from the Jenkins update center.
  - Go to **Manage Jenkins** > **Manage and Assign Roles** > **Manage Roles**.
  - Define global roles and project roles with specific permissions.
  - Assign users to these roles under **Manage Jenkins** > **Manage and Assign Roles** > **Assign Roles**.

### Conclusion
Choosing the right authorization strategy depends on your organization's size, security requirements, and user roles. By configuring the appropriate authorization options, you can ensure that your Jenkins instance is secure and that users have the necessary permissions to perform their tasks efficiently.

