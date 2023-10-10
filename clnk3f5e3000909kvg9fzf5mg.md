---
title: "Kubernetes Architecture"
datePublished: Tue Oct 10 2023 09:01:48 GMT+0000 (Coordinated Universal Time)
cuid: clnk3f5e3000909kvg9fzf5mg
slug: kubernetes-architecture
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696841665568/bccd01f4-cd2c-4079-8048-eda113716b02.png
tags: kubernetes, kubernetes-architecture, 90daysofdevops, trainwithshubham

---

**Introduction**

Welcome back to the "90 Days of DevOps" challenge! I

In this blog post, we are diving into the fascinating world of Kubernetes🛳️, the container-centric management software that has revolutionized the way we deploy and manage containerized applications.

Let's get started by exploring the fundamental concepts of Kubernetes.🤿

### What is Kubernetes(K8s)?

Kubernetes, often abbreviated as K8s, is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications and load balancing. It schedules, runs and manages isolated containers which are running on Virtual, physical and Cloud machines. It was originally developed by Google and is now maintained by the Cloud Native Computing Foundation (CNCF). Kubernetes provides a powerful toolset for managing containerized workloads and services dynamically and efficiently.

**Here's why it's called K8s:**

1. **Shortening Kubernetes:** The name "Kubernetes" is quite long and can be challenging to type and pronounce regularly. To simplify it, the creators and community members of Kubernetes adopted the abbreviation "K8s." The "K8" represents the eight letters between "K" and "s" in the full name "Kubernetes."
    
2. **Typing Efficiency:** When working in a command-line interface or while coding, a shorter abbreviation like "K8s" is easier and quicker to type than the full "Kubernetes," which can help improve productivity.
    
3. **Community Tradition:** The use of numerals within abbreviations as a shorthand is a convention within the tech industry. For example, "I18n" is a common abbreviation for "internationalization," where "18" represents the 18 letters between "I" and "n."
    

In essence, "K8s" is a convenient and widely accepted shorthand for Kubernetes, making it more accessible and user-friendly in various technical discussions and contexts.

### **What are the benefits of using k8s?**

Using Kubernetes (K8s) offers several significant benefits for managing containerized applications in a scalable and efficient manner:

1. **Container Orchestration:** Kubernetes simplifies the deployment and management of containers, automating tasks like scaling, load balancing, and self-healing. It ensures that your applications run consistently across various environments.
    
2. **Scalability:** Kubernetes allows you to effortlessly scale your applications up or down based on demand. It can automatically distribute incoming traffic across multiple instances of your application, ensuring optimal resource utilization.
    
3. **High Availability:** K8s provides tools for ensuring high availability. It can automatically reschedule containers in case of failures, ensuring that your applications remain available and reliable.
    
4. **Self-healing:** Kubernetes continually monitors the health of your applications and can restart or replace containers that are failing or unresponsive, reducing downtime and manual intervention.
    
5. **Resource Efficiency:** It optimizes resource usage, packing containers efficiently onto nodes. This means you can run more workloads on fewer servers, reducing infrastructure costs.
    
6. **Rolling Updates:** Kubernetes allows you to perform rolling updates with zero downtime. You can update your application without affecting users by gradually replacing old containers with new ones.
    
7. **Portability:** Kubernetes abstracts away the underlying infrastructure, making applications more portable. You can run the same application on various cloud providers or on-premises data centers without modification.
    
8. **Extensible:** K8s is highly extensible, with a vast ecosystem of plugins and extensions. You can customize it to suit your specific needs and integrate with other tools and services.
    
9. **Declarative Configuration:** You define your application's desired state using YAML or JSON files, and Kubernetes ensures that the actual state matches the desired state. This declarative approach simplifies configuration management.
    
10. **Community and Ecosystem:** Kubernetes has a vibrant and active community, which means regular updates, improvements, and a wealth of documentation and resources. It also has a vast ecosystem of tools and solutions built around it.
    
11. **Security:** Kubernetes offers security features like role-based access control (RBAC), secrets management, and network policies to help secure your containerized applications.
    
12. **Cost-Effective:** By efficiently utilizing resources and automating management tasks, Kubernetes can help reduce operational costs associated with running containerized applications.
    

## **Kubernetes Architecture: An In-Depth Exploration**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692698803035/c452b95f-478b-4f6f-83d7-ded14bfe9ed7.png?auto=compress,format&format=webp align="left")

Kubernetes architecture is a crucial aspect of understanding how the Kubernetes container orchestration platform works. It consists of several components and layers that work together to manage containerized applications. Let's explore the Kubernetes architecture in-depth:

* **Control Plane (Master Node)**:
    
    * The **Control Plane**, also known as the **Master Node**, is the brain of the Kubernetes cluster. It manages and controls the overall cluster state.
        
    * Key components of the Control Plane include:
        
        * **API Server**: The API server acts as the front-end interface for the control plane. It exposes the K8s API, which allows users, admins and other components to interact with the K8s clusters. Various operations, such as creating or managing pods, services, deployments, namespaces, and other K8s objects, are carried out through the API server. It is an entry point for all administrative tasks.
            
        * **Etcd**: It serves as a distributed key-value store, responsible for storing and managing the configuration data and state of the k8s cluster. Etcd is a separate database used to ensure high availability, consistency, and reliability of cluster-wide information.
            
        * **Controller Manager**: It runs as a set of independent processes on the master node(s) of the K8s cluster. Each controller runs as a separate goroutine, making it scalable and efficient. Managing these controllers, the kube CM continuously monitors the state of the cluster, makes necessary adjustments to ensure the desired state is achieved and helps maintain the system's overall health and stability.
            
            Some controllers -&gt; ReplicaSet, Deployment, Namespace, DaemonSet, Job, Cronjob, StatefulSet.
            
        * **Scheduler**: It is a "single point of truth" for pod scheduling decisions onto available nodes within the cluster based on various factors and policies which contributes to the efficient utilization of cluster resources and the reliable performance of applications running on K8s. The Scheduler decides which Node in the cluster should run a new Pod based on factors like resource requirements, node capacity, and constraints.
            
* **Node (Worker Node)**:
    
    * Nodes, also known as **Worker Nodes**, are the machines where containers (Pods) run. Each Node runs a container runtime like Docker or containerd.
        
    * Key components of a Node include:
        
        * **Kubelet**: Kubelet is an agent running on each node and is responsible for interacting with the K8s master to manage the containers and pods scheduled on that node. It ensures that the containers specified in the pods are running and healthy.
            
        * **Kube-Proxy**: it is responsible for managing network communications between services and pods within the cluster. It maintains network rules and forwards traffic to the appropriate destinations.
            
        * **Container Runtime**: It is responsible for pulling container images from a container registry and running the containers based on the specifications defined in the pod.
            

1. **Pod:**
    
    * The smallest deployable unit in Kubernetes. It represents one or more containers that share the same network namespace, storage, and IP address. Containers within a pod can communicate with each other using [**localhost**](http://localhost).
        
2. **ReplicaSet and Deployment:**
    
    * Higher-level abstractions that help manage the desired number of replicated pods. They ensure that a specified number of pod replicas are running at any given time, allowing for easy scaling and rolling updates.
        
3. **Service:**
    
    * An abstract way to expose an application running on a set of pods. Services allow pods to communicate with each other and external clients consistently, even as pods are added or removed.
        
4. **Namespace:**
    
    * A logical way to divide a cluster into multiple virtual clusters. Namespaces provide isolation, scope, and control over resources and objects within the cluster.
        
5. **ConfigMap and Secret:**
    
    * ConfigMaps hold configuration data in key-value pairs, which can be injected into pods as environment variables or volume mounts. Secrets are used to store sensitive information, such as passwords or API keys.
        
6. **Ingress:**
    
    * Manages external access to services within the cluster, typically HTTP. It provides features like SSL termination, load balancing, and URL-based routing.
        
7. **Volume:**
    
    * Allows data to be shared between containers in a pod or persist data beyond the lifetime of a pod. Kubernetes supports various types of volumes, including local storage, network-attached storage, and cloud storage.
        
8. **Addon Modules:**
    
    * Additional components that enhance Kubernetes functionality. Examples include DNS for service discovery, the dashboard for web-based management, and monitoring solutions.
        

### **What is Control Plane?**

In Kubernetes, the "Control Plane" refers to the collection of components that together manage and control the state of the cluster. It is responsible for making decisions about the desired state of the cluster and then ensuring that the actual state of the cluster matches that desired state. The Control Plane components act as the brain of the Kubernetes cluster, overseeing its operation and responding to various requests and changes.

* Key components of the Control Plane include:
    
    * **API Server**: The API server acts as the front-end interface for the control plane. It exposes the K8s API, which allows users, admins and other components to interact with the K8s clusters. Various operations, such as creating or managing pods, services, deployments, namespaces, and other K8s objects, are carried out through the API server. It is an entry point for all administrative tasks.
        
    * **Etcd**: It serves as a distributed key-value store, responsible for storing and managing the configuration data and state of the k8s cluster. Etcd is a separate database used to ensure high availability, consistency, and reliability of cluster-wide information.
        
    * **Controller Manager**: It runs as a set of independent processes on the master node(s) of the K8s cluster. Each controller runs as a separate goroutine, making it scalable and efficient. Managing these controllers, the kube CM continuously monitors the state of the cluster, makes necessary adjustments to ensure the desired state is achieved and helps maintain the system's overall health and stability.
        
        Some controllers -&gt; ReplicaSet, Deployment, Namespace, DaemonSet, Job, Cronjob, StatefulSet.
        
    * **Scheduler**: It is a "single point of truth" for pod scheduling decisions onto available nodes within the cluster based on various factors and policies which contributes to the efficient utilization of cluster resources and the reliable performance of applications running on K8s. The Scheduler decides which Node in the cluster should run a new Pod based on factors like resource requirements, node capacity, and constraints.
        

### **What happens if the node goes down?**

So, the controller manager comes into play and it is going to submit for a new pod to be created and scheduled, and it's the responsibility of the scheduler to find a node to put that pod on.

### **Write the difference between kubectl and kubelets.**

* **kubectl (Kubernetes Control CLI):** kubectl is a command-line tool used by administrators and developers to interact with the Kubernetes cluster. It allows users to manage and control the cluster by issuing commands for deploying, scaling, inspecting, and troubleshooting applications and resources within the cluster. kubectl communicates with the Kubernetes API server to perform these actions.
    
* **kubelet (Kubernetes Node Agent):** kubelet is an agent that runs on each worker node in the Kubernetes cluster. Its primary responsibility is to ensure that containers (pods) are running on the node as expected. kubelet communicates with the Control Plane (API server) to receive pod specifications and then manages the containers on the node to match the desired state.
    

### **Explain the role of the API server.**

The API Server is the main entrance where everyone interacts with the cluster. It's like the dispatcher, taking requests, ensuring they're valid, and coordinating actions. It's the gatekeeper for security, allowing only authorized folks in. The API Server ensures the cluster's resources are managed properly, whether it's creating, updating, or checking on things.