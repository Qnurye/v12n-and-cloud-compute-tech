# Building and deploying an [OpenStack](https://www.openstack.org/) server using Ansible Playbooks

Reference provided in lesson
- [Openstack 云平台搭建 - wchhh2001 - CSDN](https://blog.csdn.net/qq_58860988/article/details/142051355)

## Prerequisites

Two or more servers:
- Controller node: provides the OpenStack services
- Compute node(s): provides the computing resources

In my case I used two virtual machines running on VMware Workstation 17. The first server is the
controller node and the second server is the compute node. Both servers are running Rocky Linux 9.4.

### Virtual Machine Configuration

If you are using similar virtual machines, you can refer to my configuration:

| Name | vCPUs | Memory | Disk |
|------|-------|--------|------|
| controller | 2 x 2 | 4 GB | 50 GB |
| compute | 2 x 1 | 2 GB | 20 GB |

| Name | Network | IP Address | Subnet Mask | Gateway |
|------|---------|------------|-------------|---------|
| controller | NAT | 192.168.11.100 | 24 | 192.168.11.1|
| controller | Host-Only | 192.168.255.100 | 24 | - |
| compute | NAT | 192.168.11.200 | 24 | 192.168.11.2|
| compute | Host-Only | 192.168.255.200 | 24 | - |
