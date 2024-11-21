[![License: CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/80x15.png)](https://creativecommons.org/licenses/by-sa/4.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
# Certified Kubernetes Administrator (CKA) Exam Preparation Guide  
*Updated for the latest CKA Exam*

This guide focuses on the core objectives of the CKA exam. It includes recommended resources, tools, and hands-on labs to help you prepare effectively. Please verify that all resources match the exam's Kubernetes version.

**Disclaimer:** This is not an exhaustive list, as the exam evolves with K8s rapid development. Please make a pull request if there something wrong, should be added, or updated.

---
## **Exam Overview**
The Certified Kubernetes Administrator (CKA) exam is a performance-based test that requires you to solve multiple tasks on a live Kubernetes cluster. The exam is proctored and lasts for 2 hours. You must score at least 74% to pass the exam.

### **Exam Curriculum**
These are the exam objectives you review and understand in order to pass the test.
* [CNCF Exam Curriculum repository ](https://github.com/cncf/curriculum)
- **Workloads and Scheduling – 15%**
- **Storage – 10%**
- **Services and Networking – 20%**
- **Cluster Architecture, Installation, and Configuration – 25%**
- **Security – 20%**
- **Troubleshooting – 30%**


### **Exam Prerequisites**
- **Kubernetes Fundamentals**  
  - [Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/) (K8S Docs)  
  - [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) (K8S Docs)  
  - [Kubernetes in 5 Minutes](https://www.youtube.com/watch?v=PH-2FfFD2PU) (Video)


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

## Tips and Best Practices

### Practice, Practice, Practice! 🏋️‍♂️
Familiarize yourself with the documentation, initially [concepts](https://kubernetes.io/docs/concepts/)  and mostly [tasks](https://kubernetes.io/docs/tasks/), **kubectl explain** command, [kubectl cheatsheet](https://kubernetes.io/docs/user-guide/kubectl-cheatsheet/), and [kubectl commands reference](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
- [Kubectl Cheat Sheet By Cloud Native Islamabad](https://github.com/Cloud-Native-Islamabad/Certified-Kubernetes-Administrator-CKA-Guide-2025/blob/main/Cheetsheet.md)
- [Kubectl Commands Reference](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
- [K8s Concepts](https://kubernetes.io/docs/concepts/)  


* When using kubectl for investigations and troubleshooting utilize the wide output it gives your more details
```
     $kubectl get pods -o wide  --show-labels  --all-namespaces
     or
     $kubectl get pods -o wide  --show-labels  -A     # -A is quicker than --all-namespaces
```

* For events and troubleshooting utilize kubectl describe if its pod/resource related and logs if it is application issue related
```
     $kubectl describe pods <PODID>   # for pod, deployment, other k8s resource issues/events
     $kubectl logs <PODID>            # for container/application issues like crash loops
     
```

* The '-o yaml' in conjuction with `--dry-run=client` allows you to create a manifest template from an imperative spec, combined with `--edit` it allows you to modify the object before creation
```
kubectl create service clusterip my-svc -o yaml --dry-run=client > /tmp/srv.yaml
kubectl create --edit -f /tmp/srv.yaml
```
* use kubectl [aliases](https://github.com/ahmetb/kubectl-aliases) to speed up and reduce typo errors, practice them in your daily work some examples:

```
alias k='kubectl'
alias kg='kubectl get'
alias kgpo='kubectl get pod'
alias kcpyd='kubectl create pod -o yaml --dry-run=client'
alias ksysgpo='kubectl --namespace=kube-system get pod'

alias kd='kubectl delete'
alias kdf='kubectl delete -f'
## for quick deletes you can add --force --grace-period=0  **Not sure if it is a good idea if you are in a production cluster**
alias krmgf='kubectl delete --grace-period 0 --force'
alias kgsvcoyaml='kubectl get service -o=yaml'
alias kgsvcwn='watch kubectl get service --namespace'
alias kgsvcslwn='watch kubectl get service --show-labels --namespace'

#example usage of aliases
krmgf nginx-8jk71    # kill pod nginx-8jk71 using grace period 0 and force

```

## Books:  
- [Acing the Certified Kubernetes Administrator Exam](https://www.manning.com/books/acing-the-certified-kubernetes-administrator-exam?utm_source=acingthecka&utm_medium=affiliate&utm_campaign=book_crowell_acing_6_8_22&a_aid=acingthecka&a_bid=5502c16b)
- [Kubernetes Up & Running](https://www.amazon.com/Kubernetes-Running-Dive-Future-Infrastructure/dp/1492046531)  
- [The Kubernetes Book](https://www.amazon.com/Kubernetes-Book-Nigel-Poulton/dp/1521823638)  
- [Kubernetes Best Practices](https://www.amazon.com/Kubernetes-Best-Practices-Blueprints-Applications/dp/1492056472)

## **Webinar & Streams**
- [Certified Kubernetes Administrator Hands-On Workshop - Part 01](https://www.youtube.com/watch?v=ubZdjmODdxg&t=1671s&ab_channel=CloudNativeIslamabad)
- [Certified Kubernetes Administrator Hands-On Workshop - Part 02](https://www.youtube.com/watch?v=6xpRClUlsJQ&t=519s&ab_channel=CloudNativeIslamabad)

## **Study Resources**  
- [Kubernetes Official Documentation](https://kubernetes.io/docs/)  
- [CKA Hands-on Lab Exercises By Chad M. Crowell](https://github.com/chadmcrowell/CKA-Exercises)
- [Killer.sh CKA Simulator](https://killer.sh)  
- [Mumshad CKA Course](https://learn.kodekloud.com/courses/cka-certification-course-certified-kubernetes-administrator)  
- [NANA’s CKA Playlist](https://www.youtube.com/c/techworldwithnana/playlists)  

