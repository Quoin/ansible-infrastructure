# qi-docker

This is a reusable Ansible role that installs Docker.
It has been tested with Ansible 2.2.1, Docker 17.03, and the following operating systems:

  * CentOS 7.3
  * Debian Jessie
  * Fedora 25
  * Raspbian Jessie
  * Ubuntu 14.04
  * Ubuntu 16.04

Support has been dropped for the following operating systems:

  * CentOS 6.8
  * Ubuntu 12.04

## Usage

Include the role in your Ansible `roles_path` either by git subtree (preferred) or ansible-galaxy (not recommended) and then add it to your playbooks.

The role installs a Python virtualenv in order to prevent conflicts with system Python packages.
It switches the `ansible_python_interpreter` to use the virtualenv and this affects all roles that execute after it.

### Variables

The role can be customized by several variables:

  qi\_docker\_package
  : The name of the Docker distribution package. (Default: `docker-ce`)

  qi\_docker\_virtualenv
  : The location of the docker-py/docker-compose Python virtualenv. (Default: `/opt/docker/virtualenv`)

  qi\_docker\_virtualenv\_site\_packages
  : Whether or not to include site packages in the Python virtualenv. (Default: `yes`)

  qi\_docker\_pip\_docker\_package
  : The name of the docker pip package. (Default: `docker==2.4.2`)

  qi\_docker\_pip\_docker\_compose\_package
  : The name of the docker-compose pip package. (Default: `docker-compose==1.14.0`)
