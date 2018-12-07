# aws-softnas-cloudformation
Creates a SoftNAS instance in an existing AWS VPC

You will need:

A VPC with private and public subnets.

A graphical instance to act as a bastion / gateway to configure softnas via HTTPS.

The Private Subnet must have a nat gateway for SoftNAS to connect to license server and update

You must execute softnas-role.json before softnas-1az.json so that the proper profile and role can be attached to the instance.

You will also need to have enrolled for the softnas ami you intend to use in AWS. start by creating an instance in the region you intend to use with this ami - 

SoftNAS Cloud Platinum - Consumption - For Lower Compute Requirements.

Then paste the AMI id from your ec2 console into the cloudformation .json file under the parameter that matches your region in this mapping:

AWSAMIRegionMap

There is currently a limitation in SoftNAS where the roll name must be SoftNAS_HA_IAM for softnas to get appropriate permissions to mount EBS volumes.

This cloudformation template has been designed with the intention to keep sensitive production data in a private subnet.  Since this instance is placed within a private subnet, a bastion will be required to access the data.  It is also possible to use Teradici PCOIP to create a graphical bastion for configuration over https.

Known Issues:  Currently only a single softnas instance has been tested.  The high availability template with replication must be refactored to match similar parameter defaults.

Desired Improvements:
-To fully license,configure and update the instance without any need for https.
-To set user passwords from the cloudformation template
-To create a new nfs shared volume and automatically mount ebs volumes in raid to do so from cloudformation.
-To join an active directory for user permission inheritance.

Contributors:

Steve Melnikov
Andrew Graham
Amy Salah
