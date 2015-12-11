## nagios-server

[![Build Status](https://travis-ci.org/Oefenweb/ansible-nagios-server.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-nagios-server) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-nagios-server-blue.svg)](https://galaxy.ansible.com/list#/roles/6435)

Set up Nagios server in Debian-like systems.

#### Requirements

None

#### Variables

None

* `nagios_server_private_keys`: [default: `[]`]: Private key declarations
* `nagios_server_private_keys.{n}.owner`: [optional, default `nagios`]: The name of the user that should own the file
* `nagios_server_private_keys .{n}.group`: [optional, default `owner`, `nagios`]: The name of the group that should own the file
* `nagios_server_private_keys.{n}.mode`: [optional, default `0600`]: The UNIX permission mode bits of the file
* `nagios_server_private_keys.{n}.src`: [required]: The local path of the key
* `nagios_server_private_keys.{n}.dest`: [optional, default: default `src | basename`]: The remote path of the key (relative to `home/.ssh/`)
* `nagios_server_private_keys.{n}.state`: [optional, default: `present`]: State

* `nagios_server_htpasswd_users`: [default: `[]`]: User declarations
* `nagios_server_htpasswd_users.{n}.name`: [required]: Username
* `nagios_server_htpasswd_users.{n}.password`: [required]: Password

* `nagios_server_user_macros`: [default: `{}`]: User macro declarations
* `nagios_server_user_macros.key`: [required]: Identifier of the macro (1 through 32). Nagios supports up to 32 $USERx$ macros ($USER1$ through $USER32$)
* `nagios_server_user_macros.key.value`: [default: `{}`]: Macro value

* `nagios_server_contacts`: [default: `[]`]: Contact declarations
* `nagios_server_contacts.{n}.name`: [required]: Contact name
* `nagios_server_contacts.{n}.alias`: [required]: Contact alias
* `nagios_server_contacts.{n}.service_notification_command`: [required]: Service notification command
* `nagios_server_contacts.{n}.host_notification_command`: [required]: Host notification command
* `nagios_server_contacts.{n}.email`: [optional]: Contact name

* `nagios_server_contactgroups`: [default: `[]`]: Contactgroup declarations
* `nagios_server_contactgroups.{n}.name`: [required]: Contactgroup name
* `nagios_server_contactgroups.{n}.alias`: [required]: Contactgroup alias
* `nagios_server_contactgroups.{n}.members`: [required]: List of contactgroup members

* `nagios_server_hostextinfo`: [default: `[]`]: Hostextinfo declarations
* `nagios_server_hostextinfo.{n}.hostgroup`: [required]: Hostgroup name
* `nagios_server_hostextinfo.{n}.notes`: [required]: Notes
* `nagios_server_hostextinfo.{n}.icon_image`: [required]: Icon image
* `nagios_server_hostextinfo.{n}.icon_image_alt`: [required]: Alternative text for icon image
* `nagios_server_hostextinfo.{n}.vrml_image`: [required]: Vrml image
* `nagios_server_hostextinfo.{n}.statusmap_image`: [required]: Statusmap image

* `nagios_server_hostgroups`: [default: `[]`]: Hostgroup declarations
* `nagios_server_hostgroups.{n}.name`: [required]: Hostgroup name
* `nagios_server_hostgroups.{n}.alias`: [required]: Hostgroup alias
* `nagios_server_hostgroups.{n}.members`: [required]: List of hostgroup members

* `nagios_server_hosts`: [default: `[]`]: Host declarations
* `nagios_server_hosts.{n}.name`: [required]: Hostname
* `nagios_server_hosts.{n}.alias`: [required]: Host alias
* `nagios_server_hosts.{n}.address`: [required]: Host address

* `nagios_server_commands_custom`: [default: `[]`]: Custom command declarations
* `nagios_server_commands_custom.{n}.name`: [required]: Name of command
* `nagios_server_commands_custom.{n}.line`: [required]: Command line

* `nagios_server_commands_notification`: [default: `[]`]: Notification command declarations
* `nagios_server_commands_notification.{n}.name`: [required]: Name of command
* `nagios_server_commands_notification.{n}.line`: [required]: Command line

* `nagios_server_commands_performance_data`: [default: `[]`]: Performance data command declarations
* `nagios_server_commands_performance_data.{n}.name`: [required]: Name of command
* `nagios_server_commands_performance_data.{n}.line`: [required]: Command line

* `nagios_server_services`: [default: `[]`]: Service declarations
* `nagios_server_services.{n}.hostgroup`: [required]: Name of command
* `nagios_server_services.{n}.description`: [required]: Command line
* `nagios_server_services.{n}.check_command`: [required]: Command line

* `nagios_server_timeperiods`: [default: `[]`]: Time period declarations
* `nagios_server_timeperiods.{n}.name`: [required]: Name of time period
* `nagios_server_timeperiods.{n}.alias`: [required]: Time period alias
* `nagios_server_timeperiods.{n}.periods`: [default: `[]`]: Period intervals
* `nagios_server_timeperiods.{n}.periods.key`: [required]: Day of the week (eg. monday)
* `nagios_server_timeperiods.{n}.periods.key.value`: [required]: Time interval (eg. 08:00-23:00)


## Dependencies

None

#### Example

```yaml
---
- hosts: all
  roles:
    - nagios-server
```

#### License

MIT

#### Author Information

* Mark van Driel
* Mischa ter Smitten

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-nagios-server/issues)!
