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
ansible-galaxy install madudka.debian-security
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

| Name            | Description                   | Value example |
|-----------------|-------------------------------|---------------|
| `ssh_port`      | Default ssh port.             | 22            |
| `check_timeout` | Timeout of checking ssh port. | 10            |

User variables `/vars/main.yml`:

| Name                 | Description                          | Value example              |
|----------------------|--------------------------------------|----------------------------|
| `ssh_port_custom`    | Custom ssh port.                     | 212                        |
| `my_ip`              | Ip address of your machine.          | 192.168.0.16               |
| `sshd_jail_log_path` | Path of sshd jail fail2ban log file. | /var/log/fail2ban_sshd.log |

Dependencies
------------

No dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: madudka.debian-security }

License
-------

GPL-3.0-only

Author Information
------------------

https://madudka.github.io/