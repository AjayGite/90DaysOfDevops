---
title: "Working with Namespaces and Services in Kubernetes"
datePublished: Mon Oct 30 2023 12:23:13 GMT+0000 (Coordinated Universal Time)
cuid: clocvf73u000009migr214oh9
slug: working-with-namespaces-and-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698661573772/a058c63f-358e-4137-a984-dfd63ce98d20.png
tags: kubernetes, devops, 90daysofdevops, trainwithshubham, day33

---

### **What are Namespaces?**

* A namespace is a way to partition and isolate resources within a cluster. It provides a virtual cluster within a physical cluster, allowing multiple teams or applications to coexist without interfering with each other.
    
* Namespace-based scoping is applicable only for namespaced [**objects**](https://kubernetes.io/docs/concepts/overview/working-with-objects/#kubernetes-objects) *(e.g. Pods, Deployments, Services, etc.)* and not for cluster-wide objects *(e.g. StorageClass, Nodes, PersistentVolumes, etc.)*.
    
* By default, all objects are created in the “**default**” namespace, but administrators can create additional namespaces and apply resource quotas, network policies, and access controls to them.
    

# **Benefits of Having Namespace in Cluster**

1. **Resource Organization:** Namespaces provide a logical grouping mechanism to organize resources within a cluster.
    
2. **Resource Isolation:** Namespaces provide a way to isolate and segregate resources within a cluster. This isolation prevents resource conflicts and allows for better resource utilization and management.
    

3\. **Multi-tenancy:** Namespaces enable multi-tenancy within a Kubernetes cluster. Different teams or users can have their own dedicated namespaces, providing them with separate environments to deploy and manage their applications.

4\. **Access Control:** Namespaces provide a mechanism for access control and RBAC (Role-Based Access Control) within a cluster. By assigning appropriate roles and permissions at the namespace level, you can control who can create, view, or modify resources within a particular namespace.

1. **Resource Quotas:** Namespaces allow you to set resource quotas to limit the amount of CPU, memory, and storage that can be consumed within a namespace.
    

6\. **Namespace Scoping:** Some Kubernetes resources, such as services, secrets, and config maps, are scoped to a namespace. This means they are only accessible and visible within the same namespace where they are created.

### **Initial namespaces**

Kubernetes starts with four initial namespaces:

<dl><dt><code>default</code></dt><dd>Kubernetes includes this namespace so that you can start using your new cluster without first creating a namespace.</dd><dt><code>kube-node-lease</code></dt><dd>This namespace holds<span><span> </span></span><a href="https://kubernetes.io/docs/concepts/architecture/leases/">Lease</a><span><span> </span></span>objects associated with each node. Node leases allow the kubelet to send<span><span> </span></span><a href="https://kubernetes.io/docs/concepts/architecture/nodes/#heartbeats">heartbeats</a><span><span> </span></span>so that the control plane can detect node failure.</dd><dt><code>kube-public</code></dt><dd>This namespace is readable by<span><span> </span></span><em>all</em><span><span> </span></span>clients (including those not authenticated). This namespace is mostly reserved for cluster usage, in case that some resources should be visible and readable publicly throughout the whole cluster. The public aspect of this namespace is only a convention, not a requirement.</dd><dt><code>kube-system</code></dt><dd>The namespace for objects created by the Kubernetes system.</dd></dl>

### **Viewing namespaces**

You can list the current namespaces in a cluster using:

```bash
kubectl get namespace
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698667542478/9d76ca93-39e2-4f48-98a6-b4b44f274699.png align="center")

### **Creating a new namespace**

Create a new YAML file called `my-namespace.yaml` with the contents:

```bash
apiVersion: v1
kind: Namespace
metadata:
  name: <insert-namespace-name-here>
```

Then run:

```bash
kubectl create -f ./my-namespace.yaml
```

Alternatively, you can create namespace using below command:

```bash
kubectl create namespace <insert-namespace-name-here>
```

### **Deleting a namespace**

Delete a namespace with

```bash
kubectl delete namespaces <insert-some-namespace-name>
```

# **Services in k8s**

* **Services** in Kubernetes are a fundamental concept used to expose and access your Pods and Deployments over the network.
    
* A Service acts as an abstraction layer that defines a logical set of Pods and a policy by which to access them. It provides a stable IP address and DNS name for a set of Pods, allowing them to be accessed by other parts of the application or by external users.
    
* Services can be configured to provide load balancing, service discovery, and proxying to backends running on different ports or nodes within a cluster. They can also be used to provide access to external resources or to expose applications running inside the cluster to external users.
    
* Services are an essential component of Kubernetes networking and are widely used in microservices architectures.
    

# **Benefits of Having Services**

Services are used in Kubernetes for several reasons:

1.**Load balancing:** Services provide a single, stable IP address and DNS name for a set of Pods, distributing traffic among them and ensuring that requests are handled by healthy instances.

2.**Service discovery:** Services allow other parts of the application to discover and communicate with Pods, even if their IP addresses change due to scaling or failure.

3.**Port mapping:** Services enable backends running on different ports or nodes to be accessed through a single, well-known port or endpoint, simplifying configuration and management.

4.**External access:** Services can be used to expose applications running inside the cluster to external users or to provide access to external resources, such as databases or APIs.

## **Types of Services:**

Kubernetes supports various types of services, including:

* **ClusterIP:** Exposes the service on a cluster-internal IP, only accessible within the cluster.
    
* **NodePort:** Exposes the service on a static port on each node's IP, allowing external access to the service.
    
* **LoadBalancer:** Creates an external load balancer (if supported by the cloud provider) and assigns a unique external IP to access the service.
    
* **ExternalName:** Maps the service to a DNS name.
    

* **Creating Services:** You can create a service by defining a Service resource in a YAML or JSON manifest and applying it to the cluster using `kubectl apply`.
    

```bash
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

```bash
kubectl apply -f my-service.yaml
```

# **Task 1: Creating a Namespace for Your Deployment**

**Step 1:** Create a Namespace To create a Namespace for your Deployment, run the following command:

```bash
kubectl create namespace <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698668322378/a4887ff7-ce30-4a4a-8efc-6ce4769aeb77.png align="center")

**Step 2:** Update `deployment.yml` Edit your `deployment.yml` file to include the Namespace you created. Add or modify the `namespace` field under the `metadata` section. It should look like this:

```bash
 apiVersion: apps/v1
 kind: Deployment
 metadata:
   name: todo-app-deployment
   namespace: kubernetes-project-day33
 spec:
   replicas: 3
   selector:
     matchLabels:
       app: todo-app
   template:
     metadata:
       labels:
         app: todo-app
     spec:
       containers:
       - name: todo-app-deployment
         image: ajaygite7764/todo-app
         ports:
         - containerPort: 8000
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698668340192/ed8e7227-2778-4643-ac0e-86440fc8fbdb.png align="center")

**Step 3:** Apply the Updated Deployment Use the following command to apply the updated Deployment with the specified Namespace:

```bash
kubectl apply -f deployment.yml -n <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698668354479/0714dc8f-d31d-4754-97c9-36360ce66166.png align="center")

**Step 4:** Verify Namespace Creation To ensure that the Namespace has been created successfully, run the following command:

```bash
kubectl get namespaces
```

You should see your newly created Namespace in the list.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698668394115/696e13ba-0a4a-4af5-9471-943c13e3bcbc.png align="center")

**Step 5**: Verify that the Namespace has been created by checking the status of the Namespaces in your cluster

```bash
kubectl get pods -n <namespace-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698668420404/7ae44bfe-f31e-4501-8d3e-c73fae2f0c4e.png align="center")

# **Task 2:**

# **Cluster IP**

* ClusterIP is a type of Kubernetes Service that provides a stable IP address and DNS name for a set of Pods within a cluster. When a ClusterIP Service is created, Kubernetes assigns a virtual IP address to the Service, which can be used by other parts of the application to access the Pods.
    
* The ClusterIP is accessible only from within the cluster and is not exposed to the external network. It enables seamless communication between different services and pods within the cluster without the need for exposing them to the outside world.
    
* To use a ClusterIP Service, other parts of the application can simply use the Service’s DNS name, along with the assigned port number, to access the Pods. Kubernetes ensures that traffic sent to the Service’s IP address is distributed among the available Pods, based on the configured load-balancing algorithm.
    
* ClusterIP is commonly used for internal microservice-to-microservice communication and internal service discovery within the Kubernetes cluster.
    

# **NodePort**

* NodePort is a type of Kubernetes Service that exposes a specific port on each node in the cluster and routes traffic to a Service. When a NodePort Service is created, Kubernetes automatically assigns a random port in the range of 30000–32767 to the Service.
    
* NodePort is typically used to expose a Service externally, either to the Internet or to other services outside the cluster. For example, a web application Service could be exposed using a NodePort, allowing users to access the application using the IP address of any node in the cluster, along with the assigned port number.
    
* To use a NodePort Service, the client must connect to the IP address of a node in the cluster, along with the assigned port number. Kubernetes ensures that traffic sent to this port is routed to the appropriate Pod, based on the configured load-balancing algorithm.
    

# **Load Balancing**

* Load balancing in Kubernetes is the process of distributing network traffic across multiple Pods to ensure that requests are handled efficiently and reliably. It is achieved through the use of a Kubernetes Service, which provides a stable IP address and DNS name for a set of Pods.
    
* Load balancing in Kubernetes is essential for ensuring the high availability and scalability of applications, particularly in microservices architectures where many small, independently deployable services may be running on different nodes in the cluster.
    
* By distributing traffic across multiple instances, load balancing helps to prevent overload and ensures that requests are processed quickly and reliably. It also allows for seamless scaling of applications by adding or removing Pods without affecting the overall performance of the application.
    
* Kubernetes supports several load-balancing algorithms, including round-robin, least connections, and IP Hash, which can be configured to suit the specific needs of the application.
    

## **Networking:**

Networking in Kubernetes deals with how containers and Pods communicate both within the cluster and with external entities. Key networking concepts include:

1. **Pod Networking**: Containers within the same Pod share the same network namespace, allowing them to communicate over [`localhost`](http://localhost/). This simplifies intra-Pod communication.
    
2. **Service Networking**: Services abstract the network details of Pods. They provide a stable endpoint for accessing a set of Pods, enabling load balancing and service discovery.
    
3. **Ingress**: Ingress resources define rules for routing external HTTP(S) traffic to Services within the cluster. They act as a smart router, directing requests based on hostnames and paths.
    
4. **Network Policies**: These are used to control traffic flow to and from Pods. Network policies define rules for allowing or denying traffic based on labels, namespaces, and IP addresses, enhancing security.
    
5. **Container Network Interface (CNI)**: Kubernetes relies on CNI plugins to manage container networking. These plugins configure network interfaces in Pods, ensuring proper network isolation and communication.
    
6. **DNS**: Kubernetes has an integrated DNS service. It allows Pods to discover and communicate with each other using human-readable names, abstracting away the need to know IP addresses.
    
7. **Network Plugins**: Kubernetes supports various network plugins (e.g., Calico, Flannel, Weave) to manage networking within the cluster. These plugins offer different features and capabilities to suit various use cases.