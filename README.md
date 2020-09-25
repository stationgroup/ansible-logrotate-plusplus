# ansible-logrotate-plusplus


# Ansible Role: logrotate-plusplus

## Description

Ansible role which installs and configures logrotate
It can test if paths exist before writing a logrotate config to the server.
Load the roles default vars with custom paths and per path parameters, and run the playbook across a dynamic
infrastructure and only write logerotate rules to the appropriate system with the correct paths present.

This project was based of https://github.com/arillso/ansible.logrotate 1.5.2
(https://github.com/arillso/ansible.logrotate/commit/038649f7933c21ba9f1f2c8363bfb4d49aaf46f2)

**This Ansible role was made possible by: Ansible consultant _Serge van Ginderachter_ of _Ginsys_:**

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
| [<img src="https://avatars2.githubusercontent.com/u/382239" width="100px;"/><br /><sub>Serge van Ginderachter</sub>](https://github.com/srgvg)<br />[📖](https://github.com/stationgroup/ansible-experiments/commits?author=srgvg) | [<img src="https://avatars0.githubusercontent.com/u/4183827?s=original" width="100px;"/><br /><sub>Ginsys</sub>](https://ginsys.eu/)<br />[🌐](https://ginsys.eu/) |
| :---: | :---: |

<!-- ALL-CONTRIBUTORS-LIST:END -->


## Installation

```bash
  ansible-galaxy install stationgroup.logrotate-plusplus
```

## Requirements

None

## Role Variables

### imclude files

Path to the imclude files.

```yml
logrotate_include_dir: /etc/logrotate.d
```

### logrotate_use_hourly_rotation

Enable hourly rotation with cron.

```yml
logrotate_use_hourly_rotation: false
```

### logrotate options

List of global options.

```yml
logrotate_options:
  - weekly
  - rotate 4
  - create
  - dateext
  - su root syslog
```

### Package

package name to install logrotate.

```yml
logrotate_package: logrotate
```

### default config

logroate for wtmp

```yml
logrotate_wtmp:
  logs:
    - /var/log/wtmp
  options:
    - missingok
    - monthly
    - create 0664 root utmp
    - rotate 1
```

logroate for btmp

```yml
logrotate_btmp:
  logs:
    - /var/log/btmp
  options:
    - missingok
    - monthly
    - create 0660 root utmp
    - rotate 1
```

### applications config

More log files can be added that will logorate.

```yml
logrotate_applications: []
```

#### Example

The following options are available.

```yml
logrotate_applications:
  - name: name-your-log-rotate-application
    definitions:
      - logs:
          - /var/log/apt/term.log
          - /var/log/apt/history.log
        options:
          - rotate 12
          - monthly
          - missingok
          - notifempty
```

## Dependencies

None

## Example Playbook

```yml
- hosts: all
  roles:
    - stationgroup.logrotate-plusplus
```

## License

This project is under the MIT License.
