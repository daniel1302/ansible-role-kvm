# README

High level frameworks provides option to implement KVM networking

## Example of usage: 

```
  vars:
    networks:
      - name: routed229
        type: routed
        source_dev: br0
        br_name: virbr229
        cidr: 192.168.229.0/24
        dhcp_cidr: 192.168.229.128/25
      - name: nat222
        type: nat
        br_name: nat222
        cidr: 192.168.222.0/24
        dhcp_cidr: 192.168.222.128/25
      - name: hostbr211
        type: bridge
        source_dev: br0


  roles:
    - kvm
```


### Networks

Network lists: 

- [Routed network](https://fabianlee.org/2019/06/05/kvm-creating-a-guest-vm-on-a-network-in-routed-mode/)
- [NAT network](https://fabianlee.org/2019/05/26/kvm-creating-a-guest-vm-on-a-nat-network/)



```
networks:
  - name: Network Name
    type: nat
    source_dev: Physical network, NAT is connected to
    br_name: Virtual bridge name
    cidr: Network CIDR
    dhcp_cidr: DHCP CIDR

  - name: Network Name
    type: routed
    source_dev: Physical network, used to route trafic
    br_name: Virtual bridge name
    cidr: Network CIDR
    dhcp_cidr: DHCP CIDR

  - name: Host Bridge name
    type: bridge
    source_dev: Physical network name
```