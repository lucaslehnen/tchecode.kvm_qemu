# Ansible Collection - tchecode.kvm_qemu

[![wakatime](https://wakatime.com/badge/github/lucaslehnen/tchecode.kvm_qemu.svg)](https://wakatime.com/badge/github/lucaslehnen/tchecode.kvm_qemu)

It's an Ansible collection with roles to install libvirt and Qemu.

** For now, tested only by  amd64 hosts running Debian.

## Roles available

- `tchecode.kvm_qemu.install`: Install libvirt and Qemu
- `tchecode.kvm_qemu.network`: Configure a virtual network
- `tchecode.kvm_qemu.pool`: Create a storage pool
- `tchecode.kvm_qemu.reset`: Reset all changes made by this collection

More info about these roles can be found in `roles/{role}` folder.

## How to use

Define your inventory in `hosts` file:
```
192.168.99.30
```

Create your playbook `site.yml`:

```YAML
- hosts: all
  user: ubuntu
  become: true
  gather_facts: false
  roles:
    - tchecode.kvm_qemu.install
```

Run the playbook:

```
ansible-playbook -i hosts site.yml
```

To revert all changes, you can call the role `reset`. I Suggest another playbook, `reset.yml` for example:

```YAML
- hosts: all
  user: user
  become: true
  roles:
    - {role: reset, tags: [reset]}  
```
