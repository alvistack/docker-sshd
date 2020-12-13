# Docker Image Packaging for OpenSSH Server

## YYYYMMDD.Y.Z - TBC

### Major Changes

## 20201213.0.1 - 2020-12-13

### Major Changes

  - Change GIT tag as per Vagrant Box naming and versioning limitation

## 8.2.1-4alvistack18 - 2020-12-09

### Major Changes

  - Migrate from Travis CI to GitLab CI
  - Revamp with Packer

## 8.2.1-4alvistack14 - 2020-10-14

### Major Changes

  - Refine Molecule matrix

## 8.2.1-4alvistack10 - 2020-08-26

### Major Changes

  - Upgrade minimal Ansible Lint support to 4.3.2
  - Upgrade Travis CI test as Ubuntu Focal based
  - Upgrade minimal Ansible support to 2.10.0

## 8.2.1-4alvistack8 - 2020-06-10

### Major Changes

  - Revamp `create`, `side_effect`, `verify` and `destroy` logic
  - Replace `tini` with `catatonit`
  - Rename `post_tasks.yml` as `side_effect.yml`
  - Upgrade base image to Ubuntu 20.04

## 7.6.1-4alvistack4 - 2020-03-05

### Major Changes

  - Revamp with Molecule and `docker commit`
  - Consolidate molecule tests into `default` (noop)
  - Hotfix for systemd

## 7.6.1-3alvistack1 - 2020-01-16

### Major Changes

  - Ubuntu 18.04 based
  - Handle ENTRYPOINT with dumb-init
  - Self initialize with Ansible, by dogfooding with Ansible Playbook
