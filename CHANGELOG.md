# Docker Image Packaging for OpenSSH Server

## 7.6.1-XalvistackY - TBC

### Major Changes

  - Consolidate molecule tests into `default` (noop)

## 7.6.1-4alvistack3 - 2020-03-04

### Major Changes

  - Revamp with Molecule and `docker commit`
  - Hotfix for systemd

## 7.6.1-3alvistack1 - 2020-01-16

### Major Changes

  - Ubuntu 18.04 based
  - Handle ENTRYPOINT with dumb-init
  - Self initialize with Ansible, by dogfooding with Ansible Playbook
