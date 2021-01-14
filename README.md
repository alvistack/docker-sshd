# Docker Image Packaging for OpenSSH Server

[![GitLab pipeline status](https://img.shields.io/gitlab/pipeline/alvistack/docker-sshd/master)](https://gitlab.com/alvistack/docker-sshd/-/pipelines)
[![GitHub release](https://img.shields.io/github/release/alvistack/docker-sshd.svg)](https://github.com/alvistack/docker-sshd/releases)
[![GitHub license](https://img.shields.io/github/license/alvistack/docker-sshd.svg)](https://github.com/alvistack/docker-sshd/blob/master/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/alvistack/sshd-8.2.svg)](https://hub.docker.com/r/alvistack/sshd-8.2)

OpenSSH is the premier connectivity tool for remote login with the SSH protocol.

Learn more about OpenSSH: <https://www.openssh.com/>

## Supported Tags and Respective Packer Template Links

  - [`alvistack/sshd-8.2`](https://hub.docker.com/r/alvistack/sshd-8.2)
      - [`packer/docker-8.2/packer.json`](https://github.com/alvistack/docker-sshd/blob/master/packer/docker-8.2/packer.json)

## Overview

This Docker container makes it easy to get an instance of SSHD up and running with Ubuntu.

Based on [Official Ubuntu Docker Image](https://hub.docker.com/_/ubuntu/) with some minor hack:

  - Packaging by Packer Docker builder and Ansible provisioner in single layer
  - Handle `ENTRYPOINT` with [catatonit](https://github.com/openSUSE/catatonit)
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

### `YYYYMMDD.Y.Z`

Release tags could be find from [GitHub Release](https://github.com/alvistack/docker-sshd/releases) of this repository. Thus using these tags will ensure you are running the most up to date stable version of this image.

### `YYYYMMDD.0.0`

Version tags ended with `.0.0` are rolling release rebuild by [GitLab pipeline](https://gitlab.com/alvistack/docker-sshd/-/pipelines) in weekly basis. Thus using these tags will ensure you are running the latest packages provided by the base image project.

## License

  - Code released under [Apache License 2.0](LICENSE)
  - Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Author Information

  - Wong Hoi Sing Edison
      - <https://twitter.com/hswong3i>
      - <https://github.com/hswong3i>
