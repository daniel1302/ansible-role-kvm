# README

High level frameworks provides option to implement KVM infrastructure

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

    pools:
      - name: hostpool
        type: dir
        capacity: 100000000000
        path: /mapper/red01/kvmhostpool

      - name: hostpool1
        type: dir
        path: /mapper/red01/kvmhostpool
    
    vms:
      - name: jenkins
        vcpus: 1
        ram: 1024
        serial: true
        userdata: path_to_usedata.sh
        disks: 
          - base: path_to_base_disk.iso
            pool: some-pool
            size: 25
        cdroms:
          - path_to_iso.iso
        networks:
          - name: network_1
            ip: 255.200.100.0
            mac: 52:54:00:00:00:01
          - name: network_2
          - name: network_3
            mac: 52:54:00:00:00:02

  roles:
    - kvm
```

### Pools

- [Pools](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/sect-managing_guest_virtual_machines_with_virsh-storage_pool_commands)

```
pools:
  - name: Name of the dir pool
    type: dir
    capacity: Pool capacity in bytes
    path: Pool path

```

### Networks

Articles: 

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
