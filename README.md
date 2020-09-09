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
> Recap 

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

