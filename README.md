[![CI](https://github.com/de-it-krachten/ansible-role-ownload_docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-ownload_docker/actions?query=workflow%3ACI)


# ansible-role-ownload_docker

Sets up a Wordpress instance using Docker.<br>
This consists of Wordpress/PHP/MySQL/nginx<br>



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
# Retrieve SSL certificate from let's encrypt
ownload_certbot: true

# Custom SSL certificate
# ownload_ssl_key: /path/to/key
# ownload_ssl_certificate_chain: /path/to/certificate/chain
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'ownload_docker'
  hosts: all
  become: "yes"
  vars:
    mysql_root_password: ownload
    mysql_user: ownload
    mysql_password: ownload
    mysql_database: ownload
    ownload_certbot: False
    ownload_domain: example.com
    ownload_docker_data: /export/docker/ownload
    ownload_db_name: ownload
    ownload_db_user: ownload
    ownload_db_pwd: ownload
    letsencrypt_email: "info@{{ ownload_domain }}"
    letsencrypt_domain: "{{ ownload_domain }}"
    letsencrypt_domains: "{{ [ ownload_domain ] }}"
  roles:
    - openssl
  tasks:
    - name: Include role 'ownload_docker'
      ansible.builtin.include_role:
        name: ownload_docker
</pre></code>
