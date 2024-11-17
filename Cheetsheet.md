# **CKA Cheatsheet**

## **1. General Tips**

- **Tip 1**: _(Add your general Kubernetes exam tips here)_
- **Tip 2**:
- **Time Management**: _(E.g., Focus on solving high-weight questions first)_

---

## **2. Basic Commands**

### **Cluster Information**

```bash
# Check cluster info
kubectl cluster-info

# List nodes
kubectl get nodes
```


### Configuration

#### View and Edit Configurations
```bash
# View configurations
kubectl describe <resource> <name>

# Edit configurations
kubectl edit <resource> <name>

# Scaling
kubectl scale deployment <deployment-name> --replicas=3
```
### Namespaces

```bash
# List all namespaces
kubectl get namespaces

# Switch to a namespace
kubectl config set-context --current --namespace=<namespace>
```

## Pods

### Creating a Pod

```bash
# Basic pod creation
kubectl run <pod-name> --image=<image>
```

### Viewing Pod Logs

```bash
# Logs for a single pod
kubectl logs <pod-name>
```

### Pod YAML Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: my-container
      image: nginx
```

## ReplicaSets

### Create a ReplicaSet

```bash
kubectl apply -f replicaset-definition.yaml
```

### ReplicaSet YAML Example

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: example-replicaset
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: nginx
        image: nginx:1.21
        ports:
        - containerPort: 80
```

## Deployments

### Create a Deployment

```bash
kubectl create deployment <deployment-name> --image=<image>
```
### Update Deployment Image
```bash
kubectl set image deployment/<deployment-name> nginx=nginx:1.23
```
### Deployment YAML Example

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: example-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: nginx
        image: nginx:1.21
        ports:
        - containerPort: 80
```

## Services

### Expose a Pod

```bash
kubectl expose pod <pod-name> --type=ClusterIP --port=<port>
```
### List Services
```bash
kubectl get svc
```
### Service YAML Example (ClusterIP)
    
```yaml
apiVersion: v1
kind: Service
metadata:
  name: example-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
```

### Service YAML Example (NodePort)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: example-nodeport
spec:
  type: NodePort
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
    nodePort: 30007
```

### Service YAML Example (LoadBalancer)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: example-loadbalancer
spec:
  type: LoadBalancer
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
```

## Imperative Commands with kubectl
Use these commands for quick tasks or to generate YAML templates during the exam.
- Options to Remember:

1. `--dry-run=client`: Validates the command without creating the resource. 
2. `-o yaml`: Outputs the resource definition in YAML format for further modification.

### Pod
#### Generate YAML for an NGINX Pod:

```bash
kubectl run nginx --image=nginx --dry-run=client -o yaml
```

### Deployment
#### Generate YAML for a Deployment

```bash
kubectl create deployment nginx --image=nginx --dry-run=client -o yaml
```
####  Scale an Existing Deployment

```bash
kubectl scale deployment nginx --replicas=4
```

### Service
####    Expose Pod with ClusterIP Service
```bash
kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
```
####    Expose Pod with NodePort Service
```bash
kubectl expose pod nginx --type=NodePort --port=80 --name=nginx-service --dry-run=client -o yaml
# Update the nodePort value in the generated YAML
kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml
```
#### **Pro Tips:**

1. Use `kubectl expose` to generate selectors automatically from Pod labels.
2. Modify generated YAML files for custom settings (e.g., replicas, node ports).

## Troubleshooting

### Common Issues
- #### Pods not starting
  Possible Causes:
    1. Image pull errors (e.g., invalid image or no access).
    2. Misconfigured resource limits.
    3. Errors in the YAML manifest (syntax or invalid configuration).
    4. Pending state due to insufficient resources in the cluster.
  #### Commands to Debug:
```bash
  # Check Pod Status
  kubectl get pods
  
  # Describe the Pod for Detailed Information
  kubectl describe pod <pod-name>
  
  # Check Pod Logs
  kubectl logs <pod-name>
  kubectl logs <pod-name> -c <container-name> #For multi-container Pods:
  
  # Verify Node Status
  kubectl get nodes
  kubectl describe node <node-name>
  
  # Check Events
  kubectl get events --sort-by='.metadata.creationTimestamp'
  
  # Inspect YAML Definition
  kubectl apply -f pod.yaml --dry-run=client -o yaml

  # Check Resource Usage
    kubectl top pods
    kubectl top nodes
  ```
- #### Networking issues
  Possible Causes:
    1. Incorrect service configuration.
    2. Pod-to-Pod communication issues.
    3. Network policy restrictions.
    #### Commands to Debug:
```bash
  # Check Service Status
  kubectl get svc
  
  # Verify Pod IP Addresses
  kubectl get pods -o wide
  
  # Test Network Connectivity
  kubectl exec -it <pod-name> -- /bin/sh
  ping <pod-ip>
  curl <service-ip>:<port>
  
  # Check Network Policies
  kubectl get networkpolicies
  kubectl describe networkpolicy <policy-name>
  ```
  



## Flashcards Section

> Concept: Describe a Kubernetes concept briefly.<br>
> Command/Tip: Add a short related command or example.

## Useful Links

- Kubernetes Docs: https://kubernetes.io/docs
- Cheat Sheet: (Add any relevant link here)
