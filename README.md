# Role Name

Ansible role to install docker and docker-compose and copy docker-compose projects.

It can also manage (bring up and pull images) projects.

## Requirements

- debian

## Role Variables

The role supports the following variables

| Name       | Required/Default         | Description                                                                                        |
|------------|:------------------------:|----------------------------------------------------------------------------------------------------|
| `docker_compose_docker_users` | `[]`       | A list of users that should be added to the docker group
| `docker_compose_target_dir` | `/opt/docker-compose` | The directory where the docker compose projects should be copied to. |
| `docker_compose_project_folders_dir` | :heavy_check_mark:                   | The directory of docker-compose projects (folders) to copy.                                                                       |
| `docker_compose_managed_projects` | `[]`                      | The names of docker-compose projects which should be managed.                                            |


## Example

The following example playbook assumes that you cloned this role to roles/docker-compose (i.e. the name of the role is docker-compose instead of docker-compose) and that you have the following structure in your `files` folder:

```text
files/
└── docker-composes
    └── docker01
        ├── aThirdProject
        │   └── docker-compose.yml
        ├── someOtherProject
        │   └── docker-compose.yml
        └── someProject
            └── docker-compose.yml
```

```yml
- hosts: kube01
  roles:
    - role: docker-compose
      docker_compose_docker_users:
        - admin
        - myOtherUser
      docker_compose_project_folders_dir: "docker-composes/docker01"
      docker_compose_managed_projects:
        - someProject
```


## License

This work is licensed under the [MIT License](./LICENSE).


## Author Information

- [Tim Neumann (neumatm)](https://github.com/neumantm) _tim at c-hack.de_
