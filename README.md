# Ansible Collection - tchecode.libvirt

[![wakatime](https://wakatime.com/badge/github/lucaslehnen/tchecode.libvirt.svg)](https://wakatime.com/badge/github/lucaslehnen/tchecode.libvirt)

It's an Ansible collection with roles to install libvirt and Qemu.

** For now, tested only by  amd64 hosts running Debian.

## Roles available

- `tchecode.libvirt.install`: Install libvirt and Qemu, configure a default pool and bridge network.
- `tchecode.k3s.reset`: Reset all changes made by this collection

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
    - tchecode.libvirt.install
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
