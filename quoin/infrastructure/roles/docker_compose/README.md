# qi-docker-compose

This is a reusable Ansible role that runs Docker Compose.
It builds a set of images and then runs `docker-compose` to start the multi-container application.

## Usage

Include the role in your Ansible `roles_path` either by git subtree (preferred) or ansible-galaxy (not recommended) and then add it to your playbooks.

While this role does not depend on the [qi-docker](https://bitbucket.org/quoin/qi-docker) role it is expected to run after that role.

### Variables

The role can be customized by several variables:

  qi\_docker\_compose\_images
  : An array of images to build before running `docker-compose`.
    Each image represented by an object.
    (Default: [])

    name
    : The name of the image.

    path
    : The path to the image directory.
      (Default: omitted)

    dockerfile
    : The path to the Dockerfile.
      (Default: omitted)

    buildargs
    : The image buildargs.
      (Default: omitted)

  qi\_docker\_virtualenv
  : The location of the docker-py/docker-compose Python virtualenv.
    This role does not provide a default value.
    The value is normally set by the `qi-docker` role to `/opt/docker/virtualenv`.

  qi\_docker\_compose\_files
  : The ordered array of Docker Compose files.
    (Default: `/opt/docker/docker-compose.yml`)

  qi\_docker\_compose\_args
  : The extra arguments passed to `docker-compose`.
    (Default: '')

  qi\_docker\_compose\_folder
  : The folder from which `docker-compose` is run. (Default `/opt/docker`)

### Force Recreate

The most common use for the `qi_docker_compose_args` variable is to force `docker-compose` to recreate the images.

            qi_docker_compose_args: '--force-recreate'

This can be passed at runtime to the `ansible-playbook` command.

            (virtualenv) $ ansible-playbook -i inventory/example.ini -e qi_docker_compose_args=--force-recreate playbook.yml

It can be included in a special playbook.

            ---
            - hosts: docker-compose
              vars:
                qi_docker_compose_args: '--force-recreate'
              roles:
              - qi-docker
              - qi-docker-compose
