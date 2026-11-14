# Ansible Role for Redis (Server)

[![CircleCI](https://circleci.com/gh/lifeofguenter/ansible-role-redis/tree/main.svg?style=svg)](https://circleci.com/gh/lifeofguenter/ansible-role-redis/tree/main)

Redis from [packages.redis.io](https://packages.redis.io), whose build
carries the modules the distributions' leave out: search and query
(`FT.*`), time series (`TS.*`), JSON and the probabilistic types (`BF.*`
and the others). A Redis the distribution installed before is replaced in
place, its data and its `/etc/redis/redis.conf` kept, and the modules are
added to that file.

The major release in `redis_version` is followed: every run installs
packages.redis.io's newest release of it (restarting Redis when there is
one), and no other version, the distribution's included.

Search and query indexes only database 0.

## Requirements

Debian 12 or 13, or Ubuntu 22.04 or 24.04: the releases packages.redis.io
builds Redis 8 for.

## Role Variables

```yaml
redis_bind: 127.0.0.1

redis_munin_connect: '{{ redis_bind }}'

redis_maxmemory: 1g

redis_maxmemory_policy: allkeys-lru

redis_version: 8

# loaded at start; leave one out to not load it
redis_modules:
  - redisearch
  - redistimeseries
  - rejson
  - redisbloom

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
