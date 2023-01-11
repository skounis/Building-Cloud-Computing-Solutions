# Cloud Data Engineering
[Cloud Data Engineering](https://www.coursera.org/learn/cloud-data-engineering-duke/home/week/1) Duke University

## Week I
### Overview - Welcome to the course
* Create pipelines
* Serverless
* Batch or Streaming
* Big data
* ETL Pipelines

#### Objectives
* Data Engineering Applications in the Cloud
* Best practices with regard to end of the Moors law
* Best practices for big data solutions

#### Resources
* [AWS Academy](https://aws.amazon.com/training/a`wsacademy/) 
* [Google Qwiklabs](https://go.qwiklabs.com/)
* [Microsoft Learn](https://learn.microsoft.com/en-us/training/)
* [AWS and Lambda - Beginner’s Guide to Writing AWS Lambda Functions in Python](https://github.com/noahgift/awslambda)

#### Project overview
Serverless Data Engineering Pipeline
* Timer kicks off a serverless job - CloudWatch Timer
* Producer Lambda pulls from Serverless Database - DynamoDB
* A queue gets data - SQS 
* Consumer Lambda is listening for SQS events
* Sentiment Analysis - AWS Comprehend
* Store - S3 

### End of Moore's Law

#### Objectives
* Approaches to concurrency. Network, Process, GPU
* Chip types. 
* ASIC use cases: Application Specific Integrated Circuit
* CUDA: Compute Unified Device Architecture, an API for NVidia

#### Python and Concurrency
* Python locks the threads to one core - GIL
* Use the cloud for building a concurrent system. AWS Lambda and SQS


#### The end of Moore's Law
> The end of growth of single program speed really occurred right around this period of the last 40 years. 
> -- Dr. David Paterson 

* CPU is designed to do a lot of things. A general purpose unit
* GPU is desinged to do things in parallel
* TPU is designe for parallelization for a specific workload

#### CUBA and Numba
https://numba.pydata.org/

Notes and links
https://github.com/noahgift/cloud-data-analysis-at-scale/blob/master/topics/end-of-moores-law.md

Google Colab: https://github.com/noahgift/cloud-data-analysis-at-scale/blob/master/GPU_Programming.ipynb


#### What is ASIC
Application specific integrated circuit. Chip for a purpose. Designed for one thing/purpose
* TPU: Tensor procesing unit.
* GPU: Graphics programming - Very parallel operations
* NCS: Intel Neural Compute Stick


#### Taking Advantage of Colab Pro
Profesional version of Colab

#### The End of Moore's Law
From 
* https://noahgift.github.io/cloud-data-analysis-at-scale/topics/end-of-moores-law.html

References
* https://storage.googleapis.com/nexttpu/index.html
* Step by step example: Just in Time compiler (JIT) or a GPU using a library like numba and a hosted runtime like Google Colab.
    * https://github.com/noahgift/cloud-data-analysis-at-scale/blob/master/GPU_Programming.ipynb
    

### Building Distributing Systems
#### Introduction
* Instumentation
* CAP Theorem
* Amdahl's Law
* Elasticity: Response to higher load 
* Highly available: Respond to a request despite the increased trafic 
* Debuggin Python

Objectives
* Develop distributed systems that apply software engineering best practices

#### Logging and Instrumentation Distributed Systems
* Crytical component
* Data sciense fro software engineering
* You know what is happening with the system
* Look at all the logs in a centralized location


#### CAP Theorem
> Trade off between consistency, availability and fault-tolerance

* Consistency: The same data is received for every requuest
* Availability: Every request receives healthy responce
* Fault-tolerance: The system continuous to function as messages drop between nodes

We could have 2 of the 3

* Relational databases: Are very consistent but they do not scale without Replicas. Replicas are highly available in exchange of consistency. They need some time to get syncronized 
* Key-value databases: They do scale but are not consistent. Used in the case where consistency is not the highest priority. 


#### Amdahl's Law
>  diminishing returns that occur with parallelization

Python in particular has the global interpreter Lock or Gil, which eliminates the ability to distribute amongst many cores

After a certain threshold the gain in spead is not proportional to the computational power you use. 

Most of the code is not purely parallel. 

#### Elasticity
> Scale up or scale down automaticaly based on the load. Elasticity is about money


#### Highly Available Nine Nine's
Related terms: Highly available, uptime orservice level agreement. 

* 99.999: Daily: 0.86s of downtime - https://uptime.is/
* Amazon S3: 11 nines (99.999999999%) durability.

#### Debugging Python Code
Testing topics:
* Buyild systems
* Tools
* Debugging
* Continuous deliver


##### Build systems
* SaaS (GitHub actions)
* Open Source (Jenkins)
* Cloud-native (AWS Code Build)

##### Tools
* pylint (check syntax, suggests best practices) 
* Python black (formating tool)
* AWS Code Guru (AI suggestion for code changes)

##### Debugging
* print statements
* PDB The Python Debugger - https://docs.python.org/3/library/pdb.html
* Testing

##### Continuous Delivery
* SaaS (GitHub Actions)
* GCP (Cloud Build) 
* AWS (Elastic Beanstalk)

> The code is constantly deployed and is always in a working state


#### Hands on - GitHub
* https://github.com/skounis/cdf-advanced-testing-techniques
* https://github.com/noahgift/advanced-testing-techniques

##### Steps
1. Use Codespaces
2. Scaffold the files
3. Create a Python Virtual ENV
4. Populate the `Makefile`
5. Set requirements and isntall them `make install`


Scaffolding
```bash
touch Makefile
touch requirements.txt
touch hello.py
touch test_hello.py
```

Virtual ENV
```bash
# Create
virtualenv ~/.advanced-testing
# Activate
source ~/.advanced-testing/bin/activate
```

Makefile
```
install:
	pip install --upgrade pip &&\
		pip install -r requirements.txt

test:
	python -m pytest -vv --cov=hello --cov=hellocli test_hello.py

lint:
	pylint --disable=R,C hello.py 

all: install lint test
```

Requirements
```
pylint
pytest
pytest-cov
click
flask
```
##### Debug
* Print - https://github.com/skounis/cdf-advanced-testing-techniques/releases/tag/v0.0.1
* pdb - Interactive debuggin in console (`n`: next, `variable|statement`: evaluate) - https://github.com/skounis/cdf-advanced-testing-techniques/releases/tag/v0.0.2
* Testing


### Introduction to Big Data

#### Introduction
* What is Big Data
* Their three V's: Velocity, Variety, Volume
* Data lakes
* Big Date processing: Tools (Spank, MapReduce)
* Data feedback loop: Understand the data and get better analytics 
* Use EMR Spark for running parallel jobs

##### Objectives
* Evaluate best practices for Cloud solutions with Big Data

#### What is Big Data
* Can't fit in a Laptop
* You need x10 times the amount of RAM as the dataset. For 10GB data you need 100GB RAM
* Tools Spark, Athena, other big data toolset that distribute the load among diferent machines.
* You need the right tool for the right job.

#### The Three V's of Big Data
* Challenges
 * Valiety: CSV, Binary or SQL files, key-value databases etc. 
   * Tools for combine or extract eg AWS Glue  
 * Velocity: >10K request/second a threashold for approaching big data.
 * Volume: terabytes for petabytes of data need specialized tools and resources (CPU, RAM, Disk space)
   * Process on batches or streaming. Streaming increases the complexity
   * Tools for working with batches: AWS Glue, AWS Data Pipeline, AWS Batch, and EMR
   * Tools for working with streaming: Kinesis, IoT, and Spark EMR

#### Data Lakes
* Data all flows in
* Data can be processed in the same spot where the data lives
* S3 fits the bill since it
  * Is highly available and reliable
  * Scales up infinitely
  * Provides direct access for analytics and dashboard tools
  * Can be usid for real-time stream processing
  * Can be synchronized with any in-premises datacenter. 

> We do not move data aroung. We work with them where they are.

#### Big Data Processing
* Historical data: Dashboard for sales
* Real-time eg ad-bidding or streaming
* Future: Prediction and forecasting (ML)

#### Data Feedback Loop
* Users 
* Users generate data 
* These become big data
* AI/ML/Deep Learning: Analytics and Predictions 
* Create products
* Product targets the Users 


#### Using EMR Spark to Run Parallel Jobs
Start with [AWS EMR](https://eu-west-1.console.aws.amazon.com/elasticmapreduce/home?region=eu-west-1#)
* Create a Notebook  
   *  https://eu-west-1.console.aws.amazon.com/elasticmapreduce/home?region=eu-west-1#create-notebook:
   *  Select to create a cluster
   *  Leave all the rest as default
* Create a spot instance cluster
   * Select "Advanced options"
   * Enable JupyterHub and Spark   
   * Go next
   * Select "Instance fleet" 
   * Select 1 master, 8 core and 20 Task spot instances. (select spot for all)  

Hadoop distributed file system 

Terminate instances from the "Spot Requests" option
* https://eu-west-1.console.aws.amazon.com/ec2/home?region=eu-west-1#SpotInstances:


Pyspark.py
* https://gist.github.com/noahgift/f3adcea4d02742939d3dd327e0af7eb1


## Week II
### Introduction to Data Engineering
* Batch vs Streaming vs Events
* CLI tools with `Click` (python)
* Containerized CLI Tools
* Advanced Testing Techniques
* Map functions to CLI

#### Objectives
* Analyze best practices 
* Apply best practices in CLI tools
* Build Python CLI tools with `Click` 

#### What is Data Engineering:
* build pipelines that transport data or transform data at a periodic basis
* A data engineer is focused exclusively on the software engineering best practices around the movement and transport of data.

Concepts:
* Batch. e.g. nightly jobs
* Streaming. Data are constantly updated, e.g. Stock Ticker
* Events. Prefered way, e.g. handle files after we upload them to S3

### Command line tools
* Github Codespaces, Actions CI/CD
* Docker 

Reference repo
* https://github.com/noahgift/codespace-devops

Process, see:
* https://github.com/skounis/cdf-codespace-devops/releases/tag/v1.0.0

### Containerized CLI
Reference
* https://github.com/noahgift/container-from-scratch-python

We can package the runtime into a container's CLI. A way to distribute CLI tools.

Process, see:
* https://github.com/skounis/cdf-codespace-devops/releases/tag/v1.1.0

### Build a CLI
```bash
# Get into the project's folder
cd /home/coder/project
# Install Virtualenv
python3 -m pip install virtualenv
# Create a Virtual Environment
/home/coder/.local/bin/virtualenv VENV
# Source the virtualenv (activate it):  
source VENV/bin/activate
```

#### app.py
Note the comment in the 1st line which makes the `app.py` executable.
```python
#!/usr/bin/env python
import click

def change(amount):
    # calculate the resultant change and store the result (res)
    res = []
    coins = [1, 5, 10, 25]  # value of pennies, nickels, dimes, quarters
    coin_lookup = {25: "quarters", 10: "dimes", 5: "nickels", 1: "pennies"}

    # divide the amount*100 (the amount in cents) by a coin value
    # record the number of coins that evenly divide and the remainder
    coin = coins.pop()
    num, rem = divmod(int(amount * 100), coin)
    # append the coin type and number of coins that had no remainder
    res.append({num: coin_lookup[coin]})

    # while there is still some remainder, continue adding coins to the result
    while rem > 0:
        coin = coins.pop()
        num, rem = divmod(rem, coin)
        if num:
            if coin in coin_lookup:
                res.append({num: coin_lookup[coin]})
    return res

@click.command()
@click.option(
    "--amount",
    prompt="Amount: ",
    help="Creates change for dollar and cents value:  i.e. 1.34",
)
def make_change(amount):
    """Gives Correct Change"""

    result = change(float(amount))
    click.echo(click.style(f"Change for {amount}:", fg="red"))
    for correct_change in result:
        for num, coin in correct_change.items():
            click.echo(click.style(f"{coin}: {num}", fg="green"))

if __name__ == "__main__":
    # pylint: disable=no-value-for-parameter
    make_change()
```

#### Other files
Makefile
```
install:
	pip install --upgrade pip &&\
		pip install -r requirements.txt

lint:
	pylint --disable=R,C app

test:
	pytest -vv --cov-report term-missing --cov=app test_*.py

format:
	black *.py
```

requirements.txt
```
pylint==2.7.2
click==7.1.2
black==20.8b1
pytest==6.2.
pytest-cov==2.11.1
```

test_app.py
```python
from app import change


def test_change():
    assert [{5: "quarters"}, {1: "nickels"}, {4: "pennies"}] == change(1.34)
```
