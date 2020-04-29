# Ansible Role: Dotfiles

Installs a set of dotfiles, and preps environment for [VIM Plugin Manager ( Vundle ) ](https://github.com/vundlevim/vundle.vim) and Git bash prompt.  The dotfiles are taken from [dotfiles](https://github.com/codebleu/dotfiles), but you can use any set of dotfiles you'd like, as long as they follow a conventional format.

## Requirements

Requires `git` on the managed machine (installed via this role if not already installed)

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):


    dotfiles_repo_update: true

Variable to use git to pull/clone repos (meant to disable if needed after initial run)

    bash_files_dir: "~/development/bash"
    bash_files:
      - git-prompt.sh

This ensurse files are in place for custom git prompt (.bashrc would need to be edited to change bash_files_dir variable)

    dotfiles_repo: "https://github.com/codebleu/dotfiles.git"
    dotfiles_repo_version: master

The git repository and branch/tag/commit hash to use for retrieving dotfiles. Dotfiles should generally be laid out within the root directory of the repository.
    
    vundle_repo: "https://github.com/VundleVim/Vundle.vim.git"
    vundle_repo_version: master

The git repository and branch/tag/commit hash to use for retrieving vim plugin manager.
    
    vundle_repo_local_destination: "~/.vim/bundle/Vundle.vim"

The destination directory used form Vundle.vim plugin manager

    dotfiles_repo_accept_hostkey: false

Add the hostkey for the repo url if not already added. If ssh_opts contains "-o StrictHostKeyChecking=no", this parameter is ignored.

    dotfiles_repo_local_destination: "~/dotfiles"

The local path where the `dotfiles_repo` will be cloned.

    dotfiles_home: "~"

The home directory where dotfiles will be linked. Generally, the default should work, but in some circumstances, or when running the role as sudo on behalf of another user, you may want to specify the full path.

    dotfiles_files:
      - .tigrc
      - .gitconfig
      - .tmux.conf
      - .zshrc
      - .vimrc
      - .bashrc

Which files from the dotfiles repository should be linked to the `dotfiles_home`.

## Dependencies

None

## Example Playbook

    - hosts: localhost
      roles:
        - { role: ansible-role-dotfiles }

## License

MIT / BSD

## Author Information

This role was created in 2020 by [Jason Hollis](https://github.com/codebleu) but was modified from [Jeff Geerling's ansible-role-dotfiles](https://github.com/geerlingguy/ansible-role-dotfiles.git)
