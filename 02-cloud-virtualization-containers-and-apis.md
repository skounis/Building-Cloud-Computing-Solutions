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

Common commands
```bash
gcloud auth list
gcloud config list project
gcloud compute instances create gcelab2 --machine-type e2-medium --zone 
gcloud compute instances create --help
gcloud compute ssh gcelab2 --zone  
```


#### Azure ML Studio
* https://ml.azure.com/

In general, there's 
* Compute Instance, which is for Jupyter Notebooks. 
* Compute Clusters, which is for bursting and doing training, 
* Inference Clusters, which is an optimal environment for doing predictions at scale, not using hosted Kubernetes.

### Containers
A powerfull way to package the runtime along with the source code of the project.

Containers registries:
* Docker Hub 
* Amazon ECR

#### When to use containers
* Cloud-native environments. The simplest possible way to deploy and application.
* Microservices. Very efficient and simple way to solve a problem.
* DevOps. Reproduce the env as well as the source code. Build programmaticaly the container. IaC
* Job management. Use containers to manage workflows
* Portability and usability. DevOps and Data Sciences. Inside the source code lives the runtime. 

#### Docker
Docker: Docker Desktop and Docker Hub. 
* Docker desktop: 
    * Local development workflow: Container runtime, tools, application, interface with Kubernetes
* Docker Hub
    * Public and private repocitories / registries
    * Automate the build 
    * Certify the images
    * Teams and organizations.
##### Docker Desktop
* Use Official images and leverage the existing knowledge. 
* Build new container localy and push it in the Docker Hub
* Pull the image and deploy or onboard new developers. 

> Leverage the power of an expert developer in a runtime. 

#### Run a container
Example
* https://hub.docker.com/r/jupyter/datascience-notebook

```bash
docker pull jupyter/datascience-notebook
```

Open the app (url) and create a new notebook:
* http://127.0.0.1:10000/lab/tree/Untitled1.ipynb

```python
import pandas as pd                 
df = pd.read_csv("https://raw.githubusercontent.com/noahgift/sugar/master/sugar.csv")
df.describe()
df.plot()
```

#### Build a Docker container 
Example 
* https://github.com/noahgift/container-from-scratch-python

Work in Cloud9
```bash
git clone git@github.com:skounis/cdf-container-from-scratch-python.git
cd cdf-container-from-scratch-python

# Run
docker run -it noahgift/cloudapp python app.py --name "Big John"
```
Runs the `app.py` from the container

##### Build a local container
```bash
docker build --tag app .
# Get the list of images
docker image ls
# "app" is listed as the name of the most recently created one
# Run it
docker run -it app python app.py --name "Big John"
```

#### AWS ECR Registry
Push a container in ECR.

1. Build a container registry is ECR 
     - Create a new repository in the [Elastic Container Registry ](https://eu-west-1.console.aws.amazon.com/ecr/). e.g. `cdf-container` 
     - Check out the [sample project](https://github.com/skounis/cdf-container-from-scratch-python) in Cloud9 
     - Use the shell commands:
```bash
# Login
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 825556157514.dkr.ecr.eu-west-1.amazonaws.com
# Build the container
docker build -t cdf-container .
# Tag the image 
docker tag cdf-container:latest 825556157514.dkr.ecr.eu-west-1.amazonaws.com/cdf-container:latest
# Push to the registry
docker push 825556157514.dkr.ecr.eu-west-1.amazonaws.com/cdf-container:latest
```

2. Use the image from ECR
    - Create a new Cloud9 Env
    - Login into ECR (use the same command as above)
    - Pull the container. Use the id of the docker push command above


```bash
# Login
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 825556157514.dkr.ecr.eu-west-1.amazonaws.com
# Pull
docker pull 825556157514.dkr.ecr.eu-west-1.amazonaws.com/cdf-container:latest
# Run the application 
docker run -it 825556157514.dkr.ecr.eu-west-1.amazonaws.com/cdf-container:latest python app.py --name "Big John"
```

#### Dockerfile lint
With `hadolint`:
```bash
hadolint Dockerfile
```
### Kubernetes
* Powerfull orchestration service for containers
* Highly available solutions

Use via
* Docker Desktop
* `kubectl` cli

Cloud services
* Amazon EKS
* Google Kubernetes Engine GKE
* Azure Kubernetes Service (AKS)

Keys features
* High availability architecture
* Auto-scaling
* Rich ecosystem
* Service discovery
* Container health management
* Secrets and configuration management


Architecture / Hierarchy

* Node
  * Pod (IP Address)
    * Container

Master: Orchestrates through API

#### Killer feature
* Auto scaling 
* Horizontal Pod Autoscaler
  * HPA Control Loop (~15 secs)
  * Help metrics: CPU, Memory
  * Provisions more Pods
* Job management
  * Are listening to what is happening (metrics)
  * Scale things up and down

> [Cloud Computing for Data Analysis](https://paiml.com/docs/home/books/cloud-computing-for-data/)
>
> [Chapter3: Virtualization & Containerization & Elasticity: Kubernetes](https://paiml.com/docs/home/books/cloud-computing-for-data/chapter03-virtualization-containers-elasticity/#kubernetes)


Video Tutorials
* [Deploy Kubernetes GKE](https://www.youtube.com/watch?v=5pTQJxoK47I)
* [Running Kubernetes locally on OS X with a Flask sklearn application](https://www.youtube.com/watch?v=LcunlZ_T6Ks)
* [Demo Application and container](https://github.com/noahgift/container-revolution-devops-microservices)





## Week III
### Microservice 
* DevOps best practices in Microservices
* Different types of microservice architectures (e.g. event driven) 
* Serverless. No need to privision machines or work with their low level details. (AWS Lambda, Google Cloud Functions, Azure Functions). Event Driven and Cloud native.

#### What is a Microservice
* Small. Does one thing and does it well.
* Autonomous
* Specialized. Can do a particular task desinged to gracefully handle errors.

Benefits
* Speeds ups the development. Small codebase
* Simplicity 
* Maps logic into a particular URL. (e.g. a functions that maps to a URL or an event)
* Reliability 

#### Where do Microservices run
* Container
    * Service
    * Kubernetes
* Cloud
    * Functions (Function as a Service, FaaS)
    * Platforms (Elastic beanstalk, Google App Engine, etc)  

#### Microservices in action
>  [GitOps: A Path to More Self-service IT](https://queue.acm.org/detail.cfm?id=3237207)
>
>  GitOps: empowering users to do their own IT operations via PRs.

> By starting with many manual checks and automating issues only as demand directs your attention, low-value work is discouraged. As stated in books such as The Goal (by Eliyahu M. Goldratt, 1984) and The Phoenix Project (by Gene Kim, Kevin Behr, and George Stafford, 2013), it is best only to expend effort directly at the bottleneck: improvements upstream of the bottleneck simply create a bigger backlog; improvements downstream of the bottleneck are premature optimizations.


> To recap, a GitOps system evolves like this:
> 
> 1. Basic — configs in repo as a storage or backup mechanism.
> 2. IaC — PRs from within the team trigger only CI-based deployments.
> 3. GitOps — PRs from outside the team, pre-vetted PRs, post-merge testing.
> 4. Automatic — Eliminate the human checks entirely.


> While it may take a senior engineer to set up the initial system, automating tests is a good way for junior engineers to build up experience. Thus, GitOps creates mentoring and growth opportunities.

Metrics Dashboards 
* https://cloud.google.com/products/operations
* https://grafana.com/
* https://prometheus.io/


Some real examples:
* [Alerts and monitoring] https://www.youtube.com/watch?v=xrXjgtOSX6o
* [Five Whys method](https://www.youtube.com/watch?v=9jS3cwjIJEo)
* [Continuous improvement](https://www.youtube.com/watch?v=9jS3cwjIJEo)
* [Use prometheus](https://www.youtube.com/watch?v=4bcBS1G3GWI)

### Flask
* lightweight web framework
* the most popular framework in Python as of 2020
* maps a function in Python to a web URL route.

#### Real Flask Microservice
* https://github.com/skounis/cdf-flask-change-microservice

Checkout `main` in a GitHub codespace
```bash
# Install depedencies 
make install
# Install interactive python
pip install ipython
```

Start and use the intective shell
```bash
ipython
```
```
from app import change
change(1.34)
```
Out
```
Out[3]: [{5: 'quarters'}, {1: 'nickels'}, {4: 'pennies'}]
```

Test the routes locally:
```bash
# Start listening
python app.py
```
Open browser from Codespaces prompt and follow the path `/change/1/34`

#### Flask Microservice in Azure
Open the shell and checkout the repo
* https://github.com/skounis/cdf-python-docs-hello-world

Create a virtual environment
```bash
# Create 
python3 -m venv venv
# Activate
source venv/bin/activate
# cd into the folder and
# Install the requirements 
pip install -r requirements.txt 
# Run
python app.py
```
> Nothing happens 

```bash
export FLASH_APP=app.py
flask run
```
Output
```
(venv) stavros [ ~/cdf-python-docs-hello-world ]$ flask run
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:5000
Press CTRL+C to quit
```

##### Deploy the application
```bash
az webapp up --sku F1 -n hellopyworld
```
Output
```
(venv) stavros [ ~/cdf-python-docs-hello-world ]$ az webapp up --sku F1 -n hellopyworld
The webapp 'hellopyworld' doesn't exist
Creating Resource group 'skounis_rg_8304' ...
Resource group creation complete
Creating AppServicePlan 'skounis_asp_3541' ...
Creating webapp 'hellopyworld' ...
Configuring default logging for the app, if not already enabled
Creating zip with contents of dir /home/stavros/cdf-python-docs-hello-world ...
Getting scm site credentials for zip deployment
Starting zip deployment. This operation can take a while to complete ...
Deployment endpoint responded with status code 202
BuildRequestReceived...          Success! 
BuildPending...                  Success! 
BuildInProgress...               Success! 

Your application is running.

You can launch the app at http://hellopyworld.azurewebsites.net
Setting 'az webapp up' default arguments for current directory. Manage defaults with 'az configure --scope local'
--resource-group/-g default: skounis_rg_8304
--sku default: F1
--plan/-p default: skounis_asp_3541
--location/-l default: centralus
--name/-n default: hellopyworld
{
  "URL": "http://hellopyworld.azurewebsites.net",
  "appserviceplan": "skounis_asp_3541",
  "location": "centralus",
  "name": "hellopyworld",
  "os": "Linux",
  "resourcegroup": "skounis_rg_8304",
  "runtime_version": "python|3.7",
  "runtime_version_detected": "-",
  "sku": "FREE",
  "src_path": "//home//stavros//cdf-python-docs-hello-world"
}
(venv) stavros [ ~/cdf-python-docs-hello-world ]$ 
```

Visit
* http://hellopyworld.azurewebsites.net

Add a new route
```python
@app.route("/marco/<polo>")
def marco(polo):
    return "%s" % polo
```

Test locally 
```bash
flask run
```
Visit in browser the path `/marco/polo`

Re-deploy
```bash
az webapp up
```
Visit
* https://hellopyworld.azurewebsites.net/marco/polo

### Serverless Microservice 
* Functions serve as an event that trigers the execution
* Serverless functions are listening to events 

### Build on AWS
* Create a new lambda functions https://eu-west-1.console.aws.amazon.com/lambda/home?region=eu-west-1#/functions
   * Set name 
   * Select `Python 3.9`
   * No other settings
* Edit the code: Visit the "Code tab"
   * Deploy it
* Test it: Visit the "Test tab"



## References
* [Windows and containers - Microsoft](https://learn.microsoft.com/en-us/virtualization/windowscontainers/about/)
* [Quicklags interactive tutorial](https://www.qwiklabs.com/focuses/3563?catalog_rank=%7B%22rank%22%3A5%2C%22num_filters%22%3A0%2C%22has_search%22%3Atrue%7D&parent=catalog&search_id=7996439)
* [Chapter3: Virtualization & Containerization & Elasticity: Kubernetes](https://paiml.com/docs/home/books/cloud-computing-for-data/chapter03-virtualization-containers-elasticity/#kubernetes)
* [Play with Kubernetes](https://labs.play-with-k8s.com/)
* [Book: Containerize your Apps with Docker and Kubernetes
 `free`](https://github.com/PacktPublishing/Containerize-your-Apps-with-Docker-and-Kubernetes)
 * [Kubernetes Learning Path `Microsoft`](https://azure.microsoft.com/en-us/resources/kubernetes-learning-path/)
 * [locust.io - An open source load testing tool.](https://locust.io/)
 * config management system such as Puppet or Chef.
     * [Puppet](https://puppet.com/)
     * [Chef](https://www.chef.io/)
