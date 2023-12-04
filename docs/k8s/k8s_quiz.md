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
9.  - Smallest deployable unit in Kubernetes.
    - A pod can contain one or more containers sharing the same network namespace and storage.
10. - Provides DNS-based service discovery.
    - Allows services to be accessed by their DNS names.
11. - Manages external access to services within the cluster.

<!-- end of question -->


## Pods

??? question annotate "Why pods are considered the basic building blocks in Kubernetes?"

    - Pods encapsulate and co-locate one or more containers, providing a unified unit for deployment, scaling, and resource sharing.

<!-- end of question -->


??? question annotate "Discuss the phases a pod goes through?"

    - Pending (1)
    - Running (2)
    - Succeeded (3)
    - Failed (4)
    - Unknown (5)

1.  The Pod has been accepted by the Kubernetes cluster but is awaiting resource allocation, scheduling, and container image downloads.
2.  The Pod has been assigned to a node, and all containers have been created, and at least one container is currently running or in the process of starting or restarting.
3.  All containers in the Pod have terminated in success, and will not be restarted.
4.  At least one container in the Pod has terminated with a failure.
5.  For some reason the state of the Pod cannot be determined.

<!-- end of question -->
