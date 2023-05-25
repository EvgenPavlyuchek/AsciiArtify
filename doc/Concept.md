
# Comparison of Kubernetes Cluster Deployment Tools


| Tool     	| Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             	| Pros                                                                                                                                                                                                                                                                                                	| Cons                                                                                                                                                                                                               	|
|----------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Minikube 	| Minikube is a tool that allows you to run a single-node Kubernetes cluster on your local machine. It provides an easy setup process, supports multiple hypervisors, and offers additional functionalities like DNS addon and dashboard. Minikube is suitable for small-scale development and testing of Kubernetes applications.<br>- Supported OS:<br>- Minikube supports Windows, macOS, and Linux distributions.<br>- Supported Architectures: It supports x86 and amd64 architectures.                                                                                                              	| - Easy setup and management for single-node clusters.<br>- Supports multiple hypervisors.<br>- Offers additional functionalities like DNS addon and dashboard.<br>- Suitable for small-scale development and testing.<br>- Well-documented and widely adopted.                                      	| - Limited to single-node clusters.<br>- Performance impact with resource-intensive workloads.<br>- Requires separate installations for different hypervisors.                                                      	|
|   Kind   	| Kind, which stands for "Kubernetes in Docker," is a tool that enables the creation of multi-node Kubernetes clusters using Docker containers. It offers a quick and straightforward setup process, integrates well with Docker tools and workflows, and supports different Kubernetes versions. Kind is ideal for testing scenarios and replicating production-like environments locally.<br>- Supported OS: <br>- Kind is designed to work on Linux, macOS, and Windows (via WSL2).<br>- Supported Architectures: It supports x86_64, arm64, and Windows AMD64 architectures.                          	| - Quick and easy setup for multi-node clusters using Docker.<br>- Lightweight and efficient.<br>- Integrates well with Docker tools and workflows.<br>- Supports different Kubernetes versions.<br>- Ideal for testing and replicating environments.                                                	| - Limited to running clusters on a single machine.<br>- Not suitable for complex or large-scale deployments.<br>- May have limitations in replicating certain environments.                                        	|
|    K3d   	| k3d is a lightweight tool that allows you to create lightweight Kubernetes clusters using K3s and Docker. It provides a fast and easy setup process, supports different K3s versions, and offers additional features like automatic load balancer creation. k3d is designed for quick local development and testing, and it has gained popularity for its simplicity and speed in setting up local Kubernetes clusters.<br>- Supported OS: <br>- k3d is compatible with Linux, macOS, and Windows (via WSL2).<br>- Supported Architectures: It supports x86_64, arm64, and Windows AMD64 architectures. 	| - Fast and easy setup for lightweight K3s clusters using Docker.<br>- Provides additional features like automatic load balancer creation.<br>- Supports different K3s versions.<br>- Lightweight and efficient for local development and testing.<br>- Gaining popularity for simplicity and speed. 	| - Limited to running K3s clusters, may differ from full Kubernetes distributions.<br>- May lack compatibility and features compared to mainstream distributions.<br>- Limited community support and documentation. 	|

# Demo

![Image](./demo.gif)

Demo link: https://asciinema.org/a/587166

# Deploy into Google Cloud Shell

## Minikube

    minikube start
    kubectl create deployment hello-minikube --image=registry.k8s.io/echoserver:1.10
    kubectl expose deployment hello-minikube --type=NodePort --port=8080
    curl $(minikube service hello-minikube --url)
    minikube delete


## kind

    curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.19.0/kind-linux-amd64
    chmod +x ./kind
    mv ./kind /usr/local/bin
    kind create cluster
    kubectl create deployment hello-minikube --image=registry.k8s.io/echoserver:1.10
    kubectl expose deployment hello-minikube --type=LoadBalancer --port=8080
    kubectl port-forward service/hello-minikube 8081:8080
    curl localhost:8081
    kind delete cluster

## k3d

    wget -q -O - https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
    k3d cluster create mycluster
    kubectl create deployment hello-minikube --image=registry.k8s.io/echoserver:1.10
    kubectl expose deployment hello-minikube --type=LoadBalancer --port=8080
    kubectl get deployments
    curl IP:8080
    k3d cluster delete mycluster

