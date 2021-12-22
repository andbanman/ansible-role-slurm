ansible-role-slurm
==================

Install and configure Slurm cluster on one or more hosts.

Role Variables
--------------

All variables are optional. If nothing is set, the role will install the Slurm client programs, munge, and create a `slurm.conf` with a single `localhost` node and `debug` partition. See the [defaults](defaults/main.yml) and [example playbooks](examples/) for examples.

```yaml
slurm_roles: []         # Zero or more of 'ctl','dbd','node'; the default is all of the above.
                        # Any other value implies a client, i.e. login, node.

slurm_config: {}        # Dictionary with keys matching slurm.conf fields. All of the slurm
                        # configuration is defined here except for Nodes and Partitions. Some
                        # fields have default values (see __slurm_config_default in defaults).

slurm_cgroup_config: {} # Dictionary with keys matching cgroup.conf fields. Configure proctrack/cgroup

slurm_nodes: [{}]       # Required key 'name' to set 'NodeName', other keys match slurm.conf fields
slurm_partitions: [{}]  # Required key 'name' to set 'Partition', other keys match slurm.conf fields

slurm_munge_key: ""     # Random bytes to be used as the key, WARNING: default value is not secure,
                        # Generate new and place in encrypted secrets file

slurm_upgrade: False    # Whether to upgrade slurm packages
slurm_mail: False       # Whether to install a modified slurm-mail module that works with postfix
                        # and assumes the canonical sender is configured
```

License
-------

MIT

Author Information
------------------

This role was written by [Andrew Banman](https://github.com/andbanman) while working as a DevOps engineer at Pacific Northwest Research Institute. This role was based on [galaxyproject/ansible-slurm](https://github.com/galaxyproject/ansible-slurm.git).
