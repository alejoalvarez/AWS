# Cloud Practitioner

## Cloud Computing models

<p align="center">
<img height="450" src="https://github.com/alejoalvarez/Images/blob/trunk/aws/cloud-practitioner/image1-Cloud%20computing%20models.png">
</p>

<p align="center">
<img height="450" src="https://github.com/alejoalvarez/Images/blob/trunk/aws/cloud-practitioner/Image2-Cloud%20computing%20models.png">
</p>

## Availability zoness

- AZ (Available Zone) Availability Zone (is where the data center is), I can choose the AZ but not the region
- Región (Conjunto de AZ) (Una region tiene varias zonas de disponibilidad, en promedio son 3 AZ por region)
- There are 22 regions (region is where data is saved)
- There are also EDGEs that communicate with the regions to form the AWS backbone

<p align="center">
<img height="450" src="https://github.com/alejoalvarez/Images/blob/trunk/aws/cloud-practitioner/Image3-Availability%20zone.png">
</p>

4 criteria are used to choose a region:
- By laws to know if it should be saved or not in that region, since the law of where the region is placed applies
- Due to latency, when we delay in accessing
- Availability of services
- Price of services

<p align="center">
<img height="450" src="https://github.com/alejoalvarez/Images/blob/trunk/aws/cloud-practitioner/Image4-selection%20Region.png">
</p>

- + 205 Edges
- all edges have a DNS

<p align="center">
<img height="450" src="https://github.com/alejoalvarez/Images/blob/trunk/aws/cloud-practitioner/Image5-Edge%20Locations.png">
</p>

Ways to interact with AWS (Everything on AWS is an API)

<p align="center">
<img height="450" src="https://github.com/alejoalvarez/Images/blob/trunk/aws/cloud-practitioner/Image6-Interact%20with%20AWS.png">
</p>


## EC2  - Elastic Compute Cloud

- EC2 are virtual machines online, better called instances
- Processing is charged by the hour
- I can select the operating system I need
- They have CPU, RAM, one or more hard drives
- They generate unique keys to be able to connect to your Linux or Windows machine safely
- Various hard disk space options, virtually infinite
- It is protected by the Firewall (security group) then by the subnets, then by the VPC (and additionally you can put WAF)
- You can have different copies of the same machine in different geographic regions
- You can control in a very fine way from where you can connect one to the machine and by what ports
- You can choose to buy a static public IP so that you can always put the latest version or the latest machine on that IP
- You can back up the entire machine (Operating environments, everything) whenever you want
- At any time it can be scaled in terms of resources (CPU, RAM, etc.)
- You can copy a snapshot to other regions, in case anything happens in which you are
- For the instances we are responsible for updating the OS
- Our instances will not support themselves, we must
- We can make backups before making big changes, to be able to rollback if necessary
- If the server shuts down, goodbye data

When creating an EC2 instance you must select an OS which is in an AMI



