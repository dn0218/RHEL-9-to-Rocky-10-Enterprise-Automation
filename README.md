# RHEL 9 to Rocky 10 Enterprise Automation
> **Enterprise-grade Ansible Orchestration for Hybrid EL-Environments.**
> **面向混合 EL 环境的企业级 Ansible 自动化编排。**

[![Ansible](https://img.shields.io/badge/Ansible-2.14+-black?logo=ansible)](https://www.ansible.com/)
[![RHEL](https://img.shields.io/badge/Control_Node-RHEL_9-red?logo=redhat)](https://www.redhat.com/)
[![Rocky Linux](https://img.shields.io/badge/Managed_Node-Rocky_10-green?logo=rockylinux)](https://rockylinux.org/)

## 📌 Overview / 项目概述

This project demonstrates a production-ready automation workflow to provision and secure **Rocky Linux 10** nodes from a **RHEL 9** control host. It integrates security hardening, LVM storage orchestration, and modern container runtimes using Podman Quadlets.

本项目展示了从 **RHEL 9** 控制节点对 **Rocky Linux 10** 受控节点进行生产级自动化配置的完整流程。涵盖了安全加固、LVM 存储编排以及基于 Podman Quadlets 的现代容器运行时部署。

---

## 🚀 Key Features / 核心功能

* **Security Hardening (Role: security):** SSH dynamic templating (Jinja2) and Firewalld policy management.
    * **安全加固 (角色: security):** SSH 动态模板化配置与防火墙策略管理。
* **Storage Orchestration (Role: storage):** Automated LVM stack (PV/VG/LV) with XFS persistent mounting.
    * **存储编排 (角色: storage):** 自动化 LVM 堆栈管理与 XFS 持久化挂载。
* **Container Runtime (Role: container_runtime):** Declarative Podman deployment via Systemd Quadlets.
    * **容器运行时 (角色: container_runtime):** 通过 Systemd Quadlets 进行声明式 Podman 部署。

---

## 📂 Project Structure / 项目结构

```bash
.
├── inventory/
│   └── hosts.ini          # Managed node definitions / 受控节点定义
├── group_vars/            # Global variables / 全局变量
├── roles/
│   ├── security/          # SSH & Firewall / SSH 与防火墙
│   ├── storage/           # LVM & Filesystem / LVM 与文件系统
│   └── container_runtime/ # Podman & Quadlet / 容器管理
├── site.yml               # Main Playbook / 主剧本
└── ansible.cfg           # Optimization settings / 优化配置
```

## 🛠 Usage / 使用指南
1. Prerequisites / 前提条件
- Control Node: RHEL 9 / 控制节点：RHEL 9

- Target Node: Rocky Linux 10 / 目标节点：Rocky Linux 10

- SSH key-based authentication / 已配置 SSH 密钥对认证

2. Execution / 执行部署
```bash
# Clone the repository / 克隆仓库

git clone [https://github.com/dn0218/RHEL-9-to-Rocky-10-Enterprise-Automation.git](https://github.com/dn0218/RHEL-9-to-Rocky-10-Enterprise-Automation.git)
cd RHEL-9-to-Rocky-10-Enterprise-Automation

# Run the playbook / 运行剧本
ansible-playbook site.yml
```
