# qi-debian-stretch

This is a reusable Ansible role that allows for pinning of Debian Stretch packages into Debian Jessie.
It sets the priority to a low value and no packages will be pulled in by default.
It supports both Debian and Raspbian.

## Usage

Include the role in your Ansible `roles_path` either by git subtree (preferred) or ansible-galaxy (not recommended) and then add it to your playbooks.
