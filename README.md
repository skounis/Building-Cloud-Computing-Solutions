# Cloud Computing Foundations
[Cloud Computing Foundation](https://www.coursera.org/learn/cloud-computing-foundations-duke) by Duke University

## Week II
> talent is one aspect, but it's not the most important aspect of an effective team

> If there is no goal, it's really hard to have an effective team

Ideas of what it takes to be effective in terms of a team
1. Clear, Elevating Goal
2. Results-Driven Structure
3. Competent Team Members
4. Unified Commitment (Is everyone on the same page)
5. Collaborative Climate
6. Standards of Excellence 
7. External Support and Recognition
8. Principled Leadership

### Effective Technical Project Management
Learning Objectives
1. Identify primary factors that influence the success of a technical project
2. Cultivating positive team dynamics through transparent and timely communication

Key principles 
* **Quarterly schedule** that identifies week by week what it is that you'll build.
* **Weekly Demo**: _If you can't demo each week you probably not going to hit your deadline_
* The code is **always in a deployable state**.
* **Automated testing**: **If it is not automated, it is broken**
* Tickets sweet spot: 4 hours to 3 days time window
* Avoid the hero, _who jumps in and save the day_ (hero-drived development)
* Kaizen, from Japanese Automobile Industry: Continuous Improvement

Anti-patterns 
1. Hero-Driven development
2. Crisis-Driven development
3. HiPPO-Diven development (Highest-paid person's opinion, e.g CEO. Investor, ...) 
4. Heavy SCRUM: Mimic what appears to be succesful. 
5. Faith in people vs. Faith in process.


> Hope is not a strategy

### Reference 
* [Teamwork: What Must Go Right/What Can Go Wrong (SAGE Series in Interpersonal Communication)](https://www.amazon.com/Teamwork-Right-Wrong-Interpersonal-Communication/dp/0803932901) by Carl Larson (Author), Frank M J LaFasto (Author)


## Week III

### AWS Cloud
Tests:
* Functional
* Integration
* Load

> Linting: Catches bugs before they happen. 

Python Virtual Env:
* Isolates Python to a directory
* Best practice


GitHub Actions
* Continuous Integration: Form of automated testing.
* SaaS based continuous integration server

Sample onboarding scripts and resources 
* https://github.com/noahgift/multi-cloud-onboard

CI: 
* The software is always in a known state
* Saves time

### Azure Cloud
* Unit tests: low level. 
* Integration tests: verify that different modules or services worked well together. 
* Functional tests: Are verifying that the business requirements of an application say a web service returns the right status code. 
* End to end testing: Is a way of mimicking users and how they use the software 
* Acceptance testing: A formalized way of verifying that let's say a payroll application sends out the payments. 
* Performance testing or load testing: Is going to test how the app will perform under load. 
* Basic sanity testing: It verifies that if you also do some exploratory data analysis that you can ensure that things are working properly. 

> How much testing: Just enough to solve the problem. 

Testing Strategy:
* Just right: Not too much, neither too litle. Just enough for knowing what we do works. 
* Judgment: Do you suspect something may be wrong, write the test.
* Save time: The most common mistake developers think of. Do not debug the same code again.
* Automation: 

It is called "Kaizen":
> [Kaizen](https://en.wikipedia.org/wiki/Kaizen) is a concept referring to business activities that continuously improve all functions and involve all employees from the CEO to the assembly line workers. Kaizen also applies to processes, such as purchasing and logistics, that cross organizational boundaries into the supply chain. 

#### Azure resources and futher reading/videos
* https://paiml.com/docs/home/books/cloud-computing-for-data/chapter01-getting-started/#microsoft-azure
* [Azure Cloud Shell - Introduction](https://www.youtube.com/watch?v=rXXtJpcVems)
* [Azure Integration - Scaffold](https://www.youtube.com/watch?v=0IAcF4cfGmI)


### Scaffold Python Project 
For use with Cloud9, Azure and GCP
* https://github.com/skounis/cdf-scaffold


### Google Cloud 
#### Google Cloud resources and futher reading/videos
* https://paiml.com/docs/home/books/cloud-computing-for-data/chapter01-getting-started/#gcp-google-cloud-platform

#### Create a virtual env
```bash
which virtualenv
virtualenv ~/.cdf-scaffold
source .cdf-scaffold/bin/activate
ssh-keygen -t rsa
```

#### Continuous Delivery
> The code is always in a deployable state both in term the application software and the infrastructure. 

#### Build Servers
Some examples:
* GitHub Actions
* Jenkings
* AWS Code Build (Cloud native)

Jobs targeting the code:
* Lint the code
* Test the code
* Deploy the code/application

##### Infrastructure as Code (IaC)
Update or create an environment. It will be mapped to the source control (eg `staging`, `test` or `production` branches). We have ENVs for reach branch. 
Some examples:
* Terraform
* Cloud Formation

#### Continuous Delivery - A real example
* Repo: https://github.com/skounis/cdf-gcp-flask-ml-deploy

Setup
```bash
virtualenv ~./.cdf-gcp-flask-ml-deploy
source ~./.cdf-gcp-flask-ml-deploy/bin/activate
make install
```

Run localy (Cloud ENV):
```bash
python main.py
```

Google Cloud Deploy
```bash
gcloud app deploy
```

#### Cloud Build
1. Create a triger (region europe-west1)
    - https://console.cloud.google.com/cloud-build/triggers;region=europe-west1?project=cdf-cloud-data-cd
2. Configure settings
    - https://console.cloud.google.com/cloud-build/settings/service-account?project=cdf-cloud-data-cd
3. Settings
    - Enable "App Engine": You can do deploys for me
    - Enable "Service Accounts": Do this on my behalf.
4. Make a commit to `master`


## Week IV

### Cloud Computing Service models:

* SaaS: (e.g. Gmail, Splunk, Datadog)
* PaaS: Highlevel abstraction of the infrastructure. The team focus only on the logic of the application. (e.g. Heroku, GAE, Beanstalk ...)
* IaaS: Get things in bulk. You still need to configure everything. (e.g. AWS EC2)
* MaaS: All the cloud principles apply to the physical hardware (GPU programming or Large storage systems)
* Serverless (FaaS): eg AWS Lambda.

Cloud computing:
* Near infinite computing
* Elimination of upfront cost
* Paying for what you use
* Comperative advandage: You focus on things you are good at, leaving the rest to others.


Cloud economics
* Elasticity: Adjust the resources
* Avelabilty: Does the server respond, how many 9s. The services are desinged to be available ans scalable
* Self Service: Work around IT procurement, bureaucracy (e.g. vending machine)
* Reduced complexity: Focus on solving the business problem (not security or network etc, since the cloud ventor takes care)
* Total Cost of Ownership (TCO): Goes down in the long term
* Operational Resiliance: How do we perform on a crisis (e.g. natural disaster in physical server). The application and the infrastrure are designed to handle failures
* Busines Agility: Riding the wave that may crush you if you go against. Leveraging the cloud native resources  

Links and Resources

* https://aws.amazon.com/cloud9/
* https://aws.amazon.com/cloudshell/
* https://cloud.google.com/shell/
* https://docs.microsoft.com/en-us/azure/cloud-shell/overview
* https://learning.oreilly.com/library/view/python-for-devops/9781492057680/ch07.html
* https://www.google.com/docs/about/
* https://www.office.com/
* https://www.heroku.com
* https://aws.amazon.com/lambda/
* https://github.com/noahgift/delivery
* https://github.com/noahgift/gcp-hello-ml
* https://cloud.google.com/appengine/docs/standard/python3/quickstart
* https://cloud.google.com/source-repositories/docs/quickstart-triggering-builds-with-source-repositories
* https://console.cloud.google.com/cloud-build/triggers
* https://cloud.google.com/cloud-build/docs/create-github-app-triggers
* https://github.com/GoogleCloudPlatform/python-docs-samples/tree/master/appengine/standard_python37/hello_world
* [Brief introduction... what is cloud computing](https://www.youtube.com/watch?v=KDWkY0srFpg)
* [Brief introduction to cloud economics](https://www.youtube.com/watch?v=22mtNlfGEc8)
* [Brief intro to cloud computing service models](https://www.youtube.com/watch?v=7lgy7Cnt72c)
* [Setup Continuous Delivery on GCP Platform with Google App Engine and Cloud Build](https://www.youtube.com/watch?v=_TfWdOvQXwU)

### Websites
#### S3
...

#### AWS Lambda
...

#### EC2 
1. Create a `.pem` file and upload it to the Cloud9 environment
2. Create an EC2 Security Group
3. Install `httpd`
```bash
 sudo yum update -y
 sudo yum install -y httpd
 sudo systemctl start httpd
 ```
4. Adjust the `www` content
```bash
sudo usermod -a -G apache ec2-user
sudo chown -R ec2-user:apache /var/www
# add group write permisions
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;
```

The created files within the `html` folder inherit the permissions from the parent` 

#### Elastic Beanstalk
1. Install the [CLI tools on a Cloud9 environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html)
2. Use the install scripts from GitHub https://github.com/aws/aws-elastic-beanstalk-cli-setup

Add `eb` in the path
```bash
echo 'export PATH="/home/ec2-user/.ebcli-virtual-env/executables:$PATH"' >> ~/.bash_profile && source ~/.bash_profile
```

Create a flask app
```bash
mkdir eb-flask
cd eb-flask
# Create Virtual ENV withing the app folder (see comments below)
python3 -m venv virt
source virt/bin/activate
pip install flask==1.0.2
pip freeze > requirements.txt
touch application.py
# Get source from 
# https://github.com/noahgift/Flask-Elastic-Beanstalk
#
# Run localy
python appliction.py
```

Test the app
```bash
curl http://127.0.0.1:5000
curl http://127.0.0.1:5000/echo/foo
```

##### Deploy EB
Ignore
```bash
touch .ebignore
echo "virt" >> .ebignore 
```

Create an EB environmet
```bash
eb init -p python-3.7 flask-cloud-data
eb create flask-cloud-dataenv
```

Terminate the EB environment
```bash
 eb terminate
 ```
### Cloud Computing Economics

Key terms
* Elasticity
* Availability
* Self-Service
* Reduced complexity
* Total Cost of Ownership (TCO)
* Operational resilience
* Business agility: We focus on our business goals 

#### Elasticity
When traffic goes up, automatically deploy more virtual machines so they handle it. Traffic goes down, remove the additional virtual machines and reduce the overall cost. 
> More traffic: Scale up, Less traffic: Scale down

#### Availability
Is the website 99.9999 reliable? We use services that are designed to be available. We do not need to build this infrastructure

#### Self-Service
Work around the IT Procurement. 

#### Reduced complexity
We focus on solving the business problems instead security, network etc that are handeld by the Cloud vendors with significant better experience.

#### Total Cost of Ownership
Invest in our own data center will be more expensive in the **long term** (e.g. having the people for maintaining and running it)

#### Operational resilience
How do we perform in a crisis? When for example, a natural disaster destroys our only data center. A cloud provider has more resources, and we inherit their resilience.  
Our application is designed to take advantage of it.

#### Business agility
> Ride with the wave, not against it. 

We leverage the cloud resources that are constantly being developed and focus on our business expertise. As a result, we develop features at a much faster pace. We do not spend resources on what other people are already doing in a much better way. 

#### Hands on
* https://github.com/skounis/cdf-flask-elastic-beanstalk/blob/main/README.md



## Week V
DevOps key terms
* Continuous Integration: Automated testing process
* Continuous Deliver: Code always in deployable state
* Microservices: Smaller version of an application focus on one particular purpose
* Infrastructure as Code (IaC)
* Monitoring and Logging: There is instrumentation in place.
* Communication and Collaboration

### DevOps
> Replacing siloed Development and Operations to create multidisciplinary teams that now work together with shared and efficient practices
and tools
* Agile planning
* CI/CD
* Monitoring

#### Cylce Time 
> OODA Loop
> Observe, Orient, Decide, Act (repeat) 
1. You start with observation of business, market, needs, current user behavior, and available telemetry data.
2. Then you orient with the enumeration of options for what you can deliver, perhaps with experiments. 
3. Next you decide what to pursue, and you act by delivering working software to real users. 

All of this occurs in some cycle time.
> The feedback that you gather with each cycle should be real, actionable data. This is called **validated learning**.

> How long does it take you to deploy a change of one line of code or configuration? Ultimately, that's the **brake on your velocity**

> "Plans are worthless, but planning is everything." — Dwight D. Eisenhower

> "Everything has dramatically changed. Sustainability, besides green and clean, means that what we build today has to be easily and quickly changed tomorrow. Strategic plans are short-term, and planning and change are continuous." — Diego Lo Guidice, Forrester

##### Done 
> Are you done programming, creating test data, actually testing, ensuring it’s deployable, documenting…

#### Agile Planing
1. Vision: 18 months
2. Season: 6 months (Is described through features and sets the strategy for the next period)
3. Plan: 3 sprints
4. Sprint: 3 weeks

#### DevOps in Real World
> There's a simple heuristic, either on a daily basis you're getting better or you're getting worse. **If you don't know which one, you're probably getting worse**.

#### DevOps Benefits
DevOps: A practice that improves the velocity of the team
1. Spead the software gets to the customers 
2. Delivery: Deliver features and bug fixes faster
3. Reliability: Automated test, monitoring, loging makes systems much more reliable.
4. Scale: IaS and Microservices, the smaller you make something the easier to scale.
5. Collaboration: Shared ownership, Production management, Development and Operations work together.
6. Decurity: Leaking data, sharing data accidentantaly. DevOps increase the lever of security

#### DevOps Best Practices
1. Continuous Integration: Automaticaly testing bugs, improve the quality, reduce the time for validating and releasing.
2. Continuous Deliver: Code ready for realease into production. An extension of the CI.
3. Microservices: Critical component. Small services that communicate with each other with a queuieing syste or othe interface.
4. Infrastructure as Code (IaC): Enables the CI/CD
5. Monitoring and Logging: Look at the metrics (CPU, Memory, I/O load). Look at the data and make decisions. 
6. Communication and Collaboration: 

### Utilize IaC
Manage Cloud Infrastructure. Key terms:
* Infrastructure as Code (IaC): Code that deployes and Infrastructure
* Terraform: A popular IaC
* Environment Drift: IaC stops environments from drifting and changing
* Snowflake Environment: An example when we do not use IaC, automation. A non reproducible environment

#### What is IaC
The management of network, virtual machines, load balancers, connection topology in a descriptive model. 

The same IaC model generates the same environment every time it is applied. 

Teams who implement IaC can deliver stable environments rapidly and at scale. Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code. Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies (see [Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview))

The infracture is checked in alongside of the source code of the project. Enables a repeatable process for deploying and configure the codebase. 

An event, e.g. a push into the `master` branch triggers the build process:
1. Test
2. Lint
3. Deploy. 
4. Prepare and configure the physical infrastructure 
   -  Configure the load balancer
   -  Setting the storage
   -  Create the permissions.


#### IaC in the Real World
You can build the entire company infrastructure from scratch or in a disaster. It is dangerous not to have this in place.


#### GCP: Launch a VM with Terraform
Confirm `terraform` is available/installed
```bash
terraform
```
Output
```text
Usage: terraform [global options] <subcommand> [args]

The available commands for execution are listed below.
The primary workflow commands are given first, followed by
less common or more advanced commands.

Main commands:
  init          Prepare your working directory for other commands
  validate      Check whether the configuration is valid
  plan          Show changes required by the current configuration
  apply         Create or update infrastructure
  destroy       Destroy previously-created infrastructure

All other commands:
  console       Try Terraform expressions at an interactive command prompt
  fmt           Reformat your configuration in the standard style
  force-unlock  Release a stuck lock on the current workspace
  get           Install or upgrade remote Terraform modules
  graph         Generate a Graphviz graph of the steps in an operation
  import        Associate existing infrastructure with a Terraform resource
  login         Obtain and save credentials for a remote host
  logout        Remove locally-stored credentials for a remote host
  output        Show output values from your root module
  providers     Show the providers required for this configuration
  refresh       Update the state to match remote systems
  show          Show the current state or a saved plan
  state         Advanced state management
  taint         Mark a resource instance as not fully functional
  test          Experimental support for module integration testing
  untaint       Remove the 'tainted' state from a resource instance
  version       Show the current Terraform version
  workspace     Workspace management

Global options (use these before the subcommand, if any):
  -chdir=DIR    Switch to a different working directory before executing the
                given subcommand.
  -help         Show this help output, or the help for a specified subcommand.
  -version      An alias for the "version" subcommand.
```
Get available zones and instances
```bash
gcloud compute zones list | grep us-west
gcloud compute images list | grep debian
```

Create a configuration file `instance.tf`
```bash
touch instance.tf
```
Open it in the Editor and add.
```txt
resource "google_compute_instance" "default" {
    project         = "cdf-cloud-data-cd"
    name            = "terraform"
    machine_type    = "n1-standard-1"
    zone            = "us-west1-a"

    boot_disk {
        initialize_params {
          image = "debian-cloud/debian-10"
        }
    }  

    network_interface {
      network = "default"
      access_config {

      }
    }
}
```

Init Terraform
```bash
terraform init
```
Output
```text

Initializing the backend...

Initializing provider plugins...
- Finding latest version of hashicorp/google...
- Installing hashicorp/google v4.36.0...
- Installed hashicorp/google v4.36.0 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

Verify the configuration.
```bash
terraform plan
```

Output
```text
Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # google_compute_instance.default will be created
  + resource "google_compute_instance" "default" {
      + can_ip_forward       = false
      + cpu_platform         = (known after apply)
      + current_status       = (known after apply)
      + deletion_protection  = false
      + guest_accelerator    = (known after apply)
      + id                   = (known after apply)
      + instance_id          = (known after apply)
      + label_fingerprint    = (known after apply)
      + machine_type         = "n1-standard-1"
      + metadata_fingerprint = (known after apply)
      + min_cpu_platform     = (known after apply)
      + name                 = "terraform"
      + project              = "cdf-cloud-data-cd"
      + self_link            = (known after apply)
      + tags_fingerprint     = (known after apply)
      + zone                 = "us-central-a"

      + boot_disk {
          + auto_delete                = true
          + device_name                = (known after apply)
          + disk_encryption_key_sha256 = (known after apply)
          + kms_key_self_link          = (known after apply)
          + mode                       = "READ_WRITE"
          + source                     = (known after apply)

          + initialize_params {
              + image  = "debian-cloud/debian-9"
              + labels = (known after apply)
              + size   = (known after apply)
              + type   = (known after apply)
            }
        }

      + confidential_instance_config {
          + enable_confidential_compute = (known after apply)
        }

      + network_interface {
          + ipv6_access_type   = (known after apply)
          + name               = (known after apply)
          + network            = "default"
          + network_ip         = (known after apply)
          + stack_type         = (known after apply)
          + subnetwork         = (known after apply)
          + subnetwork_project = (known after apply)

          + access_config {
              + nat_ip       = (known after apply)
              + network_tier = (known after apply)
            }
        }

      + reservation_affinity {
          + type = (known after apply)

          + specific_reservation {
              + key    = (known after apply)
              + values = (known after apply)
            }
        }

      + scheduling {
          + automatic_restart           = (known after apply)
          + instance_termination_action = (known after apply)
          + min_node_cpus               = (known after apply)
          + on_host_maintenance         = (known after apply)
          + preemptible                 = (known after apply)
          + provisioning_model          = (known after apply)

          + node_affinities {
              + key      = (known after apply)
              + operator = (known after apply)
              + values   = (known after apply)
            }
        }
    }

Plan: 1 to add, 0 to change, 0 to destroy.

──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run "terraform apply" now.
```

Accept and apply the changes
```bash
terraform apply
```

#### Azure: Launch a VM with Terraform
Use the [instance.tf](https://github.com/skounis/Cloud-Computing-Foundations/blob/main/azure/instance.tf) file and run

Build the platform
```bash
terraform init
terraform plan
terraform apply
```
Links and Resource
1. [Speeding Up Innovation: What I learned from Netflix](https://www.slideshare.net/adriancockcroft/speeding-up-31799721)
2. [Microsoft Learn: What is continuous deliver?](https://learn.microsoft.com/en-us/devops/deliver/what-is-continuous-delivery)
3. [Microsoft Learn: What is Agile](https://learn.microsoft.com/en-us/devops/plan/what-is-agile)
4. [Microsoft Learn: What is Scrum](https://learn.microsoft.com/en-us/devops/plan/what-is-scrum)
5. [Microsoft Learn: Scaling Agine to large teams](https://learn.microsoft.com/en-us/devops/plan/scaling-agile)
6. [Microsoft Learn: What is monitoring?](https://learn.microsoft.com/en-us/devops/operate/what-is-monitoring)
7. [Microsoft Learn: What is Infrastructure as Code (IaC)](https://learn.microsoft.com/en-us/devops/deliver/what-is-infrastructure-as-code)
8. [The Agine Manifesto](http://agilemanifesto.org/)
9. [Scrum is the most common Agile framework](https://learn.microsoft.com/en-us/devops/plan/what-is-scrum)
10. [Cowboy coding](https://en.wikipedia.org/wiki/Cowboy_coding)
11. [What is configuration drift](https://coder.com/blog/what-is-configuration-drift)
12. [Azure Resource Manager](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview)
