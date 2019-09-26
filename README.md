cloud3rsio.iptables
=========

update iptables setting.

Installation
------------

```bash
$ ansible-galaxy install cloud3rsio.iptables
```

Requirements
------------

Nothing.

Role Variables
--------------

| Key | Default Value | Type |
| ------------- | ------------- | ------------- |
| `iptables_config` | Reference to [enable/defaults/main.yml](enable/defaults/main.yml) | String |

Dependencies
------------

Nothing.

Example Playbook
----------------

```yaml
# Enable
- hosts: all
  roles:
    - role: cloud3rsio.iptables/enable
      iptables_config: |
        *filter
        -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
        -A INPUT -s 127.0.0.1/32 -j ACCEPT
        -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
        -A INPUT -j DROP
        COMMIT

# Disable
- hosts: all
  roles:
    - role: cloud3rsio.iptables/disable
```

License
-------

[MIT](LICENSE)

Author Information
------------------

- youyo
