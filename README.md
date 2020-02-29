# Docker Image Packaging for OpenSSH Server

[![Travis](https://img.shields.io/travis/alvistack/docker-sshd.svg)](https://travis-ci.org/alvistack/docker-sshd)
[![GitHub release](https://img.shields.io/github/release/alvistack/docker-sshd.svg)](https://github.com/alvistack/docker-sshd/releases)
[![GitHub license](https://img.shields.io/github/license/alvistack/docker-sshd.svg)](https://github.com/alvistack/docker-sshd/blob/master/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/alvistack/sshd.svg)](https://hub.docker.com/r/alvistack/sshd/)

OpenSSH is the premier connectivity tool for remote login with the SSH protocol.

Learn more about OpenSSH: <https://www.openssh.com/>

## Supported Tags and Respective `Dockerfile` Links

  - [`7.6`, `latest` (molecule/7.6/Dockerfile.j2)](https://github.com/alvistack/docker-sshd/blob/master/molecule/7.6/Dockerfile.j2)

## Overview

This Docker container makes it easy to get an instance of SSHD up and running with Ubuntu.

Based on [Official Ubuntu Docker Image](https://hub.docker.com/_/ubuntu/) with some minor hack:

  - Minimized `Dockerfile` for meta data definition
  - Provision by Ansible and Molecule Docker driver in single layer
  - Handle `ENTRYPOINT` with [tini](https://github.com/krallin/tini)
  - Handle `CMD` with SSHD

### Quick Start

Start SSHD:

    # Pull latest image
    docker pull alvistack/sshd
    
    # Run as detach
    docker run \
        -itd \
        --name sshd \
        --publish 2222:22 \
        alvistack/sshd

**Success**. SSHD is now available on port `2222`.

Because this container **DIDN'T** handle the generation of root password, so you should set it up manually with `pwgen` by:

    # Generate password with pwgen
    PASSWORD=$(docker exec -i sshd pwgen -cnyB1); echo $PASSWORD
    
    # Inject the generated password
    echo "root:$PASSWORD" | docker exec -i sshd chpasswd

Alternatively, you could inject your own SSH public key into container's authorized\_keys by:

    # Inject your own SSH public key
    (docker exec -i sshd sh -c "cat >> /root/.ssh/authorized_keys") < ~/.ssh/id_rsa.pub

Now you could SSH to it as normal:

    ssh root@localhost -p 2222

## Versioning

The `latest` tag matches the most recent version of this repository. Thus using `alvistack/sshd:latest` or `alvistack/sshd` will ensure you are running the most up to date version of this image.

## License

  - Code released under [Apache License 2.0](LICENSE)
  - Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Author Information

  - Wong Hoi Sing Edison
      - <https://twitter.com/hswong3i>
      - <https://github.com/hswong3i>
