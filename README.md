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

![Topology Example](<img width="354" height="395" alt="gns3-ansible-vrf-lite-lab" src="https://github.com/user-attachments/assets/15352f76-f2ae-4358-9699-a916306a6997" />)

## Ansible Playbook
See `static_vrf.yaml` for the complete automated configuration.

## Verification
- `show ip vrf` lists VRFs and interfaces
- `show ip route vrf RED` shows separate routing table
- Ping succeeds in same VRF, fails cross-VRF

![show vrf output](<img width="628" height="171" alt="show_ip_vrf" src="https://github.com/user-attachments/assets/6d7ebb0b-bc30-4b2f-a25a-6a0b7c809877" />  
![show ip route vrf RED](<img width="724" height="405" alt="show_ip_route_vrf_RED" src="https://github.com/user-attachments/assets/67a974d9-9623-4e06-9bc5-970c40387a24" />)  
![Ping success in same VRF and failure if different VRF](<img width="629" height="203" alt="pings" src="https://github.com/user-attachments/assets/be4d3059-e6b7-41dc-9d94-4a0d5b7d806c" />)  

## Lessons Learned
- Use classic `ip vrf` + `ip vrf forwarding` on older IOS for active RIBs.
- Validate with `--check --diff` before running.
- Static routes are reliable for VRF-Lite on legacy platforms.

Fork and extend — add more tenants or integrate with Python/Nornir!

#NetworkAutomation #Ansible #GNS3 #Cisco #VRFLite #DevNet
