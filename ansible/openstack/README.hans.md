[English](README.md) | 简体中文

# 使用 Ansible Playbooks 构建和部署 OpenStack 服务器

课程提供的参考资料:
- [Openstack 云平台搭建 - wchhh2001 - CSDN](https://blog.csdn.net/qq_58860988/article/details/142051355)

## 先决条件

两个或更多服务器:
- 控制节点: 提供 OpenStack 服务
- 计算节点: 提供计算资源

在我的案例中，我使用了两台运行 Rocky Linux 9.4 的虚拟机。第一台服务器是控制节点，第二台服务器是计算节点。两台服务器都运行在 VMware Workstation 17 上。

另外，需要注意的是，Rocky Linux 9.4 没在提供课程参考资料中的 centos-release-openstack-train 包，我换成了最新的 zed release。
然而，zed release 国内似乎没有源，为了加速，我配置了 HTTP 代理至宿主机。


Controller 节点本人后续可能用于别的用途，给的配置稍微高一点。

| Name       | vCPUs | Memory | Disk  |
| ---------- | ----- | ------ | ----- |
| controller | 2 x 2 | 4 GB   | 50 GB |
| compute    | 2 x 1 | 2 GB   | 20 GB |

两个虚拟机通过 NAT 连接外部网络，使用 Host-Only 在 `192.168.98.x` 中直接通信。

| Name                | Network   | IP Address     | Subnet Mask | Gateway      |
| ------------------- | --------- | -------------- | ----------- | ------------ |
| controller (ens160) | NAT       | 192.168.52.133 | 24          | 192.168.52.2 |
| controller (ens192) | Host-Only | 192.168.98.128 | 24          | -            |
| compute (ens160)    | NAT       | 192.168.52.134 | 24          | 192.168.52.2 |
| compute (ens192)    | Host-Only | 192.168.98.129 | 24          | -            |

# 路线图

- [ ] 基础服务
    - [x] 安装配置基础服务
    - [ ] 将基础服务安装更改为 `check_mode: no`
- [ ] 安装配置 OpenStack 服务
    - [ ] Keystone
    - [ ] Glance
    - [ ] Placement
    - [ ] Nova
    - [ ] Neutron
    - [ ] Dashboard
    - [ ] Cinder
- [ ] 试运行
- [ ] 变量化
