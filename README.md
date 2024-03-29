# Ansible Role Helm

[![CI](https://github.com/oscaromeu/ansible-role-helm/actions/workflows/ci.yml/badge.svg)](https://github.com/oscaromeu/ansible-role-helm/actions/workflows/ci.yml)

This role manages the installation of [Helm](https://helm.sh)

## Requirements

```
molecule 4.0.0 using python 3.10
ansible:2.12.2
docker:1.1.0 from molecule_docker requiring collections: community.docker>=1.9.1
vagrant:1.0.0 from molecule_vagrant
```


## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yml
uninstall: false
```

If set to true it will only remove the installed cli. 

```yml
helm_platform: linux
helm_arch: arm64
```

By default the platform is `linux` and the `architecture` is `arm64`. These variables are checked and configured at runtime by the role so its not necessary to adjust them.

```yml
helm_version: 'v3.2.1'
```

Using these variables the binaries can be upgraded or downgraded. 


```yml
helm_bin_path: /usr/local/bin/helm
```

The location where the helm binary will be installed.

## Dependencies

None.

## Examples

### Example Playbook

```yaml
    - hosts: all
      roles:
        - role: oscaromeu.helm
```

### Execute example playbook locally

```
ansible-playbook --connection=local --inventory 127.0.0.1, playbook.yml --ask-become-pass
```

### Execute test with molecule

#### Run test sequence commands

Run molecule to create an instance with:

```
$ molecule create -s default
```

Test the role against our instances with:

```
$ molecule converge -s default --
```

Verify that the role pass the test:

```
$ molecule verify
```

Finally, we can destroy the instances with:

```
$ molecule destroy
```

#### Run a full test sequence

The full lifecycle sequence can be invoked with:

```
$ molecule test
```

__Note:__ Getting colorized output from molecule and Ansible

```
export ANSIBLE_FORCE_COLOR=1
```
## License

MIT / BSD

## Author Information

This role was created by Oscar Romeu

