# Ansible Canopy Connector Monitoring [![Build Status](https://github.com/onaio/ansible-canopy-connector-monitoring/workflows/CI/badge.svg)](https://github.com/onaio/ansible-canopy-connector-monitoring/actions?query=workflow%3ACI)

Use this role to set up [Canopy connector monitoring](https://github.com/onaio/canopy-connector-monitoring).

## Role Variables

Some of the more important variables are briefly described below.  You can see all variables by looking at the [defaults/main.yml](defaults/main.yml) file.

### canopy_connector_nifi_url

This is the URL for the NiFi instance that you wish to monitor.

```yml
canopy_connector_nifi_url: https://nifi-stage.ona.io
```

### canopy_connector_nifi_username

This is the NiFi basic auth username.  This is optional and should be left out if not needed.

```yml
canopy_connector_nifi_username: admin
```

### canopy_connector_nifi_password

This is the NiFi basic auth password.  This is optional and should be left out if not needed.

```yml
canopy_connector_nifi_password: hunter2
```

### canopy_connector_monitoring_setup_cron

Determines whether or not the monitoring command should be set up to run periodically using cron.  This defaults to `true`.

```yml
canopy_connector_monitoring_setup_cron: true
```

### canopy_connector_monitoring_cron_minute

This specifies how often the monitoring command should run.

```yml
canopy_connector_monitoring_cron_minute: "*/5"  # cron format
```

## Dependencies

At this time, this role has no dependencies.

## Example Playbook

```yml
- hosts: servers
  roles:
    - role: ansible-canopy-connector-monitoring
      vars:
        - canopy_connector_nifi_username: admin
        - canopy_connector_nifi_password: hunter2
        - canopy_connector_monitoring_cron_minute: "*/5"
```

## Testing

This project uses molecule for testing.

Start by creating a virtual environment and installing python packages

```sh
pip install -r requirements/dev.in
```

Then to run the full test sequence:

```sh
tox
```

## License

Apache 2

## Authors

[Ona Engineering](https://ona.io)
