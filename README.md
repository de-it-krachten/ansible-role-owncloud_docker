[![CI](https://github.com/de-it-krachten/ansible-role-owncloud_docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-owncloud_docker/actions?query=workflow%3ACI)


# ansible-role-owncloud_docker

Sets up a Owncloud using Docker



## Dependencies

#### Roles
None

#### Collections
- community.general
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8<sup>1</sup>
- RockyLinux 9<sup>1</sup>
- OracleLinux 8<sup>1</sup>
- OracleLinux 9<sup>1</sup>
- AlmaLinux 8<sup>1</sup>
- AlmaLinux 9<sup>1</sup>
- Debian 10 (Buster)<sup>1</sup>
- Debian 11 (Bullseye)<sup>1</sup>
- Ubuntu 18.04 LTS<sup>1</sup>
- Ubuntu 20.04 LTS<sup>1</sup>
- Ubuntu 22.04 LTS<sup>1</sup>
- Fedora 35<sup>1</sup>
- Fedora 36<sup>1</sup>
- Alpine 3<sup>1</sup>
- Docker dind (CI only)

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# FQDN of the owncloud server
owncloud_fqdn: owncloud.example.com

# Owncloud port
owncloud_port: 8080

# Owncloud admin user + password
owncloud_admin_username: admin
owncloud_admin_password: admin

# Database type to use
owncloud_db_type: mysql

# Databae root password
owncloud_db_root_password: owncloud

# Name of the database server
owncloud_db_host: mariadb

# Name of the database itself
owncloud_db_name: owncloud

# Name of the database user
owncloud_db_user: owncloud

# Password for the database user
owncloud_db_password: owncloud

# Server for nginx to connect to
owncloud_webapp_host: owncloud
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'owncloud_docker'
  hosts: all
  become: "yes"
  vars:
    owncloud_docker_data: /export/docker/owncloud
  roles:
    - openssl
  tasks:
    - name: Include role 'owncloud_docker'
      ansible.builtin.include_role:
        name: owncloud_docker
</pre></code>
