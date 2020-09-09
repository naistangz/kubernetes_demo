# Kubernetes

**Contents**
-[x] [The Legacy Monolith](#)
-[x] [Microservices](#)
-[x] [Refactoring](#)
-[x] [Case Studies](#)
-[x] [Kubernetes]

## The Legacy Monolith
> Recap - A monolith is a large, single piece of software. It runs on a single system which has to satisfy its compute, memory, storage, and networking requirements.

Moving an application to the cloud presents a multitude of problems, especially when dealing with a monolith application - consisting of features, redundant logic translated into thousands lines of code, written in a single programming language, based on outdated software architecture patterns and principles.
This makes development more challenging - loading, compiling, and building times increase with every new update. However, there is some ease as it is running on a single server.

The **scaling** of individual features is almost impossible as the enitre monolith application runs as a single process. This means scaling the entire application requires deploying a new instance of the monolith on another server, typically behind a load balancing appliance which is a pricey solution. 

During upgrades, patches or migrations of the monolith application - downtimes occur and maintenance have to be planned. An application with downtime can result a significant loss of profit. 


## Microservices
- They are carved out of the monolith, separated from one another, becoming distributed components each described by a set of specific characteristics. 
- Loosely coupled, each performing a specific business function. 
- All the functions grouped together form the overall functionality of the original monolithic application.
- Can be deployed individually on separate servers provisioned with fewer resources - only what is required by each service and the host system itself. 
- Developed and written in a modern programming language, selected to be the best suitable for the tpye of service and its business function. This offers flexibility when matching microservices with specific hardware when required, allowing deployments on inexpensive commodity hardware. 
- No downtime and no service disruption to clients because upgrades are rolled out seamlessly - one service at a time, rather than having to re-compile, re-build and re-start an entire monolithic application. 

## Refactoring
- In order for enterprises to move from monolith applications to microservices, the next natural step is to refactor.
- Migrating old appplications to the cloud through refactoring poses serious **challenges** e.g. postponing development and implementation of any new features, which delays progress and can even break the core of the business. 
- **Incremental refactoring** approach is required, meaning new features are developed and implemented as modern microservices which are able to communicate with the monolith through APIs, without appending to the monolith's code. 
- Features are refactored and its functionality is modernised into microservices.
- This approach offers gradual transition from monolith to microservices architecture. 
- By transforming monolith into a cloud-native application, it provides possibility of developing new features with new programming languages and applying modern architectural patterns. 

## Challenges
- Moving monolith architecture to microservices
- Determining which business components to separate from the monolith to become distributed microservices
- How to decouple databases from the application to separate data complexity from application logic
- How to test new microservices and their dependencies

## Determining whether certain monoliths can be refactored
- A monolith application may be written in older programming languages i.e Cobol or Assembler so it is more economical to re-build it from the ground up as a cloud-native application
- A poorly designed legacy application should be re-designed and re-built from scratch
- Applications tightly coupled with data stores are also poor candidates for refactoring. 
- If monolith survives refactoring phase, next challnege is finding right tools to keep the decoupled modules alive and ensure application resiliency. 

## Examples of monoliths to microservices 
- [Pinterest](https://kubernetes.io/case-studies/pinterest/) - moved from monolith architecture to micro with Docker containers. 
- Despite being born on the clouds, running on AWS, still faced growing pains e.g. layers of infrastructure, diverse set-up tools and platforms for different workloads, leading to inconsistent and complex end-to-end developer experience, less velocity to get to production. 
- Previously, heavily relied on virtual machines, on EC2 instances.


## Kubernetes :rocket:
> Recap containerisation, microservices, containers

### What are containers?
- Portable, isolated virtual environments for aplications to run without interference from other running applications.

### What are Microservices?
- Lightweight applications written in different modern programming languages, with specific dependencies, libraries and environmental requirements.
- To run app, it is packaged together with dependencies. 
- Containers encapsulate microservices and their dependencies but do not run them. Containers run container images. 

## Container Images
- They package the application with its runtime and dependencies
- Container is deployed from image offering an isoalted executable environment for the application. 
- Containers can be deployed from Virtual machines, workstations or public cloud. 

## Container Orchestration
- In dev environments, running containers on single host for dev and testing applications is possible.
- However, migrating to QA and prod environments, this is not an option because applications and services need to meet specific requirements:
	- fault-tolerance
	- optimal resource usage
	- accessibility from outside world 
	- seamless updates/rollbacks without any downtime

- **Container orchestrators** are tools which group systems together to form **clusters** where containers' deployment and management is automated at scale 
- Meet requirements mentioned above.
- Container orchestrators use a single controller/management unit (to connect multiple nodes together

## Examples of Container Orchestrators
- Amazon Elastic Container Service (ECS)
- Azure Container Instances
- Azure Service Fabric
- Kubernetes (most popular)
- Marathon
- Nomad
- Docker Swarm

## Why Container Orchestrators?
- We can manually maintain a couple of containers or write scripts for dozens of containers, however, orchestrators make things much easier for operators especially when it comes to managing hundreds and thousands of containers.
- Containers can:
	- Group hosts together and create a cluster
	- Schedule containers to run on hosts in the cluster based on resources availability
	- Enable containers in a cluster to communicate with each other regardless of the host they are deployed to in the cluster
	- Bind containers and storage resources
	- Allow for implementation of policies to secure access to applications running inside containers. 

## Where to deploy container orchestrators?
- Can be deployed on infrastructure of choice - on bare metal (computer system that doesn't have OS, VM installed directly on hardware) VMs, on-premise, or cloud.
- Kubernetes provides turnkey solutions, meaning clusters can be installed on top of cloud IaaS (infra as a service) e.g Docker, AWS EC2, GCE, IBM
- There are also managed container OaaS (orchestration as a service) solutions e.g Google Kubernetes Engine, Amazon Elastic Container Service for Kubernetes, IBM Cloud Kubernetes, etc

# What is Kubernetes?
- [x][Introduction](#) 
- [x][Why use Kubernetes](#)
- [x][Features of Kubernetes](#)

## Introduction 
- Kubernetes comes from Greek word κυβερνήτης, meaning helmsman or ship pilot. Kubernetes is like the pilor on a ship of containers.
- Also referred to as **k8s** (there are 8 characters between k and s)

## Features 
- **Automatic bin packing** - schedules containers based on resource needs, maximises utilisaiton without sacrificing availability
- **Horizontal Scaling** - scaled manually or automatically based on CPU or custom metrics utilisation
- **Service discovery and load balancing** - Containers receive their own IP addresses from k8 and assigned a single DNS name to a set of containers to aid in load-balancing requests across containers. 
- **Automated rollouts and rollbacks** - rolls and rolls back application updates and configuraiton changes, constantly monitoring application's health to prevent any downtime, making apps highly available. 
- **Secret and configuration management** - K8 manages secrets and configuration details for an application separately from the container image, to avoid re-build of respective image. 

## Use cases
- When we want to deploy containers from any environment e.g local or remote VM, bare metal, public/private/hybrid/mult-cloud setups.
- K8's architecture is modular and pluggable. Functionality can be extended by writing custom resources, operators, custom APIs, scheduling rules or plugins. 

# Kubernetes Architecture 
Kubernetes has the following components:
	- One or more **master nodes**
	- One or more **worker nodes**
	- Distributed key-value store, such as **etcd**

<img src="https://courses.edx.org/assets/courseware/v1/8f441b27101be805bc286e67adc671a2/asset-v1:LinuxFoundationX+LFS158x+2T2019+type@asset+block/Kubernetes_Architecture1.png" alt="Kubernetes_Architecture">

## What is master node?
- Running env for control plane 
- Responsible for managing the state of a kubernetes cluster
- Brain behind the operations inside cluster 
- Control plane components are agents with different roles in the cluster's management.
- To communicate with the cluser, users send requests to master node via CLM, Web UI, or API
- Control plane components on the master node running controllers to regulate the state of the Kubernetes cluster
- Runs controllers responsible to interact with underlying infrastructure of cloud provider, manage load balancing and routing. 

## What is the worker node?
- Provides running environment for client applications 
- Applications running in containerised microservices are encapsulated in Pods, controlled by cluster control plane agents running on master node. 
- To access applications from external world, we connect to worker nodes, not master node. 

## Networking 
- Decouple microservices rely heavily on networking in order to mimic tight-coupling in monolith architecture.
- K8 needs to address container-to-container communication inside Pods, pod-to-pod communication, pod-to-service communication, external-to-service communication for clients to access applications in a cluster.
- This is achieved with **network namespace** pods can talk to each via localhost

## Installing Minikube
```
Install VirtualBox
Install Minikube
```
Installing minikube
```bash
$ curl -Lo minikube https://storage.googleapis.com/minikube/releases/v1.0.1/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```

```
$ minikube start
```

```
$ minikube status
```

```
$ minikube stop
```

Starting Minikube with CRI-O as container runtime, instead of Docker:

```bash
minikube start --container-runtime=cri-o
minikube v1.0.1 on linux (amd64)
```
	
SSHing into the Minikube's VM
```bash
minikube ssh 
```

Listing docker containers 
```bash
sudo runc list 
```

Installing kubectl on macOS
`kubectl` is the Kubernetes Command Line Interface client to manage cluster resources and applications 

```bash
$ curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
```
or with `homebrew package manager`
```bash
$ brew install kubernetes-cli
```

Configuring `kubectl` file in order to access the Kubernetes cluster:
```bash
kubectl config view
```
or 
```bash
cat ~/.kube/config
```
To access cluster, the `kubectl` client needs the master node endpoint and the credentials to be able to interact with the API server running on the master node. 

Gathering info about the minikube cluster:
```bash
kubectl cluster-info
```
E.g.:
```bash
➜  kubernetes_demo git:(master) ✗ kubectl cluster-info
Kubernetes master is running at https://127.0.0.1:32772
KubeDNS is running at https://127.0.0.1:32772/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

Using the Kubernetes web-based user interface:
```bash
minikube dashboard
```

The `kubectl proxy` command to authenticate the API server on the master node:
```bash
$ kubectl proxy
Starting to serve on 127.0.0.1:8001
```

When `kubectl proxy` is running, we can send requests to the API over the `localhost` on the proxy port 8001:

```bash
$ curl http://localhost:8001/
```

