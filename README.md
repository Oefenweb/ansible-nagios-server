## nagios-server

[![CI](https://github.com/Oefenweb/ansible-nagios-server/workflows/CI/badge.svg)](https://github.com/Oefenweb/ansible-nagios-server/actions?query=workflow%3ACI)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-nagios--server-blue.svg)](https://galaxy.ansible.com/Oefenweb/nagios_server)

Set up nagios in Debian-like systems (server side).

#### Requirements

None

#### Variables

* `nagios_server_private_keys`: [default: `[]`]: Private key declarations
* `nagios_server_private_keys.{n}.owner`: [optional, default `nagios`]: The name of the user that should own the file
* `nagios_server_private_keys.{n}.group`: [optional, default `owner`, `nagios`]: The name of the group that should own the file
* `nagios_server_private_keys.{n}.mode`: [optional, default `0600`]: The UNIX permission mode bits of the file
* `nagios_server_private_keys.{n}.src`: [required]: The local path of the key
* `nagios_server_private_keys.{n}.dest`: [optional, default: default `src | basename`]: The remote path of the key (relative to `home/.ssh/`)
* `nagios_server_private_keys.{n}.state`: [optional, default: `present`]: State

* `nagios_server_htpasswd_users`: [default: `[]`]: User declarations
* `nagios_server_htpasswd_users.{n}.name`: [required]: Username
* `nagios_server_htpasswd_users.{n}.password`: [required]: Password

* `nagios_server_htdigest_realm`: [optional, default `Nagios4`]: Apache2 digest authentication realm (Nagios 4 only)

* `nagios_server_cgi`: [default: `{}`]: CGI declarations
* `nagios_server_cgi.refresh_rate`: [optional, default: `90`]: Refresh rate
* `nagios_server_cgi.result_limit`: [optional, default: `100`]: Default page limit

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

* `nagios_server_host_templates`: [default: `[]`]: Host definition template
* `nagios_server_host_templates.{n}.name`: [required]: The name of this host template
* `nagios_server_host_templates.{n}.notifications_enabled`: [optional, default: `1`]: Host notifications are enabled
* `nagios_server_host_templates.{n}.event_handler_enabled`: [optional, default: `1`]: Host event handler is enabled
* `nagios_server_host_templates.{n}.flap_detection_enabled`: [optional, default: `1`]: Flap detection is enabled
* `nagios_server_host_templates.{n}.failure_prediction_enabled`: [optional, default: `1`]: Failure prediction is enabled
* `nagios_server_host_templates.{n}.process_perf_data`: [optional, default: `1`]: Process performance data
* `nagios_server_host_templates.{n}.retain_status_information`: [optional, default: `1`]: Retain status information across program restarts
* `nagios_server_host_templates.{n}.retain_nonstatus_information`: [optional, default: `1`]: Retain non-status information across program restarts
* `nagios_server_host_templates.{n}.check_command`: [optional, default: `check-host-alive`]: Default check command
* `nagios_server_host_templates.{n}.max_check_attempts`: [optional, default: `10`]: Maxium check attempts
* `nagios_server_host_templates.{n}.notification_interval`: [optional, default: `0`]: Notification interval
* `nagios_server_host_templates.{n}.notification_period`: [optional, default: `24x7`]: Notification period
* `nagios_server_host_templates.{n}.notification_options`: [optional, default: `d,u,r`]: Notification options
* `nagios_server_host_templates.{n}.contact_groups`: [optional, default: `admins`]: Default contact groups
* `nagios_server_host_templates.{n}.register`: [optional, default: `0`]: Register host
* `nagios_server_host_templates.{n}.variables`: [optional, default: `[]`]: List of optional host variables
* `nagios_server_host_templates.{n}.variables.{n}.name`: [required]: The name of variable
* `nagios_server_host_templates.{n}.variables.{n}.value`: [required]: The value of variable

* `nagios_server_hostextinfo`: [default: `[]`]: Hostextinfo declarations (deprecated for nagios version 4 and up)
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
* `nagios_server_hosts.{n}.host_template`: [optional, default: `generic-host`]: Host definition template
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

* `nagios_server_generic_service`: [default: `{}`]: Generic service declarations
* `nagios_server_generic_service.name`: [optional, default: `generic-service`]: The 'name' of this service template
* `nagios_server_generic_service.active_checks_enabled`: [optional, default: `1`]: Active service checks are enabled
* `nagios_server_generic_service.passive_checks_enabled`: [optional, default: `1`]: Passive service checks are enabled/accepted
* `nagios_server_generic_service.parallelize_check`: [optional, default: `1`]: Active service checks should be parallelized (disabling this can lead to major performance problems)
* `nagios_server_generic_service.obsess_over_service`: [optional, default: `1`]: We should obsess over this service (if necessary)
* `nagios_server_generic_service.check_freshness`: [optional, default: `0`]: Default is to NOT check service 'freshness'
* `nagios_server_generic_service.notifications_enabled`: [optional, default: `1`]: Service notifications are enabled
* `nagios_server_generic_service.event_handler_enabled`: [optional, default: `1`]: Service event handler is enabled
* `nagios_server_generic_service.flap_detection_enabled`: [optional, default: `1`]: Flap detection is enabled
* `nagios_server_generic_service.failure_prediction_enabled`: [optional, default: `1`]: Failure prediction is enabled
* `nagios_server_generic_service.process_perf_data`: [optional, default: `1`]: Process performance data
* `nagios_server_generic_service.retain_status_information`: [optional, default: `1`]: Retain status information across program restarts
* `nagios_server_generic_service.retain_nonstatus_information`: [optional, default: `1`]: Retain non-status information across program restarts
* `nagios_server_generic_service.notification_interval`: [optional, default: `0`]: Only send notifications on status change by default.
* `nagios_server_generic_service.is_volatile`: [optional, default: `0`]: This directive is used to denote whether the service is "volatile"
* `nagios_server_generic_service.check_period`: [optional, default: `24x7`]: This directive is used to specify the short name of the time period during which active checks of this service can be made.
* `nagios_server_generic_service.normal_check_interval`: [optional, default: `5`]:  The interval at which the service is checked under "normal" circumstances.
* `nagios_server_generic_service.retry_check_interval`: [optional, default: `1`]:  The interval at which the service is checked during retries.
* `nagios_server_generic_service.max_check_attempts`: [optional, default: `4`]: This directive is used to define the number of times that Nagios will retry the host check command if it returns any state other than an OK state.
* `nagios_server_generic_service.notification_period`: [optional, default: `24x7`]: This directive is used to specify the short name of the time period during which notifications of events for this host can be sent out to contacts.
* `nagios_server_generic_service.notification_options`: [optional, default: `w,u,c,r`]: This directive is used to determine when notifications for the host should be sent out.
* `nagios_server_generic_service.contact_groups`: [optional, default: `admins`]: This is a list of the short names of the contact groups that should be notified whenever there are problems (or recoveries) with this service.
* `nagios_server_generic_service.action_url`: [optional, default: undefined]: 	This directive is used to define an optional URL that can be used to provide more actions to be performed on the service. (eg Displaying the nagiosgraph page).
* `nagios_server_generic_service.register`: [optional, default: `0`]: DONT REGISTER THIS DEFINITION - ITS NOT A REAL SERVICE, JUST A TEMPLATE!

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

* `nagios_server_check_external_commands`: [default: `false`]: If you want to be able to use the CGI command interface you will have to enable this
* `nagios_server_use_regexp_matching`: [default: `false`]: This option determines whether or not various directives in your object definitions will be processed as regular expressions

* `nagios_server_absent_paths`: [default: `[]`]: Paths to remove (e.g. `['/etc/nagios3/conf.d/web-01.example.com_nagios2.cfg']`)

## Dependencies

None

## Recommended

* `nagios-client` ([see](https://github.com/Oefenweb/ansible-nagios-client))

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
