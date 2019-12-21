# README

High level frameworks provides option to implement KVM networking

## Example of usage: 

```
  vars:
    networks:
      - name: routed225
        type: nat
        source_dev: br0
        br_name: vibr225
        cidr: 192.168.225.0/24
        dhcp_cidr: 192.168.225.128/25
      - name: routed226
        type: nat
        source_dev: br0
        br_name: vibr226
        cidr: 192.168.226.0/24
        dhcp_cidr: 192.168.226.128/25
      - name: routed227
        type: nat
        source_dev: br0
        br_name: vibr227
        cidr: 192.168.227.0/24
        dhcp_cidr: 192.168.227.128/25


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
    source_dev: Phsical network, NAT is connected to
    br_name: Virtual bridge name
    cidr: Network CIDR
    dhcp_cidr: DHCP CIDR

  - name: Network Name
    type: routed
    source_dev: Phsical network, NAT is connected to
    br_name: Virtual bridge name
    cidr: Network CIDR
    dhcp_cidr: DHCP CIDR
```