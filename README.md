# Certified Kubernetes Administrator (CKA) Exam Preparation Guide  
*Updated for the latest CKA Exam*

This guide focuses on the core objectives of the CKA exam. It includes recommended resources, tools, and hands-on labs to help you prepare effectively. Please verify that all resources match the exam's Kubernetes version.

---

### **Workloads and Scheduling – 15%**  
#### **Understand application deployments and how to perform rolling updates and rollbacks**  
- [Kubernetes Basics: Updating Applications](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/) (K8S Docs)  
- [Deployments in Kubernetes](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) (K8S Docs)  
- [Kubernetes Rollback Deployment](https://zeet.co/blog/kubernetes-rollback-deployment) (Vendor Guide)  
- [Update Strategies and Prometheus](https://devopswithkubernetes.com/part-4/1-update-strategies-and-prometheus) (GKE)  
- [Harness Deployment Strategies Overview](https://harness.io) (Vendor Guide)  
- [The Gotchas of Zero-Downtime Traffic with Kubernetes](https://www.weave.works/blog/kubernetes-zero-downtime-deployments) - Leigh Capili, Weaveworks  

#### **Use ConfigMaps and Secrets to configure applications**  
- [How to Deploy Hashicorp Vault in Kubernetes](https://devtron.ai) (Vendor Guide)  
- [Vault in Kubernetes: Beginner's Tutorial](https://devopscube.com/setup-vault-kubernetes/) (DevOpsCube)  
- [Reloader for Dynamic Config Updates](https://github.com/stakater/Reloader) (Open Source Tool by Stakater)  
- [Kubernetes ConfigMap Explained](https://www.qovery.com) (Qovery Blog)  

#### **Configure workload autoscaling**  
- [Kubernetes Autoscaling: Methods and Tips](https://www.datadoghq.com) (Vendor Guide)  
- [Cluster Autoscaler in Kubernetes](https://kubernetes.io/docs/tasks/administer-cluster/cluster-management/#cluster-autoscaler) (K8S Docs)  
- [Autoscaling LLM Workloads on GPUs in GKE](https://cloud.google.com) (GKE Guide)  
- [KEDA: Kubernetes Event-Driven Autoscaler](https://keda.sh/) (Open Source Tool)  

#### **Understand the primitives used to create robust, self-healing deployments**  
- Replicasets, Deployments, Statefulsets, Daemonsets  

#### **Configure Pod admission and scheduling**  
- [Custom Kube-Scheduler: Why and How](https://medium.com)  
- [GopherCon 2016: Building a Custom Kubernetes Scheduler](https://www.youtube.com)  
- [11 Kubernetes Custom Schedulers to Consider](https://blog.container-solutions.com)  

---

### **Storage – 10%**  
#### **Implement storage classes and dynamic volume provisioning**  
- [Kubernetes Storage Classes](https://kubernetes.io/docs/concepts/storage/storage-classes/) (K8S Docs)  
- [Dynamic Volume Provisioning Guide](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/) (K8S Docs)  

#### **Configure volume types, access modes, and reclaim policies**  
- [Volume Modes and Access Modes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes) (K8S Docs)  

#### **Manage persistent volumes and persistent volume claims**  
- [Persistent Volumes (PV) and Persistent Volume Claims (PVC)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) (K8S Docs)  

---

### **Services and Networking – 20%**  
#### **Understand connectivity between Pods**  
- [Pod Networking Basics](https://kubernetes.io/docs/concepts/cluster-administration/networking/) (K8S Docs)  

#### **Define and enforce Network Policies**  
- [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) (K8S Docs)  

#### **Use ClusterIP, NodePort, LoadBalancer service types, and endpoints**  
- [Services in Kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/) (K8S Docs)  

#### **Use the Gateway API to manage Ingress traffic**  
- [Gateway API Overview](https://gateway-api.sigs.k8s.io/) (Open Source)  

#### **Know how to use Ingress controllers and Ingress resources**  
- [Ingress Controllers](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/) (K8S Docs)  

#### **Understand and use CoreDNS**  
- [CoreDNS Documentation](https://coredns.io/)  

---

### **Cluster Architecture, Installation, and Configuration – 25%**  
#### **Manage role-based access control (RBAC)**  
- [RBAC Documentation](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)  

#### **Prepare underlying infrastructure for Kubernetes clusters**  
- [Cluster Setup Guide](https://kubernetes.io/docs/setup/)  

#### **Create and manage Kubernetes clusters using kubeadm**  
- [Kubeadm Documentation](https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm/)  

#### **Manage the lifecycle of Kubernetes clusters**  
- Upgrades, backups, and scaling  

#### **Implement and configure a highly-available control plane**  
- [Kubernetes HA Topology](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/)  

#### **Use Helm and Kustomize to install cluster components**  
- [Helm Documentation](https://helm.sh/)  
- [Kustomize Documentation](https://kustomize.io/)  

#### **Understand extension interfaces (CNI, CSI, CRI, etc.)**  
- Container Networking Interface (CNI)  
- Container Storage Interface (CSI)  

#### **Understand CRDs, install, and configure operators**  
- [Custom Resource Definitions (CRDs)](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)  

---

### **Troubleshooting – 30%**  
#### **Troubleshoot clusters and nodes**  
- [Cluster and Node Debugging Guide](https://kubernetes.io/docs/tasks/debug/)  

#### **Troubleshoot cluster components**  
- [Component Troubleshooting](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/)  

#### **Monitor cluster and application resource usage**  
- [Resource Monitoring in Kubernetes](https://kubernetes.io/docs/tasks/debug-application-cluster/resource-usage-monitoring/)  

#### **Manage and evaluate container output streams**  
- [Logging Architecture](https://kubernetes.io/docs/concepts/cluster-administration/logging/)  

#### **Troubleshoot services and networking**  
- [Networking Debugging](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-service/)  

---

## **Study Resources**  
- [Kubernetes Official Documentation](https://kubernetes.io/docs/)  
- [Killer.sh CKA Simulator](https://killer.sh)  
- [Mumshad CKA Course](https://kodekloud.com/p/kubernetes-certification-course)  
- [NANA’s CKA Playlist](https://www.youtube.com)  

---

Let me know if you'd like help refining further, or to add additional resources!
