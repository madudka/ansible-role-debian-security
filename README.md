Debian security
=========

The debian security role includes the following steps:

1. Changing the default SSH port.
2. Installing and configuring Fail2ban.
3. Setting up the UFW firewall.


Tested on operating system Debian GNU/Linux trixie/sid (kernel Linux 6.1.0-18-amd64).

Install
-------
```
ansible-galaxy install madudka.debian_security
```

Requirements
------------
Min ansible version: 2.16.8

Some tasks use flag `become: true`.
You can use any method to pass the `ansible_become_user` and `ansible_become_password` parameters.
More: https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_privilege_escalation.html

When using early versions of Ansible you need to install `community.general` collection:

```
ansible-galaxy collection install community.general
```


Role Variables
--------------
Defaults variables `/defaults/main.yml`:

| Name                        | Description                             | Value example                   |
| --------------------------- | --------------------------------------- | ------------------------------- |
| `cfg_owner`                 | User owning the filesystem object.      | root                            |
| `cfg_group`                 | Group owning the filesystem object.     | root                            |
| `ssh_port`                  | Default ssh port.                       | 22                              |
| `check_timeout`             | Timeout of checking ssh port.           | 10                              |
| `sshd_config_path`          | Path to the sshd_config file.           | /etc/ssh/sshd_config            |
| `sshd_config_backup_path`   | Path to the backup of sshd_config file. | /etc/ssh/sshd_config.backup     |
| `fail2ban_conf_path`        | Path to the fail2ban.conf file.         | /etc/fail2ban/fail2ban.conf     |
| `jail_conf_path`            | Path to the jail.conf file.             | /etc/fail2ban/jail.conf         |
| `jail_conf_local_path`      | Path to the jail.local file.            | /etc/fail2ban/jail.local        |
| `jail_sshd_conf_local_path` | Path to the sshd.local file.            | /etc/fail2ban/jail.d/sshd.local |
| `jail_sshd_log_path`        | Path to the fail2ban_sshd.log file.     | /var/log/fail2ban_sshd.log      |

User variables `/vars/main.yml`:

| Name                 | Description               | Value example   |
| -------------------- | ------------------------- | --------------- |
| `ssh_port_custom`    | Custom ssh port.          | 212             |
| `fail2ban_ignoreips` | Fail2ban whitelist of IP. | - 192.168.0.165 |

Dependencies
------------

No dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: madudka.debian_security }

License
-------

GPL-3.0-only

Author Information
------------------

https://madudka.github.io/