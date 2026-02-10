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

`kubectl config view` Check config

`kubectl config view --raw` Check config raw

`kubectl config get-contexts` Check contexts

`kubectl config current-context` Check current context

`kubectl config use-context <context-name>` Use context

`kubectl get nodes` Check nodes

`kubectl version` Check kubectl version

`kubectl get ns` Check namespaces

`kubectl create ns <namespace>` Create namespace

`kubectl delete ns <namespace>` Deklete namespace

`kubectl api-resources` Check api resources

`kubectl api-versions` Check api versions

`alias k=kubectl` Create alias for kubectl

`kubectl get events -n <namespace>` Check events

`kubectl get pods -n <namespace>` Check pods

`kubectl get nodes` Check nodes

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

`kubectl port-forward pod/nginx 8000:80`

---

---

`kubectl get no` Check nodes <br>
`kubectl get nodes` check nodes <br>
`kubectl get node` check nodes <br>
`kubectl get node -o wide` check nodes <br>

---

`kubectl config current-context` Check current context

`kube explain Role` Check role

### Namespaces

1. Scope = Payment, Shipment, Add to Cart, Control Plan
2. Policy Attachement
3. Resource Accounting

### RBAC (Role-Based Access Control)

1. Role -> Scope = Namespace
2. ClusterRole -> Scope = Cluster
3. RoleBinding -> Scope = Namespace
4. ClusterRoleBinding -> Scope = Cluster

Blast Radius should be minimize. Create a yaml file (declarative style)

Create `role.yaml`

```yaml
kind: Role
apiVersioon: rbac.authorize.k8s.io/v1
metadata:
  name: fundtransfer-deployer
  namespace: fundtransfer
rules:
  - apiGroups: ["apps"]
    resources: ["deployement", "replicaset"]
    verbs: ["get", "list", "create", "update", "patch"]
  - apiGroupds: [""]
    resources: ["pods", "service"]
    verbs: ["get", "list"]
```

Create namspace for **_fundtransfer_** -
`kubectl create ns fundtransfer`

Then Run **_role.yaml_** file -
`kubectl apply -f role.yaml`

Check the role in the namespace -
`kubectl get role -n fundtransfer`

#### Assigning Role To:

- User
- Group
- Service Account - a specialized, non-human identity assigned to Pods, allowing applications running within them to securely authenticate with the Kubernetes API server

Create Service Acount - `kubectl create serviceaccount <service-account-name> -n <namespace>`

e.g `kubectl create serviceaccount deployer -n fundtransfer`

e.g `kubectl create serviceaccount deployer -n fundtransfer --dry-run=client`

e.g `kubectl create serviceaccount deployer -n fundtransfer --dry-run=client -o yaml`

`kubectl get serviceaccount -n <namespace>` Get service account

`kubectl get sa -n <namespace>` Get service account

---

`kubectl create rolebinding <role-binding-name> --role=<role-name> --serviceaccount=<namespace>:<service-account-name> -n <namespace>` -> Create RoleBnding

`kubectl explain RoleBinding` Explain RoleBinding

`kubectl explain roleBinding.subjects` Explain RoleBinding Subjects

`kubectl explain roleBinding.subjects.apiGroup` Explain RoleBinding Subjects apiGroup

`kubectl explain roleBinding.subjects.kind` Explain RoleBinding Subjects kind

`kubectl explain roleBinding.subjects.name` Explain RoleBinding Subjects name

`kubectl explain roleBinding.subjects.apiGroup` Explain RoleBinding Subjects apiGroup

`kubectl explain roleBinding.roleRef` Explain RoleBinding RoleRef

---

**roleBinding.yaml**

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: deployer-binding
  namespace: fundtransfer
subjects:
  - kind: ServiceAccount
    name: deployer
    namespace: fundtransfer
roleRef:
  kind: Role
  name: fundtransfer-deployer
  apiGroup: rbac.authorization.k8s.io
```

`kubectl auth can-i create deployment -n fundtransfer --as system:serviceaccount:fundtransfer:deployer` Check if deployer can create deployment in fundtransfer namespace

`kubectl auth can-i create deployments -n fundtransfer --as system:serviceaccount:fundtransfer:deployer`

---

---

`kubectl run --image=busybox --restart=Never --port=80`

`kubectl run --image=busybox -it --rm --restart=Never`

`kubectl run --image=busybox -it --rm --restart=Never -- env`

`kubectl run --image=busybox -it --rm --restart=Never -- /bin/sh -c "sleep 10 && echo 'hello'"`

`kubectl port-forward <pod-name> <local-port>:<pod-port>`

`kubectl run fastapi-dev2 --image=ameenalam/cloud-native-fastapi:dev --labels="app=backend,"stack=fastapi"`

`kubectl run fastapi-dev --image=ameenalam/cloud-native-fastapi:dev --labels="app=backend,"stack=fastapi" --dry-run=client -o yaml > fastapi-dev.yaml`

`kubectl get pods -l app=backend`

`kubectl get pods -l stack=fastapi`

`kubectl get pods -l app=backend,stack=fastapi`

---

---

Create Token `kubectl create -n <namespace> token <service-account-name>`

`kubectl config set-credentials <service-account-name> --token=<token>`

`kubectl config set-context <context-name> --user=<service-account-name> --namespace=<namespace> --cluster=<cluster-name>`

e.g `kubectl config set-context dev-context --user=deployer --namespace=fundtransfer --cluster=docker-desktop`

`kubectl config use-context <context-name> ` Use context
