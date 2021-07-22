# Ansible Role for Loki

![molecule](https://github.com/elan/monitoring_loki/actions/workflows/molecule.yml/badge.svg)

Install the latest [loki](https://github.com/grafana/loki) version with [ansible](https://docs.ansible.com/).

## Role Variables

Have a look at the [defaults](defaults/main.yml) to see what variables you can set.

You can specify the log retention period by setting the variable `loki_retention_deletes` to `true` and
`loki_retention_period` to the desired retention period.

The role contains a template for a basic config file.
In most cases, however, you would probably want to provide your own config-templates.
You can achieve this by changing the path to the template file in `loki_config_template`.

## Example Playbook

Just add the role to your playbook:

```yaml
- hosts: all
  become: true
  roles:
    - elan.monitoring_loki
```

## Development

For development and testing you can use [molecule](https://molecule.readthedocs.io/en/latest/).
With podman as driver you can install it like this – preferably in a virtual environment (if you use docker, substitute `podman` with `docker`):

```bash
pip install -r .dev_requirements.txt
```

Then you can *create* the test instances, apply the ansible config (*converge*) and *destroy* the test instances with these commands:

```bash
molecule create
molecule converge
molecule destroy
```

If you want to inspect a running test instance use `molecule login --host <instance_name>`, where you replace `<instance_name>` with the desired value.

## License

[BSD-3-Clause](LICENSE)

## Author Information

[ELAN e.V](https://elan-ev.de/)
