OPNsense: DHCP
==============

An Ansible role to configure the DHCP server on an opnSense firewall.

Requirements
------------

This role requires the `lxml` python package to be installed on the host system.

Role Variables
--------------

|           Variable           |     Type     |                            Description                            |
| :--------------------------: | :----------: | :---------------------------------------------------------------: |
|        opnsense_dhcp         | list(object) | List of configuration settings for each dhcp server individually. |
|    opnsense_dhcp.[].iface    |    string    |             The interface this DHCP server binds to.              |
|   opnsense_dhcp.[].enabled   |     bool     |         Enable/Disable the DHCP server on the interface.          |
| opnsense_dhcp.[].range.start |    string    |               The IP range start for the DHCP pool.               |
|  opnsense_dhcp.[].range.end  |    string    |                The IP range end for the DHCP pool.                |
|     opnsense_dhcp.[].dns     |    string    |                  The DNS server served by DHCP.                   |

Dependencies
------------

N/A.

Example Playbook
----------------

```yaml
- name: Configure the DHCP server
  hosts: opnsense

  roles:
    - role: mirceanton.opnsense_dhcp
      vars:
        opnsense_dhcp:
          - iface: lan
            enabled: true
            range:
              start: "192.168.69.100"
              end: "192.168.69.199"
            dns: "8.8.8.8"
          - iface: opt1
            enabled: false
```

License
-------

MIT

Author Information
------------------

A role developed by [Mircea-Pavel ANTON](https://www.mirceanton.com).
