# &#128011; Docker role for Ansible

[![Build Status](https://img.shields.io/travis/paulborza/docker-ansible-role/master.svg)](https://travis-ci.org/paulborza/docker-ansible-role)
[![Ansible Role](https://img.shields.io/ansible/role/16538.svg)](https://galaxy.ansible.com/paulborza/docker/)

## Supported OS

- Ubuntu
  - Ubuntu 14.04 LTS (Trusty Tahr)
  - Ubuntu 16.04 LTS (Xenial Xerus)
  - Ubuntu 16.10 (Yakkety Yak)
- Debian
  - Debian 8.0 LTS (Jessie)

## Usage

First, download the Docker role locally.

```bash
ansible-galaxy install --force paulborza.docker
```

Second, create a file named `example-playbook.yml`. Use the following YAML file as example, but don't forget to replace the Docker Hub credentials and container information. The example assumes that you want to run a private container that's built by [hub.docker.com](https://hub.docker.com/)

```
- hosts: all
  roles:
    - paulborza.docker

  tasks:
    - name: login to docker hub
      become: true
      docker_login:
        username: YOUR_DOCKER_HUB_USERNAME
        password: YOUR_DOCKER_HUB_PASSWORD
        email: YOUR_EMAIL

    - name: start container
      become: true
      docker_container:
        name: DESIRED_CONTAINER_NAME
        image: YOUR_DOCKER_HUB_USERNAME/YOUR_DOCKER_HUB_REPOSITORY
        pull: true
```

Third, create another file named `hosts` by running `echo localhost > hosts`. Feel free to update the hosts file to match your infrastructure configuration.

Finally, execute the playbook against the servers listed in the `hosts` file.

```bash
ansible-playbook ./example-playbook.yml -i ./hosts
```

## Contributing

Got a new OS you'd like to see supported by this role?
Please go ahead and [create a work item](https://github.com/paulborza/docker-ansible-role/issues/new) for me; or better yet, send a pull request and I'll be sure to take a look at it within 24 hours. Thanks!
