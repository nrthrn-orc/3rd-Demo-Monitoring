Sentry monitoring role
=========

This role installs monitoring agent and enable the status information handlers for Nginx, Redis, PostgreSQL, Zookeper and memcached. The role also adds the keys of the required IAM user.

Role Variables
--------------

| Variable                       | Description              |
| ------------------------------ | ------------------------ |
| `ansible_user`                 | Your Ansible user name.  |
| `ansible_ssh_private_key_file` | Path to ssh private key. |

Example Playbook
----------------

    - hosts: sentry
      become: true
      gather_facts: no
      roles:
         - { role: sentry-monitoring-role }
