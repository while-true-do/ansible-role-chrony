[![Build Status](https://travis-ci.org/while-true-do/ansible-role-chrony.svg?branch=master)](https://travis-ci.org/while-true-do/ansible-role-chrony)

# Ansible Role: chrony
| A role that installs chrony and configures it.

## Installation

Galaxy Link: <https://galaxy.ansible.com/while-true-do/chrony>

```
ansible-galaxy install while-true-do.chrony
```

Github Link: <https://github.com/while-true-do/chrony>

```
git clone https://github.com/while-true-do/chrony.git while-true-do.chrony
```

## Requirements

None.

## Dependencies

## Role Variables

```
# Examples from
# defaults/main.yml
chrony_cfg_servers: [ 0.centos.pool.ntp.org, 1.centos.pool.ntp.org, 2.centos.pool.ntp.org, 3.centos.pool.ntp.org ]
chrony_cfg_serveroption: ''
chrony_cfg_stratumweight: ''
chrony_cfg_driftfile: '/var/lib/chrony/drift'
chrony_cfg_rtcsync: 'true'
chrony_cfg_makestep: '10 3'
...

```

## Example Playbook

Simple Example:

```
- hosts: servers 
  roles:
    - { role: while-true-do.chrony }
```

Advanced Example:

```
- hosts: servers 
  roles:
    - { role: while-true-do.chrony, chrony_cfg_servers: [ 0.centos.pool.ntp.org, 1.centos.pool.ntp.org ], chrony_cfg_logdir: '/var/log/chrony' }
```

## License

This work is licensed under a [BSD License](https://opensource.org/licenses/BSD-3-Clause).

## Contribute / Bugs

**bug reports:** <https://github.com/while-true-do/ansible-role-chrony/issues>

**contributers:** <https://github.com/while-true-do/ansible-role-chrony/graphs/contributors>

## Author Information

**blog:** <https://blog.while-true-do.org>

**github:** <https://github.com/daniel-wtd>

**contact:** [mail@while-true-do.org](mailto:mail@while-true-do.org)
