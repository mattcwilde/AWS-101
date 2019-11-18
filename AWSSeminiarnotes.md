# AWS 101 
##### Data Science Studio, UW 
##### November 18, 2019

Presented by Rob Farland (UW eScience) and Joel Morgan (Amazon)
---

*Research*
---
* Each cloud service (AWS, Google, Azure) has different specialties
* ### Cost Estimation
     - cost of cloud vs cost of hardware (cost of Hyak/Epyc)
* ### Cost Management
    - Different ways to access resources, different costs, plusses/minuses
    - don't leave zombies (code you forgot was running and is costing money)
* ### Compute
    - Instance EC2 (computer) 
    - Volume (block storage)
    - Image (how to put the computer away)
    - Snapshot
* ### Storage
    - Block storage
    - Object storage (entire object needs to be moved to a file system to access it)
* ### Services
    - premade services for different objectives
* ### IAM
    - Identity and Access management
    
---
### Introduction to Amazon Cloud and EC2 Overview

- What is AWS? 
    - don't need to build hardware
- Benefits
    - low cost, elasticity and agility, open and flexible, secureity, global reach
     
- Availability zones exist on isolated fault lines, flood plains. 
If you have logical access you dont have physical access (!). For cases where
companies cant go down ever so will still work if ie, mudslides etc. 

- Neat: Westin building in Seattle is a major lynchpin in the entire internet


- ## Compute
    - #### Amazon EC2: 
        - virtual sercice instances in the cloud
        - linux | windows
        - Arm and x86
        - can help moving data in and out
        - Can publish premade images for distributing research
        
        launch an EC2 instances (running or stopped VM) inside an AMI (virtual machine configureation)
        
- What is a virtual CPU (vCPU)?
    - hyperthreading (don't disable by default)
    physical core count = divide by two
    
- Memory and Storage
    - GibiBytes vs Gigabytes  (256 GiB == 275 GB)
    - Storage is independednt of compute
    - you allocate drives known as EBS volumes
    - Max 16 TiB per volume
    - Some instance types provided physically attached (ephemeral) storage

- Resource allocation
    - All resources assigned to you are dedicated to your instance 
    with no 
    overcommitment (except "T" family)
    
- EC2 Nameing
    `c5n.xlaerge` (this very fast system is only 23 cents an hour)
    
    - c = instance family
    - 5 instance generaltoin
    - n = enhanced networking capabilities
    - xlarge = size

- Can choose processor and architecture
- Can use windows, or most of the linux dists (Ubuntu, etc, redhat...) 


- #### What is an Amazon Machine Image (AMI)?
    - can just ssh, install all the things and make and image, 
 or can script this
    - There is an API 
    - Can launch through the comamnd line (AWS Command line) to script this
    
- Lots of options for specific problems. (CPU/GPU/Storage)
    - Elastic graphics can attach to EC2 instance to play around with it
    for a cheaper price
    
- Purchasing options
    - on-demand (pay by the second) - spiky workloads
    - reserved instances (1-3 year commitment) with significant discount
    - Spot instances (spare EC2 capacity for super cheap) Fault-tolerant, 
    flexible, stateless workloads (way cheaper but you may get outbid)
    
    
- Console vs cli vs api
    - console is logging in with a web browser
    - cli is command line access `aws ec2 run-instances`
    - API

- "houseplants vs crops":
    - get lots of little VMs instead of worrying about a single big specialized one
    
- Hibernate Amazon EC2 Instances
    - just like closing and opening your laptop
      
      
      
#### EC2 Security Groups
- Port 22 = SSH need to be open if you want to talk to your machine
- Port 80 = HTTP

- Be careful! If you accidentally git commit an access key, bots will
instantly find it and get into your account and buy really expensive cpus

- AWS is very kind about refunding when people screw up and leave things
running (even if the students in the lab do it).

- Key is only needed for you to get to EC2, then everyone else just needs a 
linux user profile

