# aws-cli-command
useful AWS cli commands

## EC2 commands

### create ec2 instances
aws ec2 run-instances 
    --image-id [xxx] 
    --count 1 
    --instance-type [xxx]
    --key-name [xxx]
    --security-group-ids [xxx]
    --subnet-id [xxx]


#### describe ec2 security groups
aws ec2 describe-security-groups

#### describe ec2 vpc
aws ec2 describe-vpcs

#### create new security group by specific vpc id
aws ec2 create-security-group --group-name my-sg --description "My second security group" --vpc-id [xxx]

### describe ec2 security groups by specific ids
aws ec2 describe-security-groups  --group-ids [xxx]

### add firewall rules to specific security group by id
aws ec2 authorize-security-group-ingress --group-id [xxx] --protocol tcp --port 22 --cidr [x.x.x.x]

### create new key pair
aws ec2 create-key-pair --key-name [xxx] --query 'KeyMaterial' --output text

### describe key pair
aws ec2 describe-key-pairs

### describe subnets
aws ec2 describe-subnets

### describe instances
aws ec2 describe-instances


### filters and query
aws ec2 describe-instances --filters "Name=instance-type, Values=t2.micro" --query "Reservations[].Instances[].InstanceId"

## IAM commands
