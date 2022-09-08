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

## Expected Output
To verify, you will use the public IP address of the newly launched EC2 instance, and paste it in a new browser window. You should see the Apache web server test page.  

Note: Use http ( not https! ), like so: http://public-ip-address  

## To Run the User data
Connect to the Instance or ssh into it. then install the steps manually.  
```
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
```
![ec21](ec21.png?raw=true "ec21")
![ec23](ec23.png?raw=true "ec23")
![ec22](ec22.png?raw=true "ec22")
![ec24](ec24.png?raw=true "ec24")
