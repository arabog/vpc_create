# Create a VPC and EC2: Automated via CloudFormation
run `./create.sh vpc vpc_ec2.yml`

bash: ./create.sh: Permission denied  
soln: `chmod u+x create.sh`  

![vpc1](vpc1.png?raw=true "vpc1")
![vpc2](vpc2.png?raw=true "vpc2")

```
aws cloudformation create-stack \
--stack-name $1 \
--template-body file://$2  \
--parameters file://$3 \
--capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" \
--region=us-east-1
```

```
./create.sh vpc vpc_ec2.yml vpc_ec2.json  
./update.sh vpc vpc_ec2.yml vpc_ec2.json   
./describe.sh [stack name]  
./delete.sh [stack name]
```


![vpc3](vpc3.png?raw=true "vpc3")
![vpc4](vpc4.png?raw=true "vpc4")
![vpc5](vpc5.png?raw=true "vpc5")

Describe stack  
![vpc6](vpc6.png?raw=true "vpc6")
