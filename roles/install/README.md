Install role
-------------------------------------------------------------------

This role install libvirt and Qemu and default configurations.

No variables are needed

Example
-----------------------

```yaml
- hosts: all
  user: ubuntu
  become: true
  gather_facts: false
  roles:
    - tchecode.kvm_qemu.install

```
