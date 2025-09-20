Role cli_tools
=========

Ansible role to install various cli tools for admin/dev/productivity work.

Requirements
------------

None.

Role Variables
--------------
Available variables are in `defaults/main.yml`:

```yaml
cli_tools_admin_packages: true
```
Installs packages for administration.

```yaml
cli_tools_basic_dev_packages: false
```
Installs packages for development work.

```yaml
cli_tools_excluded_packages: []
```
A list of packages to exclude from installation can be provided.

```yaml
cli_tools_extra_packages: []
```
An extra list of packages to install can be provided.

```yaml
cli_tools_state: present
```
Installation state can be provided to apply to cli_tools_excluded_packages.

Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: localhost
      connection: local
      roles:
         - role: cli_tools
           vars:
              cli_tools_admin_packages: true
              cli_tools_dev_packages: false
              cli_tools_extra_packages:
                - cowsay
              cli_tools_excluded_packages:
                - nano
                - tmux

```

License
-------

BSD
