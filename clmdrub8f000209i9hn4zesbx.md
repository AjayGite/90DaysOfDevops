---
title: "Docker Volumes and Networking in Containerization"
datePublished: Sun Sep 10 2023 18:11:21 GMT+0000 (Coordinated Universal Time)
cuid: clmdrub8f000209i9hn4zesbx
slug: docker-volumes-and-networking-in-containerization
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694247954579/af86cc4e-24ef-4f1d-af22-adb83fb8cc5a.jpeg
tags: 90daysofdevops, dockernetwork, keeplearning, trainwithshubham, dockervolume

---

### **Docker-Volume**

Docker volumes are a way to manage and persist data outside of a container. In the world of containers, where containers can be created and destroyed, having a way to store and share data beyond the container's lifecycle is important. Volumes allow you to store data separately from the container filesystem, ensuring that the data persists even if the container is removed.

**Creating a Volume:**

```bash
sudo docker volume create <volume-name>
```

**List the docker volume:**

```bash
sudo docker volume ls
```

**Check if the docker volume exists:**

```bash
sudo docker inspect <volume-name>
```

**Remove volume:**

```bash
sudo docker volume rm <volume-name>
```

**Removing all volumes:**

```bash
sudo docker volume prune
```

**There are two ways to link a container to a volume:**

**— mount flag-v or —volume flag**

**\[-- mount\] flag consists of:**

type=volume, source=&lt;name\_of\_volume&gt;, target=&lt;target\_path&gt;

```bash
sudo docker run -d —name Test-1 —mount source=new-vol,target=/app nginx:latest
```

**\[ - - volume or -v\] flag consists of three fields separated by colons**

&lt;name\_of\_the\_volume&gt; : &lt;destination\_path&gt; : &lt;optional\_config&gt;

```bash
sudo docker run -d —name Test-2 —volume new-vol-2:/app nginx:latest
```

Volume Types:

Tmpfs mount - used to temporarily store sensitive data in memory

Named or anonymous volume - managed by Docker using its CLI

Bind mount - arbitrary directory mounted from host to container

### **Docker Network**

Think of Docker networks as virtual highways connecting different containers within your Docker environment. Just like real-life highways connect various cities, Docker networks connect different containers, enabling them to communicate and share information with each other.

**Example:**

Imagine you have a microservices-based application where each service is a separate Docker container. These services need to communicate with each other to perform tasks. Docker networks help these containers talk to one another, just like how different teams in an office need to collaborate to get work done.

Here are examples of different types of Docker networks:

**1\. Bridge Network (Default):** Think of a bridge network as a virtual office floor where different teams have their own designated space. Each team can work independently, but they can also collaborate when needed. Similarly, containers in a bridge network can communicate with each other, and they are isolated from containers in other networks.

**Example:** You have multiple applications like HR, Sales, and Marketing. You create a bridge network for each department. Containers within the same network can easily interact, but they are separate from containers in other networks.

```bash
docker run -d --network=bridge -p 80:80 nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694365564127/f9e4a53d-43e3-4c62-8c81-d689986ea31e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694365584818/c0eaf891-2fab-4b1e-85a4-4272dbfc4602.png align="center")

**2\. Host Network:** Imagine a co-working space where different companies share a common area. Here, containers are directly connected to the host's network, just like companies connecting to the shared space's resources.

**Example:** You have containers that need direct access to your host machine's network, like monitoring tools. By using the host network, these containers can access resources without additional network setup.

```bash
docker run -d --network=host nginx
```

**3\. Overlay Network:** Picture a company with multiple branch offices located in different cities. Each office operates independently, but they need to communicate seamlessly. Overlay networks connect containers across different Docker hosts, just like branches of a company staying connected.

**Example:** You're running containers on different servers across multiple locations. Overlay networks enable containers to communicate across servers as if they're on the same network.

```bash
docker network create -d overlay my_overlay_network
docker service create --network=my_overlay_network --name=web nginx
```

**4\. Macvlan Network:** Think of a macvlan network as assigning a dedicated phone number to each employee in an office. Similarly, each container in a macvlan network gets a unique MAC address and can be assigned an IP address like an individual entity.

**Example:** You want each container to have its own IP address as if they were separate physical machines. Macvlan networks are useful when you need containers to appear as separate devices on the network.

```bash
docker network create -d macvlan --subnet=192.168.1.0/24 --gateway=192.168.1.1 -o parent=eth0 my_macvlan_network
docker run -d --network=my_macvlan_network --name=container1 nginx
```

* `docker network create`: This is the command for creating a Docker network.
    
* `-d macvlan`: This specifies that you want to create a macvlan network.
    
* `--subnet=192.168.1.0/24`: This sets the subnet for the macvlan network to `192.168.1.0/24`. This subnet defines the IP address range that containers on this network can use.
    
* `--gateway=192.168.1.1`: This specifies the gateway IP address for the macvlan network. The gateway is used for routing traffic to and from the containers on the network.
    
* `-o parent=eth0`: This option specifies the physical network interface (`eth0` in this case) on the host to which the macvlan network is attached. Containers connected to this network will use `eth0` as their parent interface on the host.
    
* `my_macvlan_network`: This is the name you've given to the macvlan network you're creating. You can replace it with your desired network name.
    

**5\. None Network:** Imagine you have a team working remotely from different locations. The "none" network is like isolating each team member in their own individual workspace with no direct communication between them.

**Example:** You want to run a container in complete isolation from any network. This can be useful for certain security-sensitive applications that shouldn't have any network access.

```bash
docker run -d --network=none nginx
```

**6\. Custom Bridge Network:** Think of a custom bridge network as creating your own unique collaboration space within a co-working building. You define the rules for communication and interaction, allowing certain members to connect while keeping others separate.

**Example:** You need fine-grained control over communication between containers. You create a custom bridge network, add specific containers to it, and configure the network rules according to your requirements.

```bash
docker network create my_bridge_network
docker run -d --network=my_bridge_network --name=container1 nginx
docker run -d --network=my_bridge_network --name=container2 nginx
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694365603899/18e00d19-1827-49d0-b20b-07084a67426e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694365611968/7da383d8-e00b-4985-92bd-cf19bcce9371.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694365619719/8eb96ebf-00a4-48b4-91e5-267390c9ad53.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694365643428/1fb2a433-eefe-4b39-834c-c5984a7d9a42.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694365646346/592168a9-e6c5-4f1b-b813-9c4345ae90b3.png align="center")

**7\. IPvlan Network:** Imagine you have a large apartment building with multiple units, and each unit has its own separate entrance and address. The "ipvlan" network is similar to creating individual addresses for each unit within the same physical building.

In Docker, the `ipvlan` network type allows you to create multiple virtual interfaces, each with its own unique IP address, all associated with the same physical network interface. This enables containers to have their own distinct network identities, even though they share the same underlying network infrastructure.

**Example:** Consider a scenario where you have a server with a single physical network interface. You want to run multiple containers on this server, each with its own IP address and network isolation, but all using the same physical network connection.

```bash
docker network create -d ipvlan --subnet=192.168.0.0/24 --gateway=192.168.0.1 -o parent=eth0 my_ipvlan_network
docker run -d --network=my_ipvlan_network --name=container1 nginx
```

Refer: [**https://www.youtube.com/live/UNew\_BBNVPk?feature=share**](https://www.youtube.com/live/UNew_BBNVPk?feature=share)

### **Task-1:**

Create a multi-container docker-compose file which will bring *UP* and bring *DOWN* containers in a single shot ( Example - Create application and database container )

Checkout my repository using the following link: [https://github.com/AjayGite/todo-flask-app](https://github.com/AjayGite/todo-flask-app)

### **Task-2**

* Learn how to use Docker Volumes and Named Volumes to share files and directories between multiple containers.
    
    Create two or more containers that read and write data to the same volume using the `docker run --mount` command.
    
    **Create a Named Volume**: Create a named volume using the `docker volume create` command. For example:
    
    ```bash
      docker volume create named-volume
    ```
    
* **Create Containers with Shared Volume**: Create two or more containers that share the same named volume using the `docker run --mount` command. Here's an example:
    
    ```bash
      docker run -d --name container1 --mount source=named-volume,target=/app image_name
      docker run -d --name container2 --mount source=named-volume,target=/app images_name
    ```
    
* Verify that the data is the same in all containers by using the docker exec command to run commands inside each container.
    
    **Verify Shared Data**: You can use the `docker exec` command to run commands inside each container to verify that they are using the same volume. For instance:
    
    ```bash
      docker exec -it container1 sh
      ls /app
    ```
    
    **Write and Read Data**: Inside each container, you can write and read data to/from the shared volume:
    
    ```bash
      touch file.txt
    ```
    
    **Check Data in Other Containers**: After writing data in one container, check if the data is visible in the other container:
    
    ```bash
    docker exec -it container2 sh
    touch /app/data.txt
    cat /app/data.txt
    ```
    
* Use the docker volume ls command to list all volumes and docker volume rm command to remove the volume when you're done.
    
    **List and Remove Volumes**: You can list all volumes using the `docker volume ls` command:
    
    ```bash
      docker volume ls
    ```
    
    **Remove Volume**: When you're done, you can remove the named volume using the `docker volume rm` command:
    
    ```bash
      docker volume rm mydata
    ```
    
    This task demonstrates how Docker Volumes and Named Volumes can be used to share files and directories between multiple containers. The named volume `mydata` is created, and two containers (`container1` and `container2`) are connected to it. Data written in one container is visible in the other due to the shared volume. Finally, the volume is removed when you no longer need it.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694368743814/d9f322ac-b73b-4942-8cf5-08397ee6b043.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694368749673/82013c63-8ad3-4980-a0e2-2c27b1f6c181.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694368754380/658d9b20-3855-488b-b5c9-0b8b9b6e12e6.png align="center")