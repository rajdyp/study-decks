??? question annotate "Kubernetes architecture"

    Kubernetes is an open-source container orchestration platform designed to automate the deployment, scaling, and management of containerized applications.
    
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

1.  The API server is the central component that exposes the Kubernetes API. It acts as the frontend for the Kubernetes control plane. All administrative tasks and communication with the cluster are conducted through the API server.
2.  etcd is a distributed key-value store that serves as the cluster's primary data store for all configuration data. It stores the cluster state and configuration, ensuring consistency and high availability. The API server interacts with etcd to read or write cluster state information.
3.  The Controller Manager is responsible for running controller processes. Controllers are responsible for maintaining the desired state of the system by watching the state of the cluster and making necessary changes to achieve and maintain the desired state.
4.  The Scheduler is responsible for placing newly created pods onto nodes in the cluster. It takes into account factors such as resource constraints, affinity/anti-affinity rules, and workload-specific requirements.
5.  Serves as an interface between Kubernetes and the cloud provider's APIs, enabling the control plane to interact with the underlying cloud infrastructure seamlessly.
6.  The Kubelet is an agent that runs on each node in the cluster. It is responsible for ensuring that containers are running in a Pod. It communicates with the API server to receive instructions and reports the node's status back to the control plane.
7.  The container runtime is responsible for pulling container images from a registry and running containers. Kubernetes supports various container runtimes such as Docker, containerd, and others.
8.  Kube Proxy is responsible for maintaining network rules on nodes. It enables communication between different pods across the cluster and performs network address translation (NAT) for pod-to-pod communication.
9.  A pod is the smallest deployable unit in Kubernetes and represents a single instance of a running process in a cluster. A pod can contain one or more containers sharing the same network namespace and storage.
10.  Kubernetes provides a DNS add-on for service discovery within the cluster. It allows pods to communicate with each other using names rather than hard-coded IP addresses.


