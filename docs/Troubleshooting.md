# Troubleshooting & Fixes / 故障排除与修复建议

## 1. Collection Compatibility / 集合兼容性
**Issue:** `[WARNING]: Collection ansible.posix does not support Ansible version 2.14.18`
**Cause:** Older Ansible-core version in RHEL 9 repo relative to new collections.
**Fix:** These are usually warnings; ensure FQCN (Fully Qualified Collection Name) is used in tasks.
RHEL 9 仓库中的 Ansible 版本相对较旧。通常不影响使用，但必须在任务中使用 **FQCN** 格式。

<img width="1390" height="167" alt="image" src="https://github.com/user-attachments/assets/30a2669b-1fd1-4690-ad8d-3b46d670196f" />


## 2. Privilege Escalation (Sudo) / 权限提升问题
**Issue:** `FAILED! => {"msg": "Missing sudo password"}`
**Fix:** Configure passwordless sudo for the deployment user on the target node:
受控节点要求输入 Sudo 密码。需在受控节点执行：
```bash
echo "danny ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/danny
```
<img width="1082" height="357" alt="image" src="https://github.com/user-attachments/assets/485a5f37-b1ef-4461-ae89-10fb078aea52" />


## 3. Invalid Firewall Service / 防火墙服务无效
**Issue:** INVALID_SERVICE: 'firewalld-config' not among existing services
**Cause:** Service names differ in EL 10 / Rocky 10.
**Fix:** Removed firewalld-config from allowed_services in roles/security/vars/main.yml.
Rocky 10 中不存在 firewalld-config 服务名。已从变量中移除，仅保留 ssh。

<img width="1177" height="197" alt="image" src="https://github.com/user-attachments/assets/131f3b8e-f13d-4768-8ec0-25e751eb156a" />


## 4. Callback Plugin Error / 回调插件错误
**Issue:** community.general.yaml has been removed.
**Fix:** Update ansible.cfg to use the built-in result formatter:
废弃了旧的回调插件。在 ansible.cfg 中改用内置格式：
```text
stdout_callback = ansible.builtin.default  
result_format = yaml
```
<img width="1207" height="112" alt="image" src="https://github.com/user-attachments/assets/240dd0e3-0c2f-4975-99b2-552e5b07fb6d" />

