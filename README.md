# Docker Swarm Cluster

Docker Swarm Cluster is an Ansible role to create a Docker Swarm cluster using
the inventory file groups, `docker_swarm_managers` and `docker_swarm_workers`.
The role will initialize the cluster with the first host from the
`docker_swarm_managers` group and then join group hosts to the cluster.

## Requirements

Docker must already be installed on each host and the `docker` Python package is
required for the role's Ansible modules.

## Role Variables

By default, the role will use the IP address of first host from the
`docker_swarm_managers` group as the
[advertised address](https://docs.docker.com/engine/reference/commandline/swarm_init/#--advertise-addr)
of the cluster. To use a custom address, set the
`docker_swarm_advertise_address` variable.

## Example Playbook

The following play first uses [Jeff Geerling](https://github.com/geerlingguy)'s
Pip and Docker roles to install the dependencies on the hosts. Then the play
creates the Docker Swarm cluster.

```yaml
- hosts: all
  roles:
    - geerlingguy.pip
    - geerlingguy.docker
    - scruffaluff.docker_swarm_cluster
```

## License

Docker Swarm Cluster is distributed under a
[MIT license](https://github.com/wolfgangwazzlestrauss/ansible-role-docker-swarm-cluster/blob/master/LICENSE.md).
