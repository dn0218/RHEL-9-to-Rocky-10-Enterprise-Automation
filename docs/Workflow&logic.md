# Workflow & Implementation Logic / 工作流与实现逻辑

## 🛠 Stage 1: Security & Infrastructure / 第一阶段：安全与基础设施

1.  **SSH Hardening**: Use Jinja2 templates to enforce `PermitRootLogin no` and `PasswordAuthentication no`.
    * **SSH 加固**: 使用 Jinja2 模板强制执行禁止 Root 登录和禁用密码认证。
      
2.  **Firewall Control**: Ensure `firewalld` is active and only essential services (SSH) are exposed.
    * **防火墙控制**: 确保 `firewalld` 运行并仅暴露核心服务。

<img width="1096" height="303" alt="Screenshot 2026-04-07 105156" src="https://github.com/user-attachments/assets/650e3b59-3657-44f6-a980-f0b8e2f2125e" />

## 🏗 Stage 2: Storage Orchestration / 第二阶段：存储编排

* **Aggregation**: Combines multiple raw disks (e.g., `/dev/sda`, `/dev/sdb`) into a single Volume Group (`vg_data`).
    * **聚合**: 将多个物理磁盘合并为卷组。
* **Dynamic LV**: Creates a Logical Volume (`lv_containers`) with auto-resize support.
    * **动态 LV**: 创建支持自动扩容的逻辑卷。
* **Persistence**: Formats with XFS and updates `/etc/fstab`.
    * **持久化**: 格式化为 XFS 并同步更新挂载表。

<img width="1288" height="822" alt="Screenshot 2026-04-07 123444" src="https://github.com/user-attachments/assets/950d52ed-ff65-4100-a0b8-99fb3d00ddc8" />

<img width="997" height="567" alt="Screenshot 2026-04-07 123530" src="https://github.com/user-attachments/assets/1c3e00d8-3153-4a66-9912-35172fa0d999" />

<img width="888" height="200" alt="Screenshot 2026-04-07 123635" src="https://github.com/user-attachments/assets/ef8c3422-9100-4b23-a624-e6b48fe68bff" />


## 📦 Stage 3: Declarative Containers / 第三阶段：声明式容器

* **Podman Quadlets**: Instead of traditional `docker-compose`, we use native systemd integration.
    * **Podman Quadlets**: 弃用传统的 compose，使用 systemd 原生集成。
* **Nginx Deployment**: Managed as a standard system service (`systemctl status nginx`).
    * **Nginx 部署**: 像标准系统服务一样管理容器。
      
<img width="1275" height="807" alt="Screenshot 2026-04-07 114623" src="https://github.com/user-attachments/assets/6171e9ab-b418-41ee-95e1-36010b8abdc7" />

<img width="1227" height="817" alt="Screenshot 2026-04-07 120008" src="https://github.com/user-attachments/assets/1bbae52c-32ba-4199-9783-a94fce12a88f" />

<img width="947" height="258" alt="image" src="https://github.com/user-attachments/assets/2bda7284-377e-4df3-8266-5101b2a812f8" />




  
