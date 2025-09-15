Role NVIM
=========

Ansible role to set up `nvim` editor environment.

Requirements
------------

None.

Role Variables
--------------
Available variables are in `defaults/main.yml`:

```yaml
nvim_bin_setup: false
```
Set to true if you want to install nvim through release binary.

```yaml
nvim_bin_version: "v0.11.4"

# List input example
nvim_bin_version:
  - "nightly"
  - "v0.11.4"
```
The version of release binary to download from official github repo. Here, a list can be specified. Keep in mind that the last entry will be the one available
in system. As shown, although nightly version availabe at path specified in `nvim_bin_dir_path`, system will detect `v0.11.4` version.
```yaml
nvim_bin_dir_path: "/opt/nvim"
```
Directory path in which store the release binary directory.

```yaml
nvim_bin_path: "/usr/local/bin/nvim"
```
Path where nvim binary will be symlink to be available system/user wide.

```yaml
nvim_manage_config: false
```
Set to true if you want to manage nvim config.

```yaml
nvim_dotfiles_github_repo: "https://github.com/rflocfloc/nvim-bootstrap.git"
```
If `nvim_manage_config: true` and github repo provided it will be cloned at `~/.config/nvim`.

```yaml
nvim_dotfiles_github_ssh_key: ""
```
Github ssh key to use in case of private repo.

```yaml
nvim_config_opts:
  - vim.opt.number = true
  - vim.opt.relativenumber = true
```
If `nvim_dotfiles_github_repo: ""` *manual* nvim opts are used to generate an `init.lua` from template.

```yaml
nvim_config_keymaps:
  - vim.keymap.set('n', '<Esc>', '<cmd>nohlsearch<CR>', {desc = "<Esc> to clear search highlights"})
  - vim.keymap.set('t', '<Esc>', '<C-\\><C-N>', {desc = "<Esc> to exit terminal mode"})
```
Same as *opts* field but for keymaps.


Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: localhost
      connection: local
      roles:
         - role: nvim
           vars:
              nvim_bin_setup: true
              nvim_bin_version: "v0.11.4"
              nvim_bin_dir_path: "/opt/nvim"
              nvim_bin_path: "/usr/local/bin/nvim"
```

License
-------

BSD
