English | [简体中文](README.hans.md)

# Building and Deploying OpenStack Server with Ansible Playbooks

Reference materials provided in the course:
- [Openstack Cloud Platform Setup - wchhh2001 - CSDN](https://blog.csdn.net/qq_58860988/article/details/142051355)

## Prerequisites

Two or more servers:
- Controller node: Provides OpenStack services
- Compute node: Provides compute resources

In my case, I used two virtual machines running Rocky Linux 9.4. The first server is the controller node, and the
second server is the compute node. Both servers are running on VMware Workstation 17.

The controller node might be used for other purposes later, so its configuration is slightly higher.

| Name       | vCPUs | Memory | Disk  |
| ---------- | ----- | ------ | ----- |
| controller | 2 x 2 | 4 GB   | 50 GB |
| compute    | 2 x 1 | 2 GB   | 20 GB |

The two virtual machines connect to the external network via NAT and communicate directly with each other on
`192.168.98.x` using Host-Only networking.

| Name                | Network   | IP Address     | Subnet Mask | Gateway      |
| ------------------- | --------- | -------------- | ----------- | ------------ |
| controller (ens160) | NAT       | 192.168.52.133 | 24          | 192.168.52.2 |
| controller (ens192) | Host-Only | 192.168.98.128 | 24          | -            |
| compute (ens160)    | NAT       | 192.168.52.134 | 24          | 192.168.52.2 |
| compute (ens192)    | Host-Only | 192.168.98.129 | 24          | -            |
