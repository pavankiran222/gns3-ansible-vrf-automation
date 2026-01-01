# GNS3 + Ansible VRF-Lite Lab: Automated Multi-Tenant Network

**Date:** December 31, 2025  
**Author:** Pavan Kiran Gummadi/[LinkedIn]([url](https://www.linkedin.com/in/pavan-kiran-g-135697310/))  
**Platform:** GNS3 with Cisco c7200 (IOS 15.3) routers and Network Automation Appliance  

## Project Overview
This project automates the configuration of **VRF-Lite** on two Cisco routers to create **three isolated tenant networks** (RED, GREEN, BLUE) over a **single trunk link** using 802.1Q subinterfaces.

Key features:
- Classic `ip vrf` syntax for full compatibility with IOS 15.x
- Separate subinterfaces and loopbacks per VRF
- Static routes for reachability between routers
- Full isolation: Connectivity only within the same VRF
- Fully automated with Ansible playbook

The lab demonstrates real-world multi-tenancy while handling older IOS limitations.

## Topology
- 2 x Cisco c7200 routers (R1, R2)
- Management Switch (for Ansible appliance)
- Trunk Switch (Ethernet switch between R1/R2 GigabitEthernet4/0)

 <img width="354" height="395" alt="gns3-ansible-vrf-lite-lab" src="https://github.com/user-attachments/assets/5ac07019-1671-4514-9707-b3a1e36f887e" />

 

## Ansible Playbook

See `static_vrf.yaml` for the complete automated configuration.

## Verification
- `show ip vrf` lists VRFs and interfaces
- `show ip route vrf RED` shows separate routing table
- `ping vrf RED 1.1.1.1` & `ping vrf RED 2.2.2.2` Ping succeeds in same VRF, fails cross-VRF (Isolation)

[show vrf output]  

<img width="628" height="171" alt="show_ip_vrf" src="https://github.com/user-attachments/assets/19763f60-00a2-46bd-8ee3-54fbda506054" />

[show ip route vrf RED]

<img width="724" height="405" alt="show_ip_route_vrf_RED" src="https://github.com/user-attachments/assets/086c1388-596b-4c08-a264-245bdf396fbf" />

[Ping success in same VRF and failure if different VRF]  

<img width="629" height="203" alt="pings" src="https://github.com/user-attachments/assets/b36052f3-75eb-43e2-9760-42ed9c82b6a5" />
