[![Build Status](https://travis-ci.org/while-true-do/ansible-role-chrony.svg?branch=master)](https://travis-ci.org/while-true-do/ansible-role-chrony)

# Ansible Role: chrony
| A role that installs chrony and configures it.

## Motivation

chrony is a daemon which implements the Network Time Protocol (NTP).

## Installation

Install from [Ansible Galaxy](https://galaxy.ansible.com/while_true_do/chrony)

```
ansible-galaxy install while_true_do.chrony
```

Install from [Github](https://github.com/while-true-do/ansible-role-chrony)

```
git clone https://github.com/while-true-do/ansible-role-chrony.git while_true_do.chrony
```

## Requirements

Used Modules:

-   [package_module](http://docs.ansible.com/ansible/latest/modules/package_module.html)
-   [service_module](http://docs.ansible.com/ansible/latest/modules/service_module.html)
-   [template_module](http://docs.ansible.com/ansible/latest/modules/template_module.html)

## Dependencies

None.

## Role Variables

```yaml
---
# defaults/main.yml

# for a complete set of options please have a look at
# man chrony.conf
# examples:
# "minpoll 6"  -> minimum polling interval
# "maxpoll 10" -> the maximum polling interval
# "iburst"     -> the interval between the first four polls
# options can be combined:
# "minpoll 6 maxpoll 10 iburst"
wtd_chrony_cfg_servers:
 - name: 0.centos.pool.ntp.org
   # options: "iburst"
 - name: 1.centos.pool.ntp.org
 - name: 2.centos.pool.ntp.org
 - name: 3.centos.pool.ntp.org

wtd_chrony_cfg_stratumweight: ""
wtd_chrony_cfg_driftfile: "/var/lib/chrony/drift"
wtd_chrony_cfg_rtcsync: true
wtd_chrony_cfg_makestep: "10 3"

wtd_chrony_cfg_allows: ""

wtd_chrony_cfg_local: false
wtd_chrony_cfg_local_stratum: "10"
wtd_chrony_cfg_local_distance: ""
wtd_chrony_cfg_local_orphan: ""

wtd_chrony_cfg_keyfile: "/etc/chrony.keys"

wtd_chrony_cfg_bindcmdaddresses: [ "127.0.0.1", "::1" ]

wtd_chrony_cfg_noclientlog: true
wtd_chrony_cfg_logchange: "0.5"
wtd_chrony_cfg_logdir: "/var/log/chrony"
# wtd_chrony_cfg_log: "measurements statistics tracking"
wtd_chrony_cfg_log: ""
```

## Example Playbook

Simple Example:

```yaml
- hosts: servers
  roles:
    - { role: while_true_do.chrony }
```

Advanced Example:

```yaml
- hosts: servers
  roles:
    - { role: while_true_do.chrony, wtd_chrony_cfg_servers: [{ name: 0.centos.pool.ntp.org, options: "iburst" }, { name: 1.centos.pool.ntp.org }], wtd_chrony_cfg_logdir: '/var/log/chrony' }
```

## Testing

All tests are located in [test directory](./tests/).

Basic testing:

```
bash ./tests/test-ansible.sh
bash ./tests/test-spelling.sh
bash ./tests/test-whitespace.sh
```

## Contribute / Bugs

Thank you so much for considering to contribute. Every contribution helps us.
We are really happy, when somebody is joining the hard work. Please have a look
at the links first.

-   [Code of Conduct](./docs/CODE_OF_CONDUCT.md)
-   [Contribution Guidelines](./docs/CONTRIBUTING.md)
-   [Create an issue or Request](https://github.com/while-true-do/ansible-role-chrony/issues)
-   [See who was contributing already](https://github.com/while-true-do/ansible-role-chrony/graphs/contributors)

## License

This work is licensed under a [BSD License](https://opensource.org/licenses/BSD-3-Clause).

## Author Information

Site: [while-true-do.org](https://while-true-do.org)

Mail: [hello@while-true-do.org](mailto:hello@while-true-do.org)
