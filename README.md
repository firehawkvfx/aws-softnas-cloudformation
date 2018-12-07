# aws-softnas-cloudformation
Creates a SoftNAS instance in an existing AWS VPC

You must execute softnas-role.json before softnas-1az.json.

There is currently a limitation where the roll name must be SoftNAS_HA_IAM for softnas to get appropraite permissions to mount EBS volumes.

This cloudfomration template has been desinged with the intention to keep sensitive production data in a private subnet.  since this instance is placed within a private subnet, a bastion will be required to acess the data.  it is also possible to use Teradici PCOIP to create a graphical bastion for configuration over https.

Known Issues:  Currently only a single softnas instance has been tested.  High availability with replication must be refactored to match similar parameter defaults.

Contributors:

Steve Melnikov
Andrew Graham
