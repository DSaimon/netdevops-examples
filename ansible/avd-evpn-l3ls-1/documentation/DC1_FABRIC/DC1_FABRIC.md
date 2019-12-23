# DC1_FABRIC

## Table of Contents

- [DC1_FABRIC](#dc1fabric )
  - [Fabric Switches and Management IP](#fabric-switches-and-management-ip)
  - [Fabric Topology](#fabric-topology)
  - [Fabric IP Allocation](#fabric-ip-allocation)
    - [Fabric Point-To-Point Links](#fabric-point-to-point-links)
    - [Point-To-Point Links Node Allocation](#point-to-point-links-node-allocation)
    - [Overlay Loopback Interfaces (BGP EVPN Peering)](#overlay-loopback-interfaces-bgp-evpn-peering)
    - [Loopback0 Interfaces Node Allocation](#loopback0-interfaces-node-allocation)
    - [VTEP Loopback VXLAN Tunnel Source Interfaces (Leafs Only)](#vtep-loopback-vxlan-tunnel-source-interfaces-leafs-only)
    - [VTEP Loopback Node allocation](#vtep-loopback-node-allocation)

## Fabric Switches and Management IP

| Node | Management IP | Platform |
| ---- | ------------- | -------- |
| DC1-SPINE1 | 192.168.2.101/24 | vEOS-LAB |
| DC1-SPINE2 | 192.168.2.102/24 | vEOS-LAB |
| DC1-BL1A | 192.168.2.110/24 | vEOS-LAB |
| DC1-BL1B | 192.168.2.111/24 | vEOS-LAB |
| DC1-LEAF1A | 192.168.2.105/24 | vEOS-LAB |
| DC1-LEAF2A | 192.168.2.106/24 | vEOS-LAB |
| DC1-LEAF2B | 192.168.2.107/24 | vEOS-LAB |
| DC1-SVC3A | 192.168.2.108/24 | vEOS-LAB |
| DC1-SVC3B | 192.168.2.109/24 | vEOS-LAB |
| DC1-L2LEAF4A | 192.168.2.112/24 | vEOS-LAB |
| DC1-L2LEAF5A | 192.168.2.113/24 | vEOS-LAB |
| DC1-L2LEAF5B | 192.168.2.114/24 | vEOS-LAB |
| DC1-L2LEAF6A | 192.168.2.115/24 | vEOS-LAB |
| DC1-L2LEAF6B | 192.168.2.116/24 | vEOS-LAB |

## Fabric Topology

| Type | Leaf Node | Leaf Interface | Leaf Port-Channel | Peer Node | Peer Interface | Peer Port-Channel |
| ---- | --------- | -------------- | ----------------- |---------- | -------------- | ----------------- |
| L3 Leaf | DC1-BL1A | Ethernet1 | N/A | DC1-SPINE1 | Ethernet6 | N/A |
| L3 Leaf | DC1-BL1A | Ethernet2 | N/A | DC1-SPINE2 | Ethernet6 | N/A |
| L3 Leaf | DC1-BL1B | Ethernet1 | N/A | DC1-SPINE1 | Ethernet7 | N/A |
| L3 Leaf | DC1-BL1B | Ethernet2 | N/A | DC1-SPINE2 | Ethernet7 | N/A |
| L3 Leaf | DC1-LEAF1A | Ethernet1 | N/A | DC1-SPINE1 | Ethernet1 | N/A |
| L3 Leaf | DC1-LEAF1A | Ethernet2 | N/A | DC1-SPINE2 | Ethernet1 | N/A |
| L3 Leaf | DC1-LEAF2A | Ethernet1 | N/A | DC1-SPINE1 | Ethernet2 | N/A |
| L3 Leaf | DC1-LEAF2A | Ethernet2 | N/A | DC1-SPINE2 | Ethernet2 | N/A |
| L3 Leaf | DC1-LEAF2B | Ethernet1 | N/A | DC1-SPINE1 | Ethernet3 | N/A |
| L3 Leaf | DC1-LEAF2B | Ethernet2 | N/A | DC1-SPINE2 | Ethernet3 | N/A |
| L3 Leaf | DC1-SVC3A | Ethernet1 | N/A | DC1-SPINE1 | Ethernet4 | N/A |
| L3 Leaf | DC1-SVC3A | Ethernet2 | N/A | DC1-SPINE2 | Ethernet4 | N/A |
| L3 Leaf | DC1-SVC3B | Ethernet1 | N/A | DC1-SPINE1 | Ethernet5 | N/A |
| L3 Leaf | DC1-SVC3B | Ethernet2 | N/A | DC1-SPINE2 | Ethernet5 | N/A |
| L2 Leaf | DC1-L2LEAF4A | Ethernet11 | Po11 | DC1-LEAF2A | Ethernet6 | Po6 |
| L2 Leaf | DC1-L2LEAF4A | Ethernet12 | Po11 | DC1-LEAF2B | Ethernet6 | Po6 |
| L2 Leaf | DC1-L2LEAF5A | Ethernet1 | Po1 | DC1-SVC3A | Ethernet5 | Po5 |
| L2 Leaf | DC1-L2LEAF5A | Ethernet2 | Po1 | DC1-SVC3B | Ethernet5 | Po5 |
| L2 Leaf | DC1-L2LEAF5B | Ethernet1 | Po1 | DC1-SVC3A | Ethernet6 | Po6 |
| L2 Leaf | DC1-L2LEAF5B | Ethernet2 | Po1 | DC1-SVC3B | Ethernet6 | Po6 |
| L2 Leaf | DC1-L2LEAF6A | Ethernet1 | Po1 | DC1-LEAF2A | Ethernet7 | Po7 |
| L2 Leaf | DC1-L2LEAF6A | Ethernet2 | Po1 | DC1-LEAF2B | Ethernet7 | Po7 |
| L2 Leaf | DC1-L2LEAF6B | Ethernet1 | Po1 | DC1-LEAF2A | Ethernet8 | Po8 |
| L2 Leaf | DC1-L2LEAF6B | Ethernet2 | Po1 | DC1-LEAF2B | Ethernet8 | Po8 |

## Fabric IP Allocation

### Fabric Point-To-Point Links

| P2P Summary | Available Addresses | Assigned addresses | Assigned Address % |
| ----------- | ------------------- | ------------------ | ------------------ |
| 172.31.255.0/24 | 256 | 28 | 10.94 % |

### Point-To-Point Links Node Allocation

| Leaf Node | Leaf Interface | Leaf IP Address | Spine Node | Spine Interface | Spine IP Address |
| --------- | -------------- | --------------- | ---------- | --------------- | ---------------- |
| DC1-BL1A | Ethernet1 | 172.31.255.21/31 | DC1-SPINE1 | Ethernet6 | 172.31.255.20/31 |
| DC1-BL1A | Ethernet2 | 172.31.255.23/31 | DC1-SPINE2 | Ethernet6 | 172.31.255.22/31 |
| DC1-BL1B | Ethernet1 | 172.31.255.25/31 | DC1-SPINE1 | Ethernet7 | 172.31.255.24/31 |
| DC1-BL1B | Ethernet2 | 172.31.255.27/31 | DC1-SPINE2 | Ethernet7 | 172.31.255.26/31 |
| DC1-LEAF1A | Ethernet1 | 172.31.255.1/31 | DC1-SPINE1 | Ethernet1 | 172.31.255.0/31 |
| DC1-LEAF1A | Ethernet2 | 172.31.255.3/31 | DC1-SPINE2 | Ethernet1 | 172.31.255.2/31 |
| DC1-LEAF2A | Ethernet1 | 172.31.255.5/31 | DC1-SPINE1 | Ethernet2 | 172.31.255.4/31 |
| DC1-LEAF2A | Ethernet2 | 172.31.255.7/31 | DC1-SPINE2 | Ethernet2 | 172.31.255.6/31 |
| DC1-LEAF2B | Ethernet1 | 172.31.255.9/31 | DC1-SPINE1 | Ethernet3 | 172.31.255.8/31 |
| DC1-LEAF2B | Ethernet2 | 172.31.255.11/31 | DC1-SPINE2 | Ethernet3 | 172.31.255.10/31 |
| DC1-SVC3A | Ethernet1 | 172.31.255.13/31 | DC1-SPINE1 | Ethernet4 | 172.31.255.12/31 |
| DC1-SVC3A | Ethernet2 | 172.31.255.15/31 | DC1-SPINE2 | Ethernet4 | 172.31.255.14/31 |
| DC1-SVC3B | Ethernet1 | 172.31.255.17/31 | DC1-SPINE1 | Ethernet5 | 172.31.255.16/31 |
| DC1-SVC3B | Ethernet2 | 172.31.255.19/31 | DC1-SPINE2 | Ethernet5 | 172.31.255.18/31 |

### Overlay Loopback Interfaces (BGP EVPN Peering)

| Overlay Loopback Summary | Available Addresses | Assigned addresses | Assigned Address % |
| ------------------------ | ------------------- | ------------------ | ------------------ |
| 192.168.255.0/24 | 256 | 9 | 3.52 % |

### Loopback0 Interfaces Node Allocation

| Node | Loopback0 |
| ---- | --------- |
| DC1-SPINE1 | 192.168.255.1/32 |
| DC1-SPINE2 | 192.168.255.2/32 |
| DC1-BL1A | 192.168.255.8/32 |
| DC1-BL1B | 192.168.255.9/32 |
| DC1-LEAF1A | 192.168.255.3/32 |
| DC1-LEAF2A | 192.168.255.4/32 |
| DC1-LEAF2B | 192.168.255.5/32 |
| DC1-SVC3A | 192.168.255.6/32 |
| DC1-SVC3B | 192.168.255.7/32 |

### VTEP Loopback VXLAN Tunnel Source Interfaces (Leafs Only)

| VTEP Loopback Summary | Available Addresses | Assigned addresses | Assigned Address % |
| --------------------- | ------------------- | ------------------ | ------------------ |
| 192.168.254.0/24 | 256 | 7 | 2.74 % |

### VTEP Loopback Node allocation

| Node | Loopback1 |
| ---- | --------- |
| DC1-BL1A | 192.168.254.8/32 |
| DC1-BL1B | 192.168.254.8/32 |
| DC1-LEAF1A | 192.168.254.3/32 |
| DC1-LEAF2A | 192.168.254.4/32 |
| DC1-LEAF2B | 192.168.254.4/32 |
| DC1-SVC3A | 192.168.254.6/32 |
| DC1-SVC3B | 192.168.254.6/32 |
