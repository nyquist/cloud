# Building with AWS

### Instances, AZs, Regions

EC2 instance runs on a physical server in an AWS facility The physical server is called a host A hypervisor mediates access between your code and the underlying server and provides isolation from other workloads

A host is phyiscially located in an availability zone (AZ). An AZ is a logical grouping of Data Centers

Two or moer AZs are part of a Region.

Region identifiers end in numbers. `us-west-2` AZ idnetifiers end in letters: `us-west-2a, us-west-2b`

Each region has it's own API Endpoint.

An EC2 instance is bound to an AZ so you have to specify it at creation time. Other resources are regional in scope, while others are global.

### Networking

* VPC = Virtual Private Cloud
* A VPC has regional scope
* A VPC contains multiple subnets.
* A subnet has AZ scope
* An EC2 instance is launched in a subnet
* By default traffic is allowed between subnets
* Internet gateway is a type of connection that can be opened on an VPC.
* A rule (route) needs to be added to allow access from the internet to our "public" subnet. Note that the public here means a subnet with private IP addresses that is intended to be accessed from the internet

#### EC2

* To view the log file, type the command below in your instance terminal.

`cat /var/log/cloud-init-output.log`

Explore the log file to see the log entries generated for installing the user data script.- To view the instance metadata, type the command below:

`curl http://169.254.169.254/latest/meta-data/`

* Execute the command below to get the instance identity document of your instance:

`curl http://169.254.169.254/latest/dynamic/instance-identity/document`

* Execute the command below to get the instance public IP address:

`curl http://169.254.169.254/latest/meta-data/public-ipv4`

* Execute the command below to get the MAC address of the instance:

`curl http://169.254.169.254/latest/meta-data/mac`

* Execute the command below to get the VPC ID in which the instance resides. Make sure to replace **Your-MAC** in the command below with the MAC address of your instance:

`curl http://169.254.169.254/latest/meta-data/network/interfaces/macs/Your-MAC/vpc-id`

* Execute the command below to get the subnet-id in which the instance resides. Make sure to replace **Your-MAC**in the command below with the MAC address of your instance:

`curl http://169.254.169.254/latest/meta-data/network/interfaces/macs/Your-MAC/subnet-id`

* Execute the command below to get the instance user data:

`curl http://169.254.169.254/latest/user-data`
