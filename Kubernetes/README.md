# Kubernetes
###### Kubernetes is a container orchestrator that solves problems of vertical and horizontal scalability. It creates and manages a cluster of machines, distributing computational power among them. Kubernetes is capable of running containers on different machines within the cluster, replacing failed containers, and adding new machines to the cluster when necessary. It also allows for automatic restart of applications in case of failures. Kubernetes is a container orchestrator that solves scalability problems and offers various functionalities to facilitate application management.

###### Kubernetes goes beyond being just a container orchestrator, having various ready-to-use resources to solve different types of problems, such as pods, ReplicaSets, Deployments, and Volumes.

* Pods encapsulate the containers and are the basic unit of execution in Kubernetes.
* Persistent Volume is a Kubernetes resource to handle data persistence.
* Kubernetes manages a cluster with machines called master and nodes. The master is responsible for coordinating and managing the cluster, while the nodes run the applications.
* The main components of the Control Plane are the API, Controller Manager, Scheduler, and ETCD. On the nodes, we have Kubelet and KubeProxy.
* The API is responsible for maintaining communication between Kubernetes components.
* Kubectl is the tool used to communicate with the API and manage cluster resources.

###### The Kubernetes manages a cluster, which consists of master nodes (responsible for coordinating the cluster) and worker nodes (responsible for running applications). Within the master node, we have components such as the API, Controller Manager, Scheduler, and ETCD, each responsible for different functions. On the worker nodes, we have Kubelet (responsible for executing pods) and KubeProxy (responsible for communication between nodes). The API is the central point of communication, receiving commands from the outside world and interacting with other components. To communicate with the API, we use the kubectl tool, which allows us to create, read, update, and delete cluster resources in a declarative or imperative manner.
---
### Pods
###### Pods are the basic unit of execution in Kubernetes, not individual containers like with Docker. A pod can contain one or more containers that share the same IP address and network namespace. This allows containers within the same pod to communicate easily via localhost. When a container within a pod fails, the entire pod is terminated and Kubernetes creates a new pod to replace it. Pods are ephemeral, meaning they can be created and destroyed at any moment by Kubernetes. The main advantage of pods is that they enable simplified communication between containers that are part of the same pod.

#### Usefull commands
> k run nginx-pod --image=nginx:latest

> k get pods --watch

> k get pods -o wide

> k describe pod nginx-pod

> k delete pod nginx-pod

> k exec -it nginx-pod -- bash

> k delete pods --all

#### Creating the first pod using declarative way
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod1
spec:
  containers:
    - name: nginx-container1
      image: nginx
```

> k apply -f defaultPodDefinition.yaml

### Services
###### Kubernetes has a feature called "service" that resolves the problem of communication between different pods. Pods can have their IP addresses changed when they are recreated, making it difficult to communicate between them. Services provide a fixed IP and a stable DNS name so that pods can communicate with each other, regardless of changes to pod IPs. There are three types of services: ClusterIP, NodePort, and LoadBalancer, each with a specific purpose.

### ClusterIP
###### The ClusterIP service allows the access from a pod to another using, inside the clouster.
###### Service definition:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: svc-nginx-pod
spec:
  selector:
    app: nginx-pod
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
  ```

###### Inside the pod, you need to add a label that defines the target to service access:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod1
  labels:
    app: nginx-pod
spec:
  containers:
    - name: nginx-container1
      image: nginx
      ports:
        - containerPort: 80
```

### ConfigMap
###### In Kubernetes, a `ConfigMap` (short for "Configuration Map") is an object that stores configuration data as key-value pairs. It's used to decouple the configuration of your application from its code and make it easier to manage and maintain.

###### A ConfigMap is like an environment variable file, but instead of being stored as individual environment variables, it's stored as a single object that can be consumed by your application.

###### Example using ConfigMap:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: db-configmap
data:
  MYSQL_ROOT_PASSWORD: "123456"
  MYSQL_DATABASE: empresa
  MYSQL_USER: user
  MYSQL_PASSWORD: "123456"
  ```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
      envFrom:
        - configMapRef:
            name: db-configmap
```

### ReplicaSet
###### In Kubernetes, a ReplicaSet (also known as ReplicationController) is an object that ensures a specified number of replicas (or copies) of a Pod  are running at any given time. It's a fundamental concept in Kubernetes, and it helps you manage the scalability and availability of your applications.

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: portal-noticias-rs
  labels:
    app: portal-noticias-rs
spec:
  template:
    metadata:
      labels:
        app: portal-noticias
    spec:
      containers:
      - name: portal
        image: aluracursos/portal-noticias:1
        ports:
          - containerPort: 80
        envFrom:
          - configMapRef:
              name: portal-configmap
  replicas: 3
  selector:
    matchLabels:
      app: portal-noticias
```

### Deployments
###### TODO

> k apply -f deployment.yaml

> k get deployments

> k rollout status deployment/deployment-name

> k edit deployment/deployment-name

> k rollout history deployment/portal-noticias-dp

> k rollout history deployment/portal-noticias-dp --revision=1

> k rollout undo deployment/portal-noticias-dp

