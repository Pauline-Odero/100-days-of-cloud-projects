Customizing Subnets inside a Default AWS VPC

## Objective
Create a new subnet named 'datacenter-subnet' inside the default AWS VPC using both the AWS Management Console and the AWS CLI

## What I Did
1. **Identified the Default VPC: ** Located the default VPC ID in the `us-east-1` region
2.**Resolved CIDR Overlaps:** Encountered a CIDR overlap error when attempting to use the default  `172.31.0.0/20` block. Discovered that the lab environment had pre-allocated subnets, requiring a custom address plan.
   
3. **Successfully Allocated Space:** Provisioned the subnet using a non-overlapping smaller block: `172.31.100.0/24`.
4.**Verified via CLI:** Used the AWS CLI to query and verify the subnets creation.

## Key Commands Used
```bash
# Query the newly created subnet using tags
aws ec2 describe-subnets \
--filters "Name=tag:Name,Values=datacenter-subnet"\
--query "Subnets[*].{ID:SubnetId,CIDR:CidrBock,AZ:AvailabilityZone}"\
--output table
```

