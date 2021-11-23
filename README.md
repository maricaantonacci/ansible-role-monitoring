# ansible-role-monitoring [![Ansible Lint](https://github.com/DODAS-TS/ansible-role-monitoring/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/DODAS-TS/ansible-role-monitoring/actions/workflows/ansible-lint.yml)

A role to setup a custom monitoring on a node

Requirements
------------

This role requires [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) to be installed. Also, Grafana tasks requires [Go](https://golang.org/).

Role Variables
--------------

### defaults

Variable for the monitoring service:

- `monitoring_project_name`: string with the name of the current project (user's choice)
- `monitoring_use_gpu`: bool, if the GPU is used and then monitored (default: false)
- `monitoring_iam_url`: URL of the IAM service
- `monitoring_iam_groups`: string with the name of the IAM groups allowed (space separated)
- `monitoring_iam_admin_groups`: string with the name of the IAM groups that will be admin (space separated)
- `monitoring_server_ip`: string with the ip of the current server

Specific service variables:

- `service_grafana`: "yes" if you want to setup also grafana
- `service_grafana_port`: int, the grafana service port
- `service_grafana_admin_user`: string
- `service_grafana_admin_password`: string
- `service_grafana_client_id`: string (used for the IAM login)
- `service_grafana_client_secret`: string (used for the IAM login)

### vars

The following string variables will be filled with the docker service information:

- `nvidia_monitoring`: string, (default: "")
- `nvidia_depends`: string, (default: "")
- `prometheus_nvidia`: string, (default: "")
- `grafana_service`: string, (default: "")
- `service_grafana_disable_admin_creation`: bool (default: true)

Dependencies
------------

There are no other dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
    - hosts: servers
      roles:
         - role: dodas-ts-monitoring
           monitoring_project_name: compute_server
           service_grafana_admin_user: admin
           service_grafana_admin_password: example_password

```

License
-------

Apache 2.0

Author Information
------------------

DODAS-TS
