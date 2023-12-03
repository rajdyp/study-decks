## Kubernetes Basics
??? question annotate "What is Kubernetes?"

    - Open-source container orchestration platform.
    - Designed to automate the deployment, scaling, and management of containerized applications.

<!-- end of question -->


??? question annotate "Kubernetes architecture"

    Master Components:
    
    1. kube-apiserver (1)
    
    2. etcd (2)
    
    3. kube-controller-manager (3)
    
    4. kube-scheduler (4)

     5. cloud-controller-manager (5)
    
    Node Components:
    
    1. kubelet (6)
    
    2. Container Runtime (7)
    
    3. kube-proxy (8)
    
    4. Pod (9)

    Add-ons:
    
    1. DNS (10)
    2. Ingress Controller (11)

1.  - Central component that exposes the Kubernetes API.
    - Acts as the frontend for the Kubernetes control plane.
2.  - Consistent and highly-available key value store.
    - Stores cluster state and configuration data.
3.  - Manages controller processes.
    - Controllers are responsible for maintaining the desired state of the cluster.
4.  - Watches for newly created Pods and selects a node for them to run on.
5.  - Serves as an interface between Kubernetes and the cloud provider's APIs.
6.  - An agent that runs on each node in the cluster.
    - Ensures that containers are running in a Pod.
    - Communicates with the API server.
    - Reports node's status back to the control plane.
7.  - Responsible for pulling container images from a registry and running containers.
8.  - Network proxy, responsible for managing network connectivity.
    - Enables communication between pods, services, and external entities.
    - Provides load balancing for services.
9.  - Smallest deployable unit and the basic building block in Kubernetes.
    - A pod can contain one or more containers sharing the same network namespace and storage.
10. - Provides DNS-based service discovery.
    - Allows services to be accessed by their DNS names.
11. - Manages external access to services within the cluster.

<!-- end of question -->


??? question annotate "Why pods are considered the basic building blocks in Kubernetes?"

    - Pods provide a way to group and manage containers that need to work together allowing them to be treated as a single unit of deployment.

<!-- end of question -->
