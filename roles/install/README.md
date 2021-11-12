Install role
-------------------------------------------------------------------

This role install libvirt and Qemu, configure a bridge network on your system and enable the default storage pool in `/var/lib/libvirt/images`.

Configure the variables
-----------------------

`bridge_network`: The name of the virtual network device that will be created.

```yaml
- hosts: all
  user: ubuntu
  become: true
  gather_facts: false
  roles:
    - tchecode.libvirt.install
  vars:
    - bridge_network: "br0"
```
