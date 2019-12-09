#  Gorilla Time off Management 


## Create an Amazon's EC2 Instance

Amazon's EC2 is easy to create. It also provides a free tier options for 1 year which is cost efficient for my need. AWS  has automated preconfigured images which can be launched with few click. 

## RHEL as a platform

I have decided to use Red Hat Enterprise Linux as a platform for this project because Redhat Linux is supported by wide application manufacturers. Red hat also provides  the best support out of many linux distros. There are certifications you can get for RHEL. In addition, my  familiarity with RHEL made it easier to  choose RHEL as a server for running the application.

## Installation
* Create an AWS account
* Login to the AWS account
* Click on EC2 dashboard and launch instance
* Select Red Hat Enterprise Linux 8 64 bit
* Ensure the instance is General Purpose Free tier eligible 
* Review and Launch
* Create a a key pair and download it. 
* Acknowledge and Launch Instances

## Connecting to RHEL instance
* Select Running insance on AWS management console
* Select your instance and click on Connect tab
* Copy 'ssh -i "yourkeypair.pem" ec2-user@ec2-3-17-26-31.us-east-2.compute.amazonaws.com'
* On your host bash terminal, run the command to prvent the key from being publicly viewable.
    chmod 400 yourkeypair.pem 
* Run ssh -i "yourkeypair.pem" ec2-user@ec2-3-17-26-31.us-east-2.compute.amazonaws.com' to SSH into your EC2 instance. 


## Installing node.js and NPM on RHEL
run the following commands
* $sudo yum update 
* curl –sL https://rpm.nodesource.com/setup_10.x | sudo bash -
* sudo yum install –y nodejs  
* node –version //verify node is installed 
* node -version  // verify npm is installed
    Install Node.js developement tools and libraries
* sudo yum install -y gcc-g++ make 


## Installing TimeOff Management application 
* sudo yum install git
* git clone https://github.com/timeoff-management/application.git timeoff-management
* cd timeoff-management
* npm install

Note: Before you run the command below, ensure port TCP port 3000 allowed on security group corresponding the ec2 instance is allowed on 

* On the AWS management console, select  Red Hat Linux Instance.
* Select the highlighted Security Group corresponding to the instance
* Under Inbound, edit and add a rule as 
    'Type Custom TCP Rule' , Port Range 3000 and Source 'Anywhere / your IP' 
Note: ensure SSH inbound rule is unchanged. 

On the SSH terminal, run the command

* npm start


## Run the application on your web browser
 * Copy the IPv4 Public IP of your EC2 instance
 * on your broswer, type
    http://ec2-ipv2-public-ip:3000/

Now you can login and make changes to your calendar. Request leave or make any changes necessary. 












 




