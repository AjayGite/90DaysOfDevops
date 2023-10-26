---
title: "Launching Your Kubernetes Cluster With Deployment"
datePublished: Thu Oct 26 2023 13:34:47 GMT+0000 (Coordinated Universal Time)
cuid: clo787u4j000f09ld3z97ecmu
slug: launching-your-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698325995780/2c19f25c-c733-4edc-951c-b2e8ea58656f.png
tags: kubernetes, 90daysofdevops, trainwithshubham, day32

---

### **What is Deployment in k8s**

In Kubernetes (K8s), a **Deployment** is a resource object that provides declarative updates to applications. It allows you to describe an application's life cycle, such as which images to use for the app, the number of replicas, and how to update them, in a declarative way. Deployments are part of the Kubernetes "Apps" API group and serve as a higher-level abstraction over pods.

Here are some key characteristics and features of Deployments:

1. **Declarative Configuration**: You define the desired state of your application in a Deployment manifest (usually a YAML file) rather than specifying a sequence of commands.
    
2. **Replica Sets**: Deployments manage Replica Sets, which in turn manage the actual pods running your application. This ensures that the desired number of replicas (instances) are always available.
    
3. **Scaling**: You can easily scale your application up or down by changing the number of desired replicas in the Deployment manifest. Kubernetes will automatically adjust the number of pods accordingly.
    
4. **Rolling Updates**: Deployments support rolling updates, which allow you to update your application without downtime. You specify a new version of the app in the manifest, and Kubernetes will incrementally replace the old pods with new ones.
    
5. **Rollback**: If a new version of your application causes issues, you can roll back to a previous version by simply updating the Deployment manifest with the desired image version.
    
6. **Health Checks**: Deployments can perform readiness and liveness checks on pods using probes. This ensures that pods are healthy and ready to serve traffic before being included in the load balancing.
    
7. **Rolling Restarts**: You can perform rolling restarts of your application to apply configuration changes or perform maintenance tasks.
    
8. **History and Revision Tracking**: Deployments maintain a history of all revisions, making it easy to track changes and rollbacks.
    

### **🔹Task-1:**

**Create one Deployment file to deploy a sample todo-app on K8s using the "Auto-healing" and "Auto-Scaling" feature**

**Prerequisites:**

* Docker Hub account
    
* Docker image of the todo-app built and tagged
    

**Step 1: Push the Docker Image to Docker Hub**

Before deploying the Kubernetes Deployment, ensure that you have built the Docker image of the todo-app and pushed it to Docker Hub. This ensures that the Kubernetes cluster can access the image when creating the pods.

```bash
docker login   # Log in to your Docker Hub account
docker push ajaygite7764/todo-app
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698326860191/0f3c4c2c-1534-4879-8c25-488c2a2fbdf5.png align="center")

**Step 2: Create a Deployment YAML File**

Create a new YAML file named `deployment.yml` and add the following content to it. This YAML file defines the Deployment with auto-healing and auto-scaling features.

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app-deployment
spec:
  replicas: 3  # Initial number of replicas
  selector:
    matchLabels:
      app: todo-app
  template:
    metadata:
      labels:
        app: todo-app
    spec:
      containers:
        - name: todo-app
          image: ajaygite/todo-app
          ports:
            - containerPort: 8000
```

**Explanation of deployment.yml**

* `apiVersion`: Specifies the Kubernetes API version to use.
    
* `kind`: Defines the resource type as a Deployment.
    
* `metadata`: Contains metadata about the Deployment, including its name.
    
* `spec.replicas`: Specifies the desired number of replicas (pods) to maintain. This is the basis for **auto-scaling**.
    
* `spec.Selector`: Defines how the Deployment selects which pods to manage based on labels.
    
* `spec.template`: Specifies the pod template to be used for creating new pods.
    
* `spec.template.metadata.labels`: Labels to be applied to the pods.
    
* `spec.template.spec.containers`: Defines the containers within the pod, including the image and ports.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698326887702/0ff47123-09bd-408a-be97-06ec7c441391.png align="center")

**Step 3: Apply the Deployment to Kubernetes**

Save the `deployment.yml` file and apply the Deployment to your Kubernetes cluster using the following command:

```bash
kubectl apply -f deployment.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698326901332/a5a3b489-e7bd-4317-9aad-7e79d5ed27ba.png align="center")

**Step 4: Testing Auto-Healing**

To validate the functionality of the auto-healing feature, deliberately remove one of the pods.

Subsequently, Kubernetes will autonomously generate a new pod to substitute the removed instance.

```bash
kubectl delete pod <pod_name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698326916261/0cb658d0-8ded-405c-81d6-fee4ecc267ab.png align="center")

**Step 5: On the worker node, verify whether the docker container working or not**

```bash
docker ps
sudo docker exec -it <docker-container> bash #Get into the docker container
curl -L http://127.0.0.1:8000
```

**Step 6:** To set the CPU utilization target for auto-scaling in a Kubernetes Deployment, you can use the `kubectl autoscale` command. Here's how you can do it:

```bash
kubectl autoscale deployment todo-app-deployment --cpu-percent=50 --min=2 --max=5
kubectl get hpa
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698327237941/c35ed65f-97b0-4b2f-be98-455c1681a4d9.png align="center")

This command will enable auto-scaling for your Deployment based on CPU utilization, with the specified parameters.

**Step 7**: To update the autoscaling settings, you can run the `kubectl autoscale` command with the new values, just like you did when initially setting it up. For example:

```bash
kubectl edit hpa todo-app-deployment
```

**Step 8**: To remove auto-scaling completely, you can delete the HPA resource associated with your Deployment:

```bash
kubectl delete hpa todo-app-deployment
```

**Step 9: Delete the Deployment**

If you need to remove the entire Deployment and its associated pods, use the following command:

```bash
kubectl delete -f deployment.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698326947545/0d517138-ca38-4fe1-aeed-752ddae8494b.png align="center")

By following these steps, you've successfully created a Kubernetes Deployment for a sample todo-app with auto-healing and auto-scaling features. The Docker image was pushed to Docker Hub, allowing Kubernetes to fetch it during the deployment process.