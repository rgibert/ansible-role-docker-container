# Docker Container

Standardized setup for managing my Docker containers

## Role Variables

| Variable | Description |
|----------|-------------|
| docker_container_group_name | Primary group for the user specified under docker_container_user_name |
| docker_container_user_name | User to pass into the container |
| docker_container_dirs | Directories to create on the docker host |
| docker_container_files | Files to copy to the docker host |
| docker_container_volumes | Volumes to mount within the container |
| docker_container_name | Name for the running container |
| docker_container_image | Image to use to create the container |
| docker_container_network | network for the container (defaults to {{ docker_container_name }}_default |
| docker_container_ports | ports to expose |
| docker_container_tz | Timezone to pass into the container |

## Dependencies

- Docker installed
- pip installed

## Example Playbook

```yaml
- hosts:
   - server
  roles:
    - role: rgibert.docker_container
      docker_container_name: cadvisor
      docker_container_image: google/cadvisor:latest
      docker_container_user_name: richard
      docker_container_group_name: users
      docker_container_dirs:
        - /var/run/containers/cadvisor
      docker_container_ports:
        - "8080:8080"
      docker_container_volumes:
        - "/:/rootfs:ro"
        - "/var/run:/var/run"
        - "/sys:/sys:ro"
        - "/var/lib/docker/:/var/lib/docker:ro"
```

## License

GPLv3

## Author Information

Richard Gibert\
[richard@gibert.ca](mailto:richard@gibert.ca)\
[https://richard.gibert.ca/](https://richard.gibert.ca/)