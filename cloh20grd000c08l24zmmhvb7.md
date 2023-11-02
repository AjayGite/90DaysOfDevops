---
title: "Working with Services in Kubernetes"
datePublished: Thu Nov 02 2023 10:38:48 GMT+0000 (Coordinated Universal Time)
cuid: cloh20grd000c08l24zmmhvb7
slug: working-with-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698838405909/927272de-2740-46ae-bab4-dfc7fd289b6c.png
tags: kubernetes, containers, trainwithshubham, day34

---

### **🔹What are Services in K8s?**

A Kubernetes Service is a mechanism to expose applications both internally and externally. Every service will create an everlasting IP address that can be used as a connector.

Additionally, it will open a `port` that will be linked with a `targetPort`. Some services can create ports in every [Node](https://sysdig.com/learn-cloud-native/kubernetes-101/what-is-a-kubernetes-node/), and even external IPs to create connectors outside the cluster.

With the combination of both IP and Port, we can create a way to uniquely identify an application.

Services come in several types:

* **ClusterIP (default)**:
    
    This is the default type for service in Kubernetes.
    
    As indicated by its name, this is just an address that can be used inside the cluster. This creates a connection using an internal Cluster IP address and a Port. But, what if we need to use this connector from outside the Cluster? This IP is internal and won’t work outside.
    
    This is where the rest of the services come in…
    
* **Nodeport:**
    
    A NodePort differs from the ClusterIP in the sense that it exposes a port in each Node. When a NodePort is created, kube-proxy exposes a port in the range 30000-32767.
    
    The problem with using a NodePort is that you still need to access each of the Nodes separately.
    
* **LoadBalancer:**
    
    A LoadBalancer is a Kubernetes service that:
    
    * Creates a service like ClusterIP
        
    * Opens a port in every node like NodePort
        
    * Uses a LoadBalancer implementation from your cloud provider (your cloud provider needs to support this for LoadBalancers to work).
        
    * LoadBalancer services are typically used in cloud environments where they provision a load balancer to distribute traffic across multiple pods. This allows for external access to services.
        
* **ExternalName:**
    
    This service type maps a service to an external DNS name. It's used for accessing external services from within the cluster.
    

Services provide an essential layer of networking abstraction in Kubernetes, allowing applications to communicate reliably and consistently, regardless of where pods are located or how they are scaled.

![](https://miro.medium.com/v2/resize:fit:700/1*tnK94zrEwyNe1hL-PhJXOA.png align="left")

# **Task 1: Create a Service for your todo-app Deployment**

1. **Create a Service definition YAML file:** Begin by creating a YAML file named `service.yml` to define your Service for the `todo-app` Deployment.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698912233134/cca1c0a7-b9dc-4512-99d8-795e7bf012a0.png align="center")
    
    ```bash
     apiVersion: v1
     kind: Service
     metadata:
       name: todo-app-deployment
       namespace: k8s-day34
     spec:
       type: NodePort
       selector:
         app: todo-app
       ports:
         - port: 80
           targetPort: 8000
    ```
    
    1. **Apply the Service definition:** Execute the following command to apply the Service definition to your Kubernetes cluster.
        
        Don't forget to replace `<namespace-name>` with the actual namespace where your `todo-app` Deployment resides.
        
        ```bash
        kubectl apply -f service.yml -n <namespace-name>
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698913191474/b6685563-c9af-4853-9a71-ca6b93f3b771.png align="center")
        
    2. **Verification:** To ensure that the Service is working correctly, access the `todo-app` using the Service's IP and Port within your specified Namespace.
        
        ```bash
         kubectl get svc -n <namespace-name>
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698913242393/a0bf4fe0-bae3-4c76-86c9-ba99f894b14d.png align="center")
        
    
    # **Task 2: Create a ClusterIP Service for accessing the todo-app within the cluster**
    
    1. **Create a ClusterIP Service definition YAML file:** Now, create another YAML file named `cluster-ip-service.yml` to define a ClusterIP Service for your `todo-app` Deployment.
        
        ```bash
         apiVersion: v1
         kind: Service
         metadata:
           name: todo-app-clusterip
           labels:
             app: todo-app
         spec:
           selector:
             app: todo-app
           ports:
             - protocol: TCP
               port: 8000
               targetPort: 8080
           type: ClusterIP
        ```
        
    2. **Apply the ClusterIP Service definition:** Use the following command to apply the ClusterIP Service definition to your Kubernetes cluster within the specified namespace.
        
        ```bash
         kubectl apply -f cluster-ip-service.yml -n <namespace-name>
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698913347747/7dc1dac3-503d-4c2b-a0be-6f9866e88f63.png align="center")
        
    3. **Verification:** To confirm that the ClusterIP Service is functioning correctly, access the `todo-app` from another Pod within the cluster, still in your specified Namespace.
        
        Create a YAML file named `test-pod.yml` for a testing pod:
        
        ```bash
         apiVersion: v1
         kind: Pod
         metadata:
           name: test-pod
         spec:
           containers:
             - name: busybox
               image: busybox       command: ['sh', '-c', 'while true; do wget -q -O- clusterip:8000; done']'
        ```
        
    4. Apply the ClusterIP Service definition to your K8s cluster using the command & verify todo-app is running
        
        ```bash
         kubectl apply -f test-pod.yml -n <namespace-name>
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698913419313/1644e35f-ead0-4ee9-8e08-2e2244bfa919.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698913614908/672ff31c-69e8-4d53-a086-30215750fbb9.png align="center")
        
        # **Task 3: Create a LoadBalancer Service for accessing the todo-app from outside the cluster**
        
        1. **Create a LoadBalancer Service definition YAML file:** Create a YAML file named `load-balancer-service.yml` to define a LoadBalancer Service for your `todo-app` Deployment.
            
            w you can do it:
            
            ```bash
             apiVersion: v1
             kind: Service
             metadata:
               name: todo-app-loadbalancer
             spec:
               selector:
                 app: todo-app
               ports:
                 - protocol: TCP
                   port: 80
                   targetPort: 8000
               type: LoadBalancer
            ```
            
        2. **Apply the LoadBalancer Service definition:** Apply the LoadBalancer Service definition to your Kubernetes cluster within the specified namespace using the following command:
            
            ```bash
             kubectl apply -f load-balancer-service.yml -n <namespace-name>
            ```
            
        3. **Verification:** To verify the functionality of the LoadBalancer Service, access the `todo-app` from outside the cluster, within your specified Namespace with the command:
            
            ```bash
             kubectl get svc -n <namespace-name>
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698913740789/4cca951a-2ade-4b2a-9160-6d7eb3e38bc5.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698913747962/fd241c24-7667-470e-a61b-f00ef4c31538.png align="center")
            
    
    #