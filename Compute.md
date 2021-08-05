## Domain 1: Design Resilient Architectures 
  ### 1.1 Design a multi‐tier architecture solution 
  ### 1.2 Design highly available and/or fault‐tolerant architectures 
  ### 1.4 Choose appropriate resilient storage 
## Domain 2: Design High‐Performing Architectures 
  ### 2.1 Identify elastic and scalable compute solutions for a workload 
  ### 2.2 Select high‐performing and scalable storage solutions for a workload 
## Domain 3: Design Secure Applications and Architectures 
  ### 3.1 Design secure access to AWS resources 
## Domain 4: Design Cost‐Optimized Architectures 
  ### 4.1 Identify cost‐effective storage solutions 
  ### 4.2 Identify cost‐effective compute and database services 
  ### 4.3 Design cost‐optimized network architectures

## EC2

Image types and why
* Quick start AMIs - (always up to date and officially supported) - **common every day**
* AWS marketplace AMIs - (provided and supported by industry vendors like SAP Cisco) - **specialised** 
* Community AMIs - (maintained by independent vendors) - **specific need**, planning an application built on a custom combination of software resources
* Private AMIs - (You store) - you've found/created a reliable tested and patched AMI that makes autoscaling easy

EC2 types and why
* General purpose - **M and T series**. M good for small to mid sized data centric operations where many come with their own built in storage.
T is burstable and good for accumulating CPU credits for high demand periods (feast and famine approach)
* Compute Optimised - **C series**. High end machine learning and web servers
* Memory optimised - **X and R series**. Data intensive or analysis type workloads as much as 3.9 terabytes of DRAM available
* Accelerated Computing - **G, P and F series**. P series come with GPGPUs (general purpose graphics processing unit). F series comes with FPGA (field programmable gate array)
* Storage optimised - **H, I and D series**. Low latency large storages volumes. Good for distributed file systems and heavyweight data processing

Note: terminating instances destroys data unless using EBS
Note: new instances have new IPS unless you use an elastic IP address
Note: security groups for instances can be changed at runtime
Note: changes to instance type and resource limits requires a restart

Resource Topology
* Region - close to your use case. Controls visibility or resources
* Availability Zones - at least 2 per region  
* VPC - network organisers. Great for separating environments
* Tenancy Model - shared (default) vs dedicated, isolated (done via tags)

Placement Groups
* Cluster - each instance in single availability zone. Instances in same cluster node have close physical proximity to 
  each other. Good for Low latency 
  network good for high performance compute
* Spread - each instance on separate hardware rack to reduce risk of failure related data or service loss. Good for 
  small number of critical instances that cannot tolerate multiple concurrent failures and must be separate from each 
  other. Max 7 instances per availability zone
* Partition - (new) each instance runs on separate partition. Partitions have their own set of racks, so partitions do 
  not share resources. Instances within partitions may share resources. Good for large distributed workloads. Max 7 
  partitions per availability zone. Max instances per partition depends on your account
  
Instance Pricing
* on-demand (OpEx) - billed per hour, most expensive, most flexibility. Good for short term, low availability
* reserve instance (CapEx) - Billed upfront, 1-3 year contracts or partial (upfront and then monthly), Good for high availability
* spot instance - (OpEx) - cheapest (up to 90% discount), enter maximum dollar-value bid for instance type in region, next time instance 
  available in that region for that price or below you'll get it. Good for flexible applications like data processing, CI/CD pipelines.
  Can be combined with on-demand and reserve instances. Can be created by you or automatically by AWS as part of an EC2 fleet configuration

Resource Tags
* key value pairs to group resources for easier administration
* use a good naming convention e.g. Key: production-server, Value: server1, Key: staging-server, Value: server1

Service Limits
* limit number of instances of particular service that can launch
* can be regional or global

Questions

You need to deploy multiple EC2 Linux instances that will provide your company with virtual private networks (VPNs) using 
software called OpenVPN. Which of the following will be the most efficient solutions? (Choose two.) 
* A Select a regular Linux AMI and bootstrap it using user data that will install and configure the OpenVPN package on the instance and use 
it for your VPN instances. 
* B Search the community AMIs for an official AMI provided and supported by the OpenVPN company. 
* C Search the AWS Marketplace to see whether there's an official AMI provided and supported by the OpenVPN company. 
* D Select a regular Linux AMI and SSH to manually install and configure the OpenVPN package. 
* E Create a Site‐to‐Site VPN Connection from the wizard in the AWS VPC dashboard.

The sensitivity of the data your company works with means that the instances you run must be secured through 
complete physical isolation. What should you specify as you configure a new instance? 
* A Dedicated Host tenancy 
* B Shared tenancy 
* C Dedicated Instance tenancy 
* D Isolated tenancy

