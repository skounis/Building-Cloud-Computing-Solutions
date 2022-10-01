# Cloud Virtualization, Containers and APIs
[Cloud Virtualization, Containers and APIs](https://www.coursera.org/learn/cloud-virtualization-containers-api-duke/) - Duke University

## Week I
### Overview
* Virtulization and Containers
* Spot Instances
* Docker format containers
* Kubernetes
* Microservices
* DevOps best practices
* Monitoring and Logging

#### Learning Objectives
* Evaluate virtualization and container technology
* Develop effective and efficient technical solutions with Microservices
* Evaluate effective technical operations stategies using Cloud development best practices.

#### Prerequisitied
* Python
* Linux
* IT Infrastructure 
* JSON and YAML

### Project
* Containarized Flash Microservice
* Managed container service
    * Cloud run: Fully managed container service on GCP
    * EKD: Container platform on AWS (Kubernetes environment)

## Week II
### Virtual Machines
* Containers vs VMs
* Spot Instances
* GCP VM

#### Objects
* Evaluate virtualization abstractions
* Build solutions with VMs

#### Key terms
* Container
    * Cloud native applications
    * DevOps best practices
    * Includer runtime with code
    * Launch time in miliseconds 
* Virual Machines
    * Used for monolithic applications
    * Run OS inside of another OS
    * Launch time from seconds to minutes
* Docker format container
    * Flat file with instructions / directives
    * Can live inside the source countrol
    * Launch time from seconds to minutes

#### Containers vs VMs
* VMs: Guest and Host OSs
* VM: Full operating system.
* VM: suitable for monolithic application
* VM: Convert from a physical machine
* VM: Lift and shift of legacy applications
* Container: Host and a subset of an OS for guest. More like an process than an OS. Mor lightweight, smaller, faster.
* Container: Good fit for DevOps best practices, continuous integration, micro services.
* Key difference: Portability

> [Red Hat on Containers vs VMs](https://www.redhat.com/en/topics/containers/containers-vs-vms)
> The caveat is that containers have to be compatible with the underlying OS.
> Compared to VMs, containers are best used to: 
> * Build cloud-native apps
> * Package microservices
> * Instill DevOps or CI/CD practices
> * Move scalable IT projects across a diverse IT footprint that shares the same OS

> Because containers are so small, there are usually hundreds of them loosely coupled together—which is why container orchestration platforms (like [Red Hat OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift) and [Kubernetes](https://www.redhat.com/en/topics/containers/what-is-kubernetes)) are used to provision and manage them.

> **Containers use the host operating system's kernel**. In contrast to containers, VMs run a complete operating system–including its own kernel – [as
shown in this diagram](https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/#how-containers-work)

##### Containers vs VM comparison table
The following table shows some of the similarities and differences of these complementary technologies.
* https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/containers-vs-vm#containers-vs-virtual-machines-1


#### Spot Instance
* Launch by API or Web Console 
* You bid what price you'd like to pay. 
* It saves up to 90% off.


#### GCP Virtual machine from Terminal
```bash
gcloud compute instances create gcelabe2 --machine-type n1-standard-2 --zone us-central1-c
```
Output
```
NAME: gcelabe2
ZONE: us-central1-c
MACHINE_TYPE: n1-standard-2
PREEMPTIBLE:
INTERNAL_IP: 10.128.0.2
EXTERNAL_IP: 34.66.119.9
STATUS: RUNNING
```
Install nginx
```bash
sudo apt update
sudo apt install nginx -y
ps auxw | grep nginx
```

Create a GCP VM following the [Quicklags interactive tutorial](https://www.qwiklabs.com/focuses/3563?catalog_rank=%7B%22rank%22%3A5%2C%22num_filters%22%3A0%2C%22has_search%22%3Atrue%7D&parent=catalog&search_id=7996439)

## References
* [Windows and containers - Microsoft](https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/)
