# Golang role for Ansible

Installs Golang from source, sets up the necessary development environment, and grabs the specified packages.

## Requirements

Tested on Ubuntu 12.04 Server.

## Role Variables

The default variables are as follows:

    go_user:       '{{ ansible_ssh_user }}'
    go_user_home:  '/home/{{ go_user }}'
    go_version:    '1.3'
    go_clone_dir:  '{{ go_user }}/golang_src'
    go_bin_dir:    '{{ go_clone_dir }}/bin'
    go_path:       '{{ go_user_home }}/go_path'
    app_name:      ''
    use_go_env:    false
    go_env:        'development'
    go_env_config: 'config/development.yml'
    go_global_packages:
      - 'github.com/codegangsta/gin'    # Live reloader
      - 'github.com/onsi/ginkgo/ginkgo' # Testing framework
      - 'github.com/onsi/gomega'        # Matcher for ginkgo
      - 'github.com/golang/lint/golint' # Go linter
      - 'github.com/GeertJohan/fgt'     # Go linter piped through this to return proper exit codes

## Example Playbook

    - hosts: 'servers'
      roles:
        - role: 'ssilab.golang'
          go_user: 'vagrant'
          go_version: '1.3'
          app_name: 'github.com/ssilab/awesome-go-app'
          use_go_env: true
          go_env: 'development'
          go_env_config: 'config/development.yml'
          go_global_packages:
            - 'github.com/codegangsta/gin'    # Live reloader
            - 'github.com/onsi/ginkgo/ginkgo' # Testing framework
            - 'github.com/onsi/gomega'        # Testing framework
            - 'github.com/golang/lint/golint' # Go linter
            - 'github.com/Ge

# License

This playbook is provided 'as-is' under the conditions of the BSD license. No fitness for purpose is guaranteed or implied.