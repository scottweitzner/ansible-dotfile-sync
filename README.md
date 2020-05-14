scottweitzner.dotfile-sync
=========

Manage your dotfiles without thinking about symlinks  
This handles the linking process, you handle the pushes to your repo

---
Role Variables
--------------

``` yaml
working_directory: "{{ home_directory }}"
```
the working directory to pull your git repo into and link dotfiles from

<br/>


```yaml
dotfiles_git_repo: git@github.com:scottweitzner/ansible-dotfile-sync.git
```
the git repo where your dotfiles are stored

<br/>

``` yaml
files_to_sync:
- name: alacritty.yml
  file_name: alacritty.yml
  dest: .config/alacritty
```
list of files to sync. must include `name` and `file_name` but `dest` is optional

Note: 
- base directory for file_name is working_directory/dotfiles (found here)
- base dirctory for dest is home_directory (found in vars/main.yml)


---


Example Playbook
----------------


``` yaml
---
- hosts: localhost
  roles:
    - role: ansible-dotfile-sync
      vars:
        working_directory: /Users/me 
        dotfiles_git_repo: git@github.com:me/dotfiles.git
        files_to_sync:
        - name: zsh
          file_name: .zshrc
        - name: alacritty.yml
          file_name: alacritty.yml
          dest: .config/alacritty


```
---

License
-------

BSD
