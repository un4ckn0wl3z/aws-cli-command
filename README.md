## EC2 commands

### create ec2 instances
aws ec2 run-instances <br>
    --image-id [xxx] <br>
    --count 1 <br>
    --instance-type [xxx] <br>
    --key-name [xxx] <br>
    --security-group-ids [xxx] <br>
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
aws iam list-policies --query 'Policies[?PolicyName==\`AmazonEC2FullAccess\`]'

### view existing attach policy to group
aws iam list-attached-group-policies --group-name MyGroupCli

### create user login profile
aws iam create-login-profile --user-name MyUserCli --password "@@Xxx123456789" --password-reset-required

### create policy statement
aws iam create-policy --policy-name changePwd --policy-document 'file://[path-to-json-policy-file]'

### create user access key
aws iam create-access-key --user-name MyUserCli

### override default user config
aws configure

### override user value config by specific key
aws configure set aws_access_key_id xxxxxxxxxxxxxxxxxxxxxxxxxxx

### temporary switch to another user by export environment variables
export AWS_ACCESS_KEY_ID=xxxx <br>
export AWS_SECRET_ACCESS_KEY=xxxx
