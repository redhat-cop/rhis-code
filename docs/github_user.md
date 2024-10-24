# GitHub User

The automation code and the Ansible Automation Platform require a connection to GitHub to push changes or sync the project from the automation controller. While using a GitHub application is considered best practice, it involves many complex prerequisites. Therefore, we have decided to create a GitHub account to be used as a service account by our systems. After creating the account, several steps must be taken to make it fully functional.

## Create GitHub User

First, visit GitHub's website to sign up for a new account, choosing a username that clearly indicates its purpose as a service account. Add this user the project's organization.

## Create SSH Key

Generate an SSH key pair on the system that will connect to GitHub; this is crucial for AAP GitHub communication. Add the public key to the service account's SSH keys on GitHub for secure access.

## Create GPG Keys

Creating GPG keys is essential for signing commits and tags in GitHub, as it verifies the authenticity of the contributions and ensures that they have not been tampered with. Add the public key to the service account's GPG keys on GitHub for verification.

## Create Personal Access Token

A personal access token (PAT) is an alternative to using passwords for authentication to GitHub when using the GitHub API or the command line. Navigate to GitHub, log in to your account, generate a new token and follow the next step for the appropriate permissions.

## Assign Appropriate Roles

Assign the appropriate permissions to the service account for the necessary repositories, ensuring it has the correct level of access to push changes and sync projects.
- Read access to code repository
- Read/Write access to inventory repository any branch
Finally, verify that the system can connect to GitHub using the new service account and test pushing changes and syncing the project to ensure everything is working correctly. 





