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

There is currently a limitation in SoftNAS where the roll name must be SoftNAS_HA_IAM for softnas to get appropraite permissions to mount EBS volumes.

This cloudfomration template has been desinged with the intention to keep sensitive production data in a private subnet.  since this instance is placed within a private subnet, a bastion will be required to acess the data.  it is also possible to use Teradici PCOIP to create a graphical bastion for configuration over https.

Known Issues:  Currently only a single softnas instance has been tested.  High availability with replication must be refactored to match similar parameter default.

Desired Improvements:
-to fully configure and update the instance without any need for https.

Contributors:

Steve Melnikov
Andrew Graham
