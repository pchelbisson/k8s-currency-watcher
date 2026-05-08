# Currency Watcher in K8s

This is a comprehensive DevOps pet project designed to practice production-grade Kubernetes administration and application deployment. The goal is to move from bare-metal virtualization to a fully functional, monitored, and automated "Currency Watcher" dashboard.

## Infrastructure & Cluster Setup

Unlike managed cloud solutions, this project focuses on the **under-the-hood** mechanics of K8s. The cluster is built from scratch with the following configuration:

- **Virtualization:** 4 Virtual Machines running **Debian 13** on VirtualBox.
    
- **Networking:** Utilizes **Bridged Adapter** mode to ensure seamless connectivity between Windows (Host), WSL2, and the cluster nodes.
    
- **K8s Distribution:** **RKE2** (v1.35.4+rke2r1) for a secure, enterprise-ready control plane.
    
- **Node Topology:**
    
    - `infra-01`: Dedicated infrastructure node (DNS for `.test` zone and NFS v4 server).
        
    - `cp-01`: Control-plane (Master) with custom **Taints** applied to protect system processes.
        
    - `worker-01` & `worker-02`: Dedicated compute nodes for application workloads.
        

## Tech Stack

- **Orchestration:** Kubernetes (RKE2).
    
- **Storage:** Persistent Volumes via **NFS v4**.
    
- **Runtime:** Containerized with **Docker**.
    
- **Observability:** Promtail, Loki, and Grafana.
    
- **CI/CD:** GitHub Actions for automated deployment.
    
- **Management:** Lens IDE and kubectl via WSL2.
    

##  Project Roadmap

### Phase 1: Foundation (Completed) 

- Deployment of Debian VMs and network debugging.
    
- RKE2 Cluster initialization and Node "Ready" status verification.
    
- Setting up the `currency-watcher` namespace via GitOps.
    

### Phase 2: Compute & Network (In Progress) 

- Containerizing the Frontend (Nginx + HTML/JS charts).
    
- Deploying Pods and configuring **Services** and **Ingress** for access via `currency.k8s.test`.
    

### Phase 3: State & Secrets

- Connecting **Persistent Volumes** for database backends (Redis/PostgreSQL).
    
- Managing API keys and sensitive data using **K8s Secrets**.
    

### Phase 4: Day 2 Operations

- Implementing **Horizontal Pod Autoscaler (HPA)** for dynamic scaling.
    
- Full log aggregation and monitoring integration.
    

---

_This project is a part of my journey to mastering DevOps and Kubernetes infrastructure._