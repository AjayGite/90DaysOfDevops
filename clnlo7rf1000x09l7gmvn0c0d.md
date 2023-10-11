---
title: "Launching your first Kubernetes cluster with Nginx running"
datePublished: Wed Oct 11 2023 11:31:42 GMT+0000 (Coordinated Universal Time)
cuid: clnlo7rf1000x09l7gmvn0c0d
slug: launching-your-first-kubernetes-cluster-with-nginx-running
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697021966503/edcd1cc3-c5cb-4712-abdf-223917fce326.png
tags: kubernetes, trainwithshubham, day31, kubernetescluster

---

## **What is Minikube?**

Minikube is a tool that quickly sets up a local K8s cluster on any OS. It can deploy as a VM, a container, or on bare metal.

Minikube is a pared-down version of K8s that gives you all the benefits of K8s with a lot less effort. This makes it an interesting option for users who are new to containers, and also for projects in the world of edge computing and the Internet of Things.

### Features of Minikube:-

* supports the latest K8s release
    
* cross-platform
    
* Deploy as a VM, a container, or on Bare Metal
    
* multiple container runtimes (Docker, Containers, CRI-O)
    
* Advanced features such as Load Balancer, File system mounts, Feature Gates, and Network policy.
    
* Addons for easily installed K8s applications.
    
* Supports common CI environments.
    

## Task 1- Install minikube on your local

Before beginning with installation find the prerequisites to install Minikube below

* sudo privileges
    
* 2CPUs or more
    
* 2GB of free memory
    
* 20GB of free disk
    
* Docker
    
* kubectl
    

## Diagram:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022087612/e7374a20-a341-4f60-b0f4-b9859b7dbf3f.png align="center")

## Steps:-

1. First update and upgrade your system using the following commands. (I am using Ubuntu 22.04 LTS on my Laptop)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022174404/9f18298f-aa8b-4a9b-a10e-a3bd6f6a4914.png align="center")
    
2. Install some basic required packages.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693314293413/f49b1ead-af88-4b47-bb9d-cde8d974a0ae.png?auto=compress,format&format=webp align="left")
    
3. Minikube can run a Kubernetes cluster either in a VM or locally via Docker. Install docker
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022754477/11721d90-00a6-40fb-ac65-76448d6effd3.png align="center")
    
4. Start and enable Docker and Add current user to docker group (To use docker without root)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022792969/906a36bb-b1a8-4ed9-8bf5-a7a9e601da81.png align="center")
    
5. Find the below command. [**Link**](https://minikube.sigs.k8s.io/docs/start/) to install minikube
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022820350/b94cb5aa-6b45-467f-8ac4-f9efaf9dd1da.png align="center")
    
6. Install Kubectl
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022849086/dac1de87-fc59-4f64-8031-d2c5d7df2262.png align="center")
    
7. Now, you can start Minikube with the following command:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022912365/49634c34-6bbd-4039-9366-5bf8161e14e3.png align="center")
    
    1. To interact with the minikube cluster we need to install Kubectl. Download the latest binary release with the following command. Make the downloaded kubectl binary executable and move the binary into your PATH
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697022959213/0c7ba9cc-66e1-471e-8d84-a23636925ec7.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697023279088/5ce810d4-c6ee-44ce-a098-b5b1947f0082.png align="center")
        

Yeah! You installed minikube and kubectl successfully.

## Pod:-

The pod is the smallest deployable unit in K8s.

It is a group of one or more containers that are deployed together on the same host which shares storage, and network resources, and a specification for how to run the containers.

A Pod models an application-specific "logical host"; it contains one or more application containers that are relatively tightly coupled.

## Task 2- Create your first pod on Kubernetes through minikube.

To create a Pod we have to write a manifest file which looks like below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697023300772/1da27230-f407-4d68-ad12-df139ce51aea.png align="center")

To create a Pod from the manifest file use `kubectl apply -f pod.yml` command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697023314339/90e963b0-1e39-4742-a04c-e2c43934280e.png align="center")

To stop Minikube use `minikube stop` command.

This is how we create and run pods with the help of Minikube.

Thank you so much for taking the time to read till the end! Hope you found this blog informative.