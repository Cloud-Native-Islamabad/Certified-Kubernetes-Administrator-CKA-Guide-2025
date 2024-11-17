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

#### Scale an Existing Deployment

```bash
kubectl scale deployment nginx --replicas=4
```

### Service

#### Expose Pod with ClusterIP Service

```bash
kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
```

#### Expose Pod with NodePort Service

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

## Scheduling

Kubernetes offers powerful scheduling capabilities to control where and how Pods are placed within a cluster.

### Manual Scheduling

Add a Pod with `nodeName` specified to schedule it on a particular node.

To have direct control over Pod placement, which is useful for debugging, testing, or when specific workloads need to run on particular nodes due to hardware constraints.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: manual-scheduled-pod
spec:
  nodeName: worker-node-1
  containers:
    - name: my-container
      image: nginx
```

### Labels and Selectors

Labels are key/value pairs attached to Kubernetes objects. Selectors are used to filter resources based on labels.

Enables grouping of resources for efficient management, selection, and scheduling based on specific criteria.

```bash

# Add a label to a node
kubectl label nodes <node-name> <label-key>=<label-value>

# Get nodes with a specific label
kubectl get nodes --selector <label-key>=<label-value>
```

### Taints and Tolerations

Taints prevent Pods from being scheduled on certain nodes. Tolerations allow Pods to be scheduled on nodes with matching taints.

```bash
# Taint a node
kubectl taint nodes <node-name> <key>=<value>:<effect>
# Effects: NoSchedule, PreferNoSchedule, NoExecute

# Remove a taint from a node
kubectl taint nodes <node-name> <key>:<effect>-
```

Add tolerations to a Pod spec:

```yaml
spec:
  tolerations:
    - key: "key"
      operator: "Equal"
      value: "value"
      effect: "NoSchedule"
```

### Node Selectors

Use nodeSelector to schedule Pods onto nodes with matching labels.

```yaml
spec:
  nodeSelector:
    <label-key>: <label-value>
```

### Node Affinity

Advanced scheduling constraints using Node Affinity.

Offers more expressive options than nodeSelector, allowing for soft/hard requirements and combining multiple conditions.

**Use Case**: Define more expressive and flexible scheduling rules compared to node selectors.

**Why Needed**: Implement complex scheduling requirements, such as preferred node attributes or multiple label conditions.

#### Types of Node Affinity

- **RequiredDuringSchedulingIgnoredDuringExecution**: Hard requirements that must be met for scheduling.
- **PreferredDuringSchedulingIgnoredDuringExecution**: Soft preferences that the scheduler will try to satisfy but can ignore if necessary.

#### Operators

- **In**: Matches if the label value is in the specified list.
- **NotIn**: Matches if the label value is not in the specified list.
- **Exists**: Matches if the label key exists, regardless of its value.
- **DoesNotExist**: Matches if the label key does not exist.
- **Gt**: Greater than a specified value (numeric).
- **Lt**: Less than a specified value (numeric).

```yaml
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: <label-key>
                operator: In
                values:
                  - <label-value>
```

### Taints and Tolerations vs. Node Affinity

- Taints and Tolerations: Nodes repel Pods unless the Pods have matching tolerations.
- Node Affinity: Pods prefer or require nodes with specific labels.

### Resource Limits

Define resource requests and limits for containers to manage resource usage.

```yaml
resources:
  requests:
    cpu: "500m"
    memory: "256Mi"
  limits:
    cpu: "1"
    memory: "512Mi"
```

### A Quick Note on Editing Pods and Deployments

- Pods: Generally, Pods cannot be edited directly once created. To modify either:
  - Update the YAML file and recreate the Pod.
  - Edit the file, and then `replace --force` the file
- Deployments: Can be updated using kubectl edit deployment <deployment-name> or by applying changes to the YAML file.

### DaemonSets

Ensure a Pod runs on all (or selected) nodes in the cluster.

DaemonSet YAML Example:

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: example-daemonset
spec:
  selector:
    matchLabels:
      app: my-daemon
  template:
    metadata:
      labels:
        app: my-daemon
    spec:
      containers:
        - name: my-container
          image: my-image
```

### Static Pods

Pods managed directly by the kubelet, not by the API server.

- Create a Pod manifest file and place it in the kubelet's manifest directory (e.g., /etc/kubernetes/manifests).

### Multiple Schedulers

Run custom schedulers alongside the default scheduler.

Specify a custom scheduler in the Pod spec:

```yaml
spec:
  schedulerName: my-scheduler
```

- Deploy your custom scheduler as a Pod or static Pod.

### Configuring Scheduler Profiles

Define custom scheduling behaviors using scheduler profiles.

Scheduler Configuration Example:

```yaml
apiVersion: kubescheduler.config.k8s.io/v1
kind: KubeSchedulerConfiguration
profiles:
  - schedulerName: my-scheduler
    plugins:
      filter:
        enabled:
          - name: NodeResourcesFit
```
