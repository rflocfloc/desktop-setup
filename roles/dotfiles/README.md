Role - Dotfiles
=========

Simple ansible role to pull dotfile repo and stow it.

Requirements
------------

None.

Role Variables
--------------
Available at `defaults/main.yml`:
```yaml
dotfiles_github_repo: ""
```
User required var, it is used to define from which github repo to clone dotfiles.
```yaml
dotfiles_github_ssh_key: ""
```
By default **not** defined, it is used to specify ssh key to clone specified repo. If empty git tries to clone it without key.
```yaml
dotfiles_repo_path: "~/.dotfiles"
```
Where to put your dotfiles repo, defaults to `$HOME/.dotfiles`.
```yaml
dotfiles_stow_manage: true
```
Whether to manage your repo with [stow](https://www.gnu.org/software/stow/manual/stow.html). If true, `stow` is installed and the role proceeds to stow files as specified. In particular:
```yaml
dotfiles_stow_repo: false
```
Set to `true` if wanted stow behaviour is `stow .`. This way the entire directory is stow as it is.
```yaml
dotfiles_stow_dirs: []
```
Works only when `dotfiles_stow_repo: false`, defines `stow` behaviour by *apps* in the form of `stow -R <your_dir>`. Defaults to empty list, when like this
ansible retrieves all directories present at level 1 of your dotfiles path and stows them one at the time. List can be modified specified by the user.

Dependencies
------------
None.

Example Playbook
----------------

```yaml
    - hosts: local
      localhost: true

      roles:
        - role: dotfiles
          vars:
            - dotfiles_github_repo: "git@github.com-personal:rflocfloc/dotfiles.git"
            - dotfiles_github_ssh_key: "~/.ssh/id_rsa_github"
            - dotfiles_stow_manage: true
```

License
-------

BSD

Author Information
------------------

