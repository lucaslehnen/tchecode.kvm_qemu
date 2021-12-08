Network role
-------------------------------------------------------------------

This role configure a virtual network. 

Variables
-----------------------

- `kvm_qemu.bridge_network` : Name for the bridge network adapter (Debian network bridge)
- `kvm_qemu.networks.{dict}`: Virtual Networks to be created. 

    Two types supported:

    - bridge

  ```yaml
  kvm_qemu:
    networks:
      - name: virbr0  
        mode: bridge
  ``` 

    - NAT

  ```yaml
  kvm_qemu:
    networks:
      - name: virbr1
        mode: nat
        address: "192.168.100.1"
        netmask: "255.255.255.0"
        dhcp:
          start: "192.168.100.128"
          end: "192.168.100.254"
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
  vars:
    kvm_qemu:    
      bridge_network: br0
      networks:
      
        - name: virbr0
          mode: bridge

        - name: virbr1
          mode: nat
          address: "192.168.100.1"
          netmask: "255.255.255.0"
          dhcp:
            start: "192.168.100.128"
            end: "192.168.100.254"
  
```
