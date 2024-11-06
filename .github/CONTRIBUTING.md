# Contributor's Guidelines

Refer to the [Ansible Community Guide](https://docs.ansible.com/ansible/devel/community/index.html) for basic guideline.

## General Guidance
When making a contribution to the repositories of the Red Hat Communities of Practice, try to utilize the following set of guidelines outlined in this section. Committers should adhere to these practices as they attempt to address many (but not all) of the primary concerns associated with open source repositories and project management:

**Do:**

- Squash commits whenever possible
- Engage with the community and with contributors
- Write tests when applicable
- Discuss with other committers whenever you are unsure of something
- Create documentation, especially for new features and functionality
- Review existing content in order to avoid overwriting existing content
- Keep it simple
- Sign your commits

**Don’t:**

- Commit directly to the master branch
- Merge pull requests you have authored
- Break existing functionality
- Ignore requests for assistance
- Go against established repository and CoP norms

Please checkout [General Guidelines](../docs/general_guidelines.md) for more information.

Please follow [Ansible Good Practices](../docs/ansible_practices.md) as the project consists of full automation with Ansible.

And finally, you can benefit from the [Git Cheat Sheet](../docs/git_cheat_sheet.md) for the basics of using Git within the project.

## How to Contribute

Contributions from the community play an important role in the assets associated with the Red Hat Communities of Practice (CoP). We welcome contributions from the community. Here are a few ways you can help us improve.

### Open an Issue

If you see something you'd like changed, but aren't sure how to change it, submit an issue describing what you'd like to see.

### Submit a Pull Request

If you feel like getting your hands dirty, feel free to make the change yourself. Here's how:

1. Fork the repo on Github, and then clone it locally.
2. Create a branch named appropriately for the change you are going to make. Follow the [branch standards](../docs/branch_standards.md) to create a branch.
3. Make your code change.
4. If you are creating a new role, please add a tests for it for use in a github action if possible.
5. Push your code change up to your forked repo.
6. Open a Pull Request to merge your changes to this repo. The comment box will be filled in automatically via a template.
7. All Pull Requests will be subject to Ansible and Yaml Linting checks. Please make sure that your code complies and fix any warnings that arise. These are Checks that appear at the bottom of your Pull Request.
8. PR must be reviewed and approved by two persons who own commit permissions.


See [Using Pull Requests](https://help.github.com/articles/using-pull-requests/) got more information on how to use GitHub PRs.

For an in depth guide on how to contribute see [this article](https://opensource.com/article/19/7/create-pull-request-github)

Note that we follow the [Automation Good Practices](https://redhat-cop.github.io/automation-good-practices) and so are you expected to do.

Use Github [discussions](https://github.com/redhat-cop/rhis-code/discussions) forum or for a live chat experience try
Matrix room [#aap_config_as_code:ansible.com](https://matrix.to/#/#aap_config_as_code:ansible.com).

## Code of Conduct

As with all Ansible projects, we have a [Code of Conduct](./CODE_OF_CONDUCT.md).

- [ansible communication](https://docs.ansible.com/ansible/latest/community/communication.html)
- [code of conduct](https://docs.ansible.com/ansible/latest/community/code_of_conduct.html)
- [creating your fork on github](https://guides.github.com/activities/forking/)
- [releases and maintenances](https://docs.ansible.com/ansible-core/devel/reference_appendices/release_and_maintenance.)
- [supported ansible versions](https://docs.ansible.com/ansible-core/devel/reference_appendices/release_and_maintenance.html#ansible-core-release-cycle)
