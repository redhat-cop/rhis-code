# Abstract

This document simply refers to the [good practices
document](https://redhat-cop.github.io/automation-good-practices/) from
the field of Ansible practitioners at Red Hat, consultants, developers,
and others. and also [tips and
tricks](https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html)
from Ansible community. Please visit the related pages to get more deep
understanding if needed.

The following rules are a good recommendation to start with. **Optimize
for Readability** should be the main indicator and if done properly, it
can be the documentation of your workflow automation.

A clean separation of code and data (aka inventory) needs to be fostered
from the beginning. In general one basis version control system
repository for all the project code and documentation, including all
roles in a sub-directory and another version control system repository
called for the inventory and variables. The root directory in each
repository contains a `README.adoc` file which explains the repository
and the sub-directories structure and/or points to more detailed
documentation.

The project contains following repositories:

1.  Code repository for roles, collections, playbooks is named
    [`rhis-code`](https://github.com/redhat-cop/rhis-code)

2.  Inventory and variable repository is placed named
    [`rhis-inventory`](https://github.com/redhat-cop/rhis-inventory)

# High level hierarchy for playbooks

The following automation structure model is used in the project.

![Structure of Automation](./images/ansible_structures.svg)

## Landscape

Top level playbooks are separated by role. A landscape is anything we
want to deploy at once which includes many import of other playbooks and
can be visualized like a workflow approach in Ansible Automation
Controller. The named should be include a prefix named `landscape_`.

## Use Cases (Types)

Use cases are high level collections of tasks, grouped around a specific
type of usage - base operating system configuration, a particular server
deployment etc. Use cases are mapped as epics in the Jira. These epics
contain user stories, tasks and bugs for specific features. These kind
of playbooks should start with a prefix named `type_` which can be
easily used on Ansible Automation Controller. Each type is then made of
multiple functions, represented by roles, so that the same function used
by the same type can be re-used, written only once.

## Features (Functions)

Depending on the complexity and distinct requirements, a use case might
contain one or more features. Features are generally mapped to user
stories in a particular epic in Jira. It is preferred to create a simple
playbook named with a prefix named `function_` for a particular role,
mostly to be used as a ad-hoc script.

## Helper playbooks (Toolboxes)

Non use case playbooks and scripts, generally the required for cleanup,
testing etc., are allowed as long as they are explicitly named starting
with `toolbox_` prefix. They are self contained and do not introduce
additional dependencies or blockers for the use case features.

# Roles

1.  All new roles should be placed under the standard folder `roles`.

2.  New roles should be initiated in line, with the skeleton directory,
    which has standard boilerplate code for a Galaxy-compatible Ansible
    role and some enforcement around these standards.

3.  All defaults and all arguments to a role should have a name that
    begins with the role name to help avoid collision with other names.

4.  Design roles focused on the functionality provided, not the software
    implementation. Break down your playbooks into reusable roles. Each
    role should have a clear and specific purpose.

5.  All roles have a `meta/main.yml` file with the fields **values**
    documented in alignment with
    [guidelines\_automation\_header.yml](guidelines_automation_header.yml).
    In normal cases, only the `description` should need specific values,
    and potentially the `min_ansible_version`.

6.  No empty directories, or directories with useless files.

7.  All roles have a `README.md` file with at least an explanation of
    the purpose of the role; variables don’t need to be repeated. The
    documentation is essential for the success of the content. Place the
    `README.md` file in the root directory of the role.

8.  `defaults/main.yml` contains *all* variables able to influence the
    role, together with comments on usage. The variables can be
    commented out if their default is to be undefined but they have to
    be listed.

9.  All variables defined within a role have a prefix corresponding to
    the role name to create a kind of namespace (see also variable names
    in link:Inventory and Variables\[Inventory and Variables\]).

10. Use handlers for tasks that should only run when notified. Handlers
    should have clear names and be defined in the handlers section of a
    role.

11. Follow a consistent naming convention for roles. Use lowercase
    letters and separate words with underscores.

12. Documentation: Include a README.md file in each role to document its
    purpose, variables, and usage. Document playbook dependencies and
    any prerequisites.

13. Internal variables (those that are not expected to be set by users)
    are to be prefixed by two underscores like \`\_\_foo\_variable\`.

14. Prefix all tags within a role with the role name or, alternatively,
    a "unique enough" but descriptive prefix.

15. Do not use dashes in role names. This will cause issues with
    collections.

16. The role should work in check mode, meaning that first of all, they
    should not fail check mode, and they should also not report changes
    when there are no changes to be done.

17. Reporting changes properly is related to the other requirement named
    `idempotency`. Roles should not perform changes when applied a
    second time to the same system with the same parameters, and it
    should not report that changes have been done if they have not been
    done.

18. Add `{{ ansible_managed | comment }}` at the top of the template
    file file to indicate that the file is managed by Ansible roles,
    while making sure that multi-line values are properly commented.

19. It is a common practice to have tasks/main.yml file including other
    tasks files, which we’ll call sub-tasks files. Make sure that the
    tasks' names in these sub-tasks files are prefixed with a shortcut
    reminding of the sub-tasks file’s name.

# Playbooks

1.  YAML documents (including Ansible playbooks) MUST begin a document
    with `---` followed by one empty line.

2.  Files SHOULD use long-form YAML, not short-form YAML.

        person: {name: ansible test, address: {street: somewhere, city: Anycity, state: HE, zip: 12345}}

    use long-format YAML

<!-- -->

    person:
    name: ansible test
      address:
      street: somewhere
      city: Anycity
      state: HE
      zip: 12345

1.  Every task, play or block MUST have a name.

2.  Every task, play or block MUST have 1 or more appropriate tags,
    annotated as an array instead of a single string. Also document tags
    and their purpose(s).

3.  Strings which are *not* builtin parameter triggers like `present`
    are enclosed in quotes to make them stand out to the reader.

4.  Use Ansible modules in tasks instead of commands if available.

5.  Use fully qualified collection names (FQCN) to avoid ambiguity in
    which collection to search for the correct module or plugin for each
    task.

6.  For builtin modules and plugins, use the `ansible.builtin`
    collection name as a prefix, for example `ansible.builtin.copy`.

7.  Tasks using the `command` or `shell` module (or, more generally, any
    module that doesn’t report if it changed anything) have a
    `changed_when` field to indicate if they changed something. If a
    tasks merely collects information append `changed_when: false` to
    the task.

8.  Use only the `true/false` boolean style, Do *not* use `yes/no` or
    `True/False`

9.  No privilege escalation unless absolutely necessary. Using `become`
    at the playbook context is strongly discouraged. All roles should
    include `become` for tasks that need privileged execution. To keep
    the tasks design simple, `block` or `include_tasks` can also be used
    depending on the design.

10. A playbook can contain pre\_tasks, roles, tasks and post\_tasks
    sections. Avoid using both roles and tasks sections, the latter
    possibly containing import\_role or include\_role tasks.

11. It is a good practice to enable debug messages only if a higher
    level of verbosity is specified while launching the playbook.

    -   name: this message will only appear when verbosity is 2 or more
        debug: msg: "Some more debug information if needed" verbosity: 2

12. Do not use special characters other than underscore in variable
    names, even if YAML/JSON allow them.

13. Use a single space separating the template markers from the variable
    name inside all Jinja2 template points. For instance, always write
    it as {{ variable\_name\_here }}

14. Use double quotes for YAML strings with the exception of Jinja2
    strings which will use single quotes.

15. Always mention the state. For many modules, the `state` parameter is
    optional. Different modules have different default settings for
    state, and some modules support several state settings. Explicitly
    setting `state: present` or `state: absent` makes playbooks and
    roles clearer.

16. Use the serial keyword to control how many machines you update at
    once in the batch.

17. Name your playbooks descriptively, reflecting their purpose or the
    infrastructure component they manage.

18. Define variables in a separate vars section or in separate variable
    files. Use meaningful variable names and provide comments for
    complex or non-obvious cases. Please refer to the section
    link:Inventory and Variables\[Inventory and Variables\].

19. Implement proper error handling in your playbooks. Avoid to use the
    `ignore_errors` and `failed_when` attributes judiciously.

# Collections

1.  All required collections should be defined in the `collections`
    folder. The best practice is to list all the required collections in
    the `requirements.yml` file, and let AAP controller install them as
    needed.

# Inventory and Variables

1.  Define your inventory as structured directory instead of single
    file.

2.  Directory Structure include `group_vars` and `host_vars`
    directories.

3.  `group_vars` folder is the main location for variable and parameter
    files for a given group. The parameters defined here are valid for
    all hosts that belong to the relevant group.

4.  `host_vars` folder is the main location for variable and parameter
    files for a given host.

5.  All hosts are defined by their FQDNs.

6.  Use dynamic inventory with cloud approach and build smart
    inventories if needed.

7.  Variables should written in the separate files that is simplifying
    to use by grouping.

8.  Keep vaulted variables safely visible. Encrypt sensitive or secret
    variables with Ansible Vault. However, encrypting the variable names
    as well as the variable values makes it hard to find the source of
    the values. To circumvent this, you can encrypt the variables
    individually using `ansible-vault encrypt_string`.

9.  Do not populate the same variable in more than one hierarchy.

10. Don’t use `extra vars` to define your desired state. Make sure your
    inventory completely describes how your environment is supposed to
    look like. Use extra vars only for troubleshooting, debugging or
    validation purposes.

11. Avoid playbook and play variables, as well as include\_vars. Opt for
    inventory variables instead.

12. Use parent/child group relationships. It is always good to use
    parent/child relationships among groups. Parent groups are also
    known as nested groups or groups of groups.

13. Variables should be prefixed with the related application, Ansible
    Role, etc, to bring context and avoid with the name of the role.

# YAML / Jinja2 Syntax

1.  Indentation should be 2 spaces. Further, arrays (i.e., lines which
    begin with -) should be indented 2 spaces from its parent as well.

2.  use two spaces indentation width in YAML files; Do *not* use tabs.

3.  Lines MUST NOT have trailing whitespace. Remove all trailing
    whitespaces before you commit a file.

4.  A file MUST end with a single empty line feed.

5.  Files MUST use only UTF-8 without BOM as its character encoding.

6.  Split long expressions into multiple lines.

7.  Code that is no longer needed is removed and not commented out.

8.  Avoid comments in playbooks when possible. Instead, ensure that the
    task name value is descriptive enough to tell what a task does.
    Variables are commented in the defaults and vars directories and,
    therefore, do not need explanation in the playbooks themselves. If
    needed, comments MUST have a single space after `\#` for better
    readability.

9.  There SHOULD always be one line of whitespace above the start of a
    comment block.

10. When naming files, use the `.yml` extension and not `.yaml` for YAML
    files, `.j2` as the file extension for Jinja files.

11. Use lowercase a-z for naming the files. Use underscore \_ as a
    separator, do NOT use dashes.

12. Do NOT use whitespace as a separator.

# General Ansible Guidelines

1.  Ensure that all tasks are idempotent.

2.  If there is ever a discrepancy between English-speaking dialects,
    use U.S. English as a baseline for both spelling and word choice.

3.  Use the `| bool` filter when using bare variables (expressions
    consisting of just one variable reference without any operator) in
    when.

4.  Use bracket notation instead of dot notation for value retrieval
    (e.g. `item['key']` vs. `item.key`)

5.  Do not use `meta: end_play` as it aborts the whole play instead of a
    given host.

6.  Avoid the use of `lineinfile` wherever that might be feasible.

7.  Enable Callback plugins. Callback plugins enable adding new
    behaviors to Ansible when responding to events. By default, callback
    plugins control most of the output you see when running the command
    line programs, but can also be used to add additional output,
    integrate with other tools and marshal the events to a storage
    backend.

8.  Use tools like `ansible-lint` to check your code for common issues
    and adherence to best practices. Maintain consistent code
    formatting.

9.  Implement testing for your Ansible code, either manually or through
    automated testing frameworks.
