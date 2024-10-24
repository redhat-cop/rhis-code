git_repo_commit
=========

This repo first installs and configures git on the given host and then clone the given repository, add files, commit, and push changes to remote repository.

Requirements
------------

- Private access token should have provided with the write access to the remote repository.
- Provided user should have rights to push `devel` branch.
- GPG signing key should be created and public key should be placed under GitHub Account.
- Configuration variables should be provided with a variable file.

Role Variables
--------------

```yaml
# default variables
git_repo_commit_repo_path: /tmp
git_repo_commit_branch: devel

# configuration variables
git_repo_commit_git_username: "{{ git_username }}"
git_repo_commit_git_email: "{{ git_email }}"
git_repo_commit_signing_key: "{{ gpg_signingkey_id }}"
git_repo_commit_commit_message: "Git repo commit by bot: {{ git_repo_commit_git_username }}"
git_repo_commit_github_pat: "{{ github_pat }}"

# execution variables:
git_repo_commit_repository:
git_repo_commit_file:
```

Dependencies
------------

- N/A

Example Playbook
----------------

```yaml
- hosts: rootCA
  roles:
    - role: git_repo_commit
      vars:
        git_repo_commit_repository: "{{ github_inventory_repo_path }}"
        git_repo_commit_file: "{{ path_file_encrypted }}"
```

License
-------

GPL-3.0-only

Author Information
------------------

Showroom Project Team
