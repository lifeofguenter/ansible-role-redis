# Ansible Role for Redis (Server)

[![CircleCI](https://circleci.com/gh/lifeofguenter/ansible-role-redis/tree/main.svg?style=svg)](https://circleci.com/gh/lifeofguenter/ansible-role-redis/tree/main)

## Requirements

_none_

## Role Variables

```yaml
redis_bind: 127.0.0.1

redis_munin_connect: '{{ redis_bind }}'

redis_maxmemory: 1g

redis_default_release: '{{ ansible_distribution_release }}'

# optional

redis_requirepass:

redis_tls_cert_file:

redis_tls_key_file:

redis_tls_dh_params_file:

redis_tls_ca_cert_dir: /etc/ssl/certs
```

## Dependencies

_none_

## Example

`requirements.yml`

```yml
roles:
  - name: lifeofguenter.redis
```

`playbook.yml`

```yaml
- hosts: servers
  tasks:
    - ansible.builtin.import_role: lifeofguenter.redis
```

## License

[MIT](LICENSE)

## Author Information

Günter Grodotzki <gunter@grodotzki.com>
