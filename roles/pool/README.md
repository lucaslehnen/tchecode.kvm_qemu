Storage pools role
-------------------------------------------------------------------

This role configure a storage pool. 

Variables
-----------------------

- `kvm_qemu.pools.{dict}`: Storage pools to be created. 

    Two types supported:
    - dir

  ```yaml
  kvm_qemu:    
    pools:    
      - name: "vms"
        type: dir
        path: "/home/lucas/.libvirt/vms/"      
  ```

    - netfs   

  ```yaml
  kvm_qemu:
    pools:
      - name: "isos"
        type: "netfs"
        hostname: "192.168.99.1"
        path: isos(sda2) # remote shared path
        format: "cifs"      
        mount_path: "/home/lucas/.libvirt/isos/" # path to mount
        options:
          - "vers=1.0"
  ```

Example
-----------------------

```yaml
- hosts: all
  user: ubuntu
  become: true
  gather_facts: false
  roles:
    - tchecode.kvm_qemu.network
  pools:    
    - name: "vms"
      type: dir
      path: "/home/lucas/.libvirt/vms/"      
    - name: "isos"
      type: "netfs"
      hostname: "192.168.99.1"
      path: isos(sda2)
      format: "cifs"      
      mount_path: "/home/lucas/.libvirt/isos/"
      options:
        - "vers=1.0"
  
```

Docs:
 - https://libvirt.org/storage.html