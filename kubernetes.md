# Kubernetes

Kubernetes (K8s) is an open-source platform that automates the deployment, scaling, and management of containerized applications. Originally developed by [Google](https://google.com), it functions as a container orchestrator, managing groups of containers (pods) across clusters of machines to ensure high availability, self-healing, and efficient resource utilization.

It does reconsiliation of the cluster state to ensure that the cluster is in the desired state.

### Key Features and Capabilities

- **Automation**: Automates container deployment and replication.
- **Self-Healing**: Automatically restarts failed containers, replaces them, and reschedules them when nodes die.
- **Scaling**: Scales applications up or down automatically based on demand.
- **Load Balancing**: Distributes network traffic to maintain stable performance.
- **Storage Orchestration**: Mounts storage systems (local, public cloud) automatically.

### Core Components

1. **Cluster**: A set of machines (nodes) that run containerized applications.
2. **Control Plane**: The "brain" of Kubernetes that makes global decisions about the cluster.
3. **Nodes**: Machines (virtual or physical) that run the application containers.
4. **Pods**: The smallest deployable units, containing one or more containers.

### Cloud Providers

- **Google Kubernetes Engine (GKE)**: Google's managed Kubernetes service.
- **Amazon Elastic Kubernetes Service (EKS)**: Amazon's managed Kubernetes service.
- **Azure Kubernetes Service (AKS)**: Microsoft's managed Kubernetes service.
- **DigitalOcean Kubernetes (DOKS)**: DigitalOcean's managed Kubernetes service.

Note: `kubectl` is a client tool to interact with the cluster.

### Commands

`kubectl cluster-info` Check cluster info

`kubectl get nodes` Check nodes

`kubectl version` Check kubectl version

`kubectl get ns` Check namespaces

`kubectl create ns <namespace>` Create namespace

`kubectl delete ns <namespace>` Delete namespace

`kubectl api-resources` Check api resources

`kubectl api-versions` Check api versions

`alias k=kubectl` Create alias for kubectl

---

`kubectl run <pod-name> --image=<image-name> --restart=Never -n <namespace>` Create pod

e.g `kubectl run nginx --image=nginx:alpine --restart=Never -n nginx`

---

`kubectl get pods -n <namespace>` Check pods

e.g `kubectl get pods -n nginx`

---

`kubectl logs <pod-name> -n <namespace>` Check logs

e.g `kubectl logs nginx -n nginx`

---

`kubectl describe pod <pod-name> -n <namespace>` Describe pod

e.g `kubectl describe pod nginx -n nginx`

---

### Namespaces

1. Scope = Payment, Shipment, Add to Cart, Control Plan
2. Policy Attachement
3. Resource Accounting
