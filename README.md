# 🏠 HomeCluster-Ansible

Welcome to **HomeCluster-Ansible**! 🚀 This repository contains Ansible playbooks to set up a local Raspberry Pi cluster as a lightweight Kubernetes (K3s) environment. The cluster consists of:

- 🌟 **1 Master Node**: The control plane for your Kubernetes cluster.
- ⚙️ **2 Worker Nodes**: Handling workloads and applications.

---

## 🌟 Features

- **Automated Setup**: Deploy K3s on a Raspberry Pi cluster with ease using Ansible.
- **GitOps with ArgoCD**: Manage your Kubernetes applications declaratively.
- **Persistent Storage with Longhorn**: Lightweight and reliable block storage for your workloads.
- **Scalable Design**: Easily add more nodes to your cluster.

---

## 🖥️ Cluster Topology

| Node Type   | Role          | Host         |
|-------------|---------------|--------------------|
| Master Node | Control Plane | `halo-0`    |
| Worker 1    | Application   | `halo-1`    |
| Worker 2    | Application   | `halo-2`    |

---

## 📦 Components

### 1️⃣ **K3s**
A lightweight Kubernetes distribution ideal for edge computing and resource-constrained devices like Raspberry Pis.
---

## 🚀 Getting Started

### Prerequisites
1. 🐧 Raspberry Pi OS or a compatible Linux distribution installed on all nodes.
2. 🔑 Passwordless SSH access from the control machine to all nodes.
3. 📦 Ansible installed on the control machine (`pip install ansible`).

---

## ⚡ Usage

### Step 1: Clone the Repository

### Step 2: Configure Inventory
Edit the `inventory/hosts.ini` file to define your cluster's nodes:

#### Example:
```yml
[master]
192.168.1.100 ansible_user=pi 

[workers]
192.168.1.101 ansible_user=pi
192.168.1.102 ansible_user=pi 

[k3s_cluster:children]
master
workers
```

### Step 3: Run the Playbook
Run the Ansible playbook to set up the cluster:
`ansible-playbook site.yml -i inventory/hosts.ini --ask-pass`


### Step 4: Verify the Cluster
SSH into the master node and check the cluster status:
`kubectl get nodes` 


---

## 🎯 Post-Setup

Once the playbook completes successfully:
- **ArgoCD** will be running in its own namespace (`argocd`). Access it via its web UI or CLI to manage your applications.
- **Longhorn** will be deployed in the `longhorn-system` namespace, ready to provide persistent storage for your workloads.

---

## ❤️ Contributing

Feel free to submit issues or pull requests to improve this project! Contributions are always welcome.

---

## 🎉 Enjoy Your Cluster!

With HomeCluster-Ansible, you're ready to explore Kubernetes on your Raspberry Pi setup! 🌐 Happy clustering! 🚀✨



