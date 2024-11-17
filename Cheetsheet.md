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

### Namespaces

```bash
# List all namespaces
kubectl get namespaces

# Switch to a namespace
kubectl config set-context --current --namespace=<namespace>
```

## 3. Pods

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

## 4. Services

### Expose a Pod

```bash
kubectl expose pod <pod-name> --type=ClusterIP --port=<port>
```

## 5. Configuration

### View and Edit Configurations

```bash
# View configurations
kubectl describe <resource> <name>

# Edit configurations
kubectl edit <resource> <name>
```

## 6. Troubleshooting

### Common Issues

- Pods not starting: (Possible causes and commands to debug)
- Networking issues: (Commands to diagnose)

## 7. Flashcards Section

> Concept: Describe a Kubernetes concept briefly.<br>
> Command/Tip: Add a short related command or example.

## 9. Useful Links

- Kubernetes Docs: https://kubernetes.io/docs
- Cheat Sheet: (Add any relevant link here)
