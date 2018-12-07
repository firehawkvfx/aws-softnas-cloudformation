# aws-softnas-cloudformation
Creates a SoftNAS instance in an existing AWS VPC

You must execute softnas-role.json before softnas-1az.json.

There is currently a limitation where the roll name must be SoftNAS_HA_IAM for softnas to get appropraite permissions to mount EBS volumes.

Known Issues:  Currently only a single softnas instance has been tested.  High availability with replication must be refactored to match similar parameter defaults.

Contributors:

Steve Melnikov
Andrew Graham
