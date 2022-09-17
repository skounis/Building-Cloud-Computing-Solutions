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
> The feedback that you gather with each cycle should be real, actionable data. This is called *validated learning*.

