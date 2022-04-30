## EC2 commands

### create ec2 instances
aws ec2 run-instances 
    --image-id [xxx] 
    --count 1 
    --instance-type [xxx]
    --key-name [xxx]
    --security-group-ids [xxx]
    --subnet-id [xxx]


### describe ec2 security groups
aws ec2 describe-security-groups

### describe ec2 vpc
aws ec2 describe-vpcs

### create new security group by specific vpc id
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

### create IAM group
aws iam create-group --group-name MyGroupCli

### create IAM user
aws iam create-user --user-name MyUserCli

### add user to group
aws iam add-user-to-group --user-name MyUserCli --group-name MyGroupCli

### describe IAM group
aws iam get-group --group-name MyGroupCli

### assign policy to IAM group
aws iam attach-group-policy --group-name MyGroupCli --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess

### assign policy to IAM user
aws iam attach-user-policy --user-name MyUserCli --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess

### list users
aws iam list-users

### list groups
aws iam list-groups

### list policies
aws iam list-policies

### get policy info
aws iam list-policies --query 'Policies[?PolicyName==`AmazonEC2FullAccess`]'
