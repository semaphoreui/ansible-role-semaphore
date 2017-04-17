# Ansible UI Semaphore

[![Build Status](https://travis-ci.org/morbidick/ansible-role-semaphore.svg?branch=master)](https://travis-ci.org/morbidick/ansible-role-semaphore)

Ansible role to install and configure the Ansible UI Semaphore.

## Requirements

None. But for an production environment you should install a webserver as proxy for ssl termination.

## Example playbook

````yaml
- hosts: all
  become: yes

  roles:
  - semaphore
````

## Role variables

None of the variables below are required.

| Variable                 | Default   | Comment |
| :---                     | :---      | :---    |
| `semaphore_version`      | `v2.2.0`  | the version to download, also see `semaphore_download_url` and `semaphore_download_sha256` |
| `semaphore_mysql_install` | `true`   | whether to install mysql on the host, installs with the password `mysql_root_password` |
| `semaphore_mysql_create_db` | `true` | whether to create the mysql db and user |
| `semaphore_mysql_host`:`semaphore_mysql_port` | `127.0.0.1`:`3000` | the mysql host |
| `semaphore_mysql_db`     | semaphore | the mysql database |
| `semaphore_mysql_user`   | semaphore | the mysql user |
| `semaphore_mysql_password` | semaphore | the mysql user password |
| `semaphore_user`         | semaphore | the user and systemd identifier semaphore runs as |
| `semaphore_port`         | `3000`    | the port semaphore binds to |
| `semaphore_path`         | /opt/semaphore | destination for the binary |
| `semaphore_config_path`  | /etc/semaphore/semaphore.json | config file |
| `semaphore_default_user` | admin | login name of the default user |
| `semaphore_default_user_name` | `{{ semaphore_default_user }}` | his human readable name |
| `semaphore_default_user_password` | admin | the password |
| `semaphore_default_user_mail` | admin@example.com | and mail adress |

For all options see [defaults/main.yml](defaults/main.yml)

## Demo/Development

You can use the [Vagrantfile](Vagrantfile) for local testing, just install vagrant and virtualbox, execute the following commands. Open your browser at [127.0.0.1:5000](http://127.0.0.1:5000) and login with user and password `admin`.

````bash
vagrant up
vagrant provision
````

## License

MIT
