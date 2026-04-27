# Kubernetes Complete Learning Roadmap

## 1. Prerequisites
- Containers & Images
  - Docker basics
  - Images, containers, volumes, networks
- Linux Fundamentals
  - Processes, namespaces, cgroups
- Networking Basics
  - IP, DNS, ports, load balancing
- YAML Syntax

---

## 2. Kubernetes Fundamentals
- What is Kubernetes & why it exists
- Cluster Architecture
  - Control Plane
  - Worker Nodes
- Kubernetes Objects
- Declarative vs Imperative Approach
- Kubernetes API
- kubectl CLI

---

## 3. Core Objects
- Pods
- ReplicaSets
- Deployments
- StatefulSets
- DaemonSets
- Jobs
- CronJobs

### Key Concepts
- Pod Lifecycle
- Scaling & Self-Healing
- Rolling Updates & Rollbacks

---

## 4. Networking
- Cluster Networking Model
- Services
  - ClusterIP
  - NodePort
  - LoadBalancer
- DNS in Kubernetes
- Ingress
- Ingress Controllers
- Network Policies

---

## 5. Storage
- Volumes
- Persistent Volumes (PV)
- Persistent Volume Claims (PVC)
- Storage Classes
- Dynamic Provisioning

---

## 6. Configuration & Secrets
- ConfigMaps
- Secrets
- Environment Variables
- Mounting Configurations into Pods

---

## 7. Security
- Authentication
- Authorization
- RBAC (Role-Based Access Control)
- Service Accounts
- Pod Security Standards
- Network Security

---

## 8. Workloads & Scheduling
- Kubernetes Scheduler
- Node Selectors
- Taints & Tolerations
- Affinity & Anti-Affinity
- Resource Requests & Limits

---

## 9. Observability & Monitoring
- Logs
- Events
- Metrics
- Health Checks
  - Liveness Probes
  - Readiness Probes

### Tools
- Prometheus
- Grafana

---

## 10. Scaling & Performance
- Horizontal Pod Autoscaler (HPA)
- Vertical Pod Autoscaler (VPA)
- Cluster Autoscaler
- Resource Optimization

---

## 11. Advanced Workloads
- Stateful Applications
- Multi-container Pods
- Sidecar Pattern
- Init Containers

---

## 12. CI/CD with Kubernetes
- Rolling Deployments
- Blue-Green Deployments
- Canary Releases

### Tools
- Jenkins
- GitHub Actions

---

## 13. Package Management
- Helm
- Helm Charts
- Releases & Templating

---

## 14. Kubernetes in Cloud
- Amazon EKS
- Google Kubernetes Engine (GKE)
- Azure Kubernetes Service (AKS)

---

## 15. Cluster Management
- Cluster Installation (kubeadm, minikube, kind)
- Upgrades
- Backup & Restore
- High Availability (HA Clusters)

---

## 16. Troubleshooting
- Debugging Pods
- CrashLoopBackOff
- ImagePullBackOff
- Network Issues
- Resource Starvation

---

## 17. Advanced Concepts
- Custom Resource Definitions (CRDs)
- Operators
- API Extensions
- Service Mesh

### Tools
- Istio

---

## 18. Ecosystem & Real-World Tools
- Argo CD
- Terraform
- Flux
