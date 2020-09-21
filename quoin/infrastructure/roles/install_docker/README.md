# qi-install-docker

This is a reusable Ansible role that installs Docker.
It has been tested with Ansible 2.6, Docker 18.06, and the following operating systems:

  * Debian Stretch
  * Fedora 28
  * Raspbian Stretch

## Usage

Include the role in your Ansible `roles_path` either by ansible-galaxy (preferred) or git subtree (not recommended) and then add it to your playbooks.

The variable `qi_install_docker_docker_package` is used to specify a docker version.  Here are some examples of the version format for Debian, Fedora, and Ubuntu:

  * Debian: `docker-ce=17.06.0~ce-0~debian`
  * Fedora: `docker-ce-17.06.0.ce-1.fc25`
  * Ubuntu: `docker-ce=17.06.0~ce-0~ubuntu`
