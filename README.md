# k3-automate 🚀
Declarative Proxmox VM configuring + k3s cluster bootstrap with:

- 🌊 MetalLB for load balancing  
- 🧅 Nginx instead of Traefik  
- 📦 Rook-Ceph for storage  
- 🤖 All powered by Ansible playbooks

## Repo layout 🗂️
- `group_vars/all/` – 🛠️ Cluster configuration. Variables used across all playbooks.
- `inventory/` – 🧬 Auto-generated inventory based on `configuration.yml` in `group_vars/all/`.
- `roles/` – ♻️ Reusable, self-contained Ansible roles.

## Deployment
```bash
# 1. Copy the template and edit the configs
cp group_vars/all/configuration.yml.template group_vars/all/configuration.yml

# 2. Generate inventory from your configurations
ansible-playbook 0100-generate_inventory.yml

# 3. Preconfigure Proxmox VMs
ansible-playbook 0200-preconfigure_vms.yml

# 4. Install k3s cluster
ansible-playbook 0300-install_k3.yml

# 5. Pull kubeconfig to local machine
ansible-playbook 0310-setup_local_env.yml
```
You now have a shiny k3s cluster running on Proxmox ✨—ready for apps, experiments, and occasional chaos.
