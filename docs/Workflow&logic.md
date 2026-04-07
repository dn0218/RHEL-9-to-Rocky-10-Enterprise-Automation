# Workflow & Implementation Logic / 工作流与实现逻辑

## 🛠 Stage 1: Security & Infrastructure / 第一阶段：安全与基础设施

1.  **SSH Hardening**: Use Jinja2 templates to enforce `PermitRootLogin no` and `PasswordAuthentication no`.
    * **SSH 加固**: 使用 Jinja2 模板强制执行禁止 Root 登录和禁用密码认证。
2.  **Firewall Control**: Ensure `firewalld` is active and only essential services (SSH) are exposed.
    * **防火墙控制**: 确保 `firewalld` 运行并仅暴露核心服务。



## 🏗 Stage 2: Storage Orchestration / 第二阶段：存储编排

* **Aggregation**: Combines multiple raw disks (e.g., `/dev/sda`, `/dev/sdb`) into a single Volume Group (`vg_data`).
    * **聚合**: 将多个物理磁盘合并为卷组。
* **Dynamic LV**: Creates a Logical Volume (`lv_containers`) with auto-resize support.
    * **动态 LV**: 创建支持自动扩容的逻辑卷。
* **Persistence**: Formats with XFS and updates `/etc/fstab`.
    * **持久化**: 格式化为 XFS 并同步更新挂载表。



## 📦 Stage 3: Declarative Containers / 第三阶段：声明式容器

* **Podman Quadlets**: Instead of traditional `docker-compose`, we use native systemd integration.
    * **Podman Quadlets**: 弃用传统的 compose，使用 systemd 原生集成。
* **Nginx Deployment**: Managed as a standard system service (`systemctl status nginx`).
    * **Nginx 部署**: 像标准系统服务一样管理容器。
