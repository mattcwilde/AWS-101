# AWS 102
##### Data Science Studio, UW 
##### November 18, 2019
##### Presented by Rob Farland (UW eScience) and Joel Morgan (Amazon)

---

## Lab

---


AWS has 10x more cores than any  other cloud provider combined. (!!!)

We are running the lab on: https://dashboard.eventengine.run/login

Once you have access, make sure to select your region!! 
 - upper right side of the web console window
 - Oregon region is closest for us

NB: There are many ways to get free credits for instructors (or when you sign up
with your academic email)

### Launching an EC2 Instance
- *Step 1: Choose AMI*
    - preconfigured OS images obptimaized for lots of use cases
    - We are using the AWS Linux 2 
    
- *Step 2: Choose Instance Type*
     - pick how many cores and memory you want
     - we are using `m5a.large`

- *Step 3: Configure Instance Details*
    - see the *Advanced Details section at the bottom*:
        - this text box takes linux commamds 
        - i.e. `pip install anaconda` but need shebang `#!/bin/bash`
        (this didn't seem to work?)
 
- Step 4: Add Storage

- Step 5: Add Tags
    Useful if you have multiple people using the account something like
    Key: Owner
    Value: Name


 - Step 6: Configure Security Group
    - want 22
    - this is whre you pick source. Dont do 00.000.00.0.0 (can log in everywhere)
 
- We use chose `My IP` (so we should only be able to get in from work)
- Can add more rules to be able access from another IP

### after step 7, click `launch`
key pair is the master account. 
You can then create linux users with passwords later


### Once you have an instance:
you can easily stop and change your instance type if you need more cores
for example. Or, start a large instance and install everything, then turn 
it down to a cheaper smaller option to test stuff on it. 

NB: Need to make sure the key file is only accessible to you (chmod 400)
`chmod 400 ~/.ssh/privatekey.pem`

to log in:
`ssh -i ~/.ssh/privatekey.pem ec2-user@ec2-44-228-131-81.us-west-2.compute.amazonaws.com`


After logging in we created a file. Stopped the instance and changed the instance
type and then logged back in and the file is still there. 

Your Public DNS license will change. Use elastic (bottom left) to have a permanent 
address string


#### Creating an Image
Instance (EC2) --> Image (AMI)

Volume (Block Storage) --> Snapshot

#### Snapshots: 
 - cheaper 
 - it is like making a zip of your computer and putting it on S3
 - if you take a subsequent snapshot, it will only put what has changed
 on S3. 
 
 
#### Elastic IP: Will not change
- get Amazon to allocate an elastic IP, name it
- actions -> associate it

---

# AWS Machine Learning Services

---

 - Many built in. 
 - Sagemaker is the most interesting
 