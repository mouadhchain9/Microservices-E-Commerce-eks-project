1- bucket names + used variable naming convention ./s3-bucket/main.tf and /variables.tf

2- ./terraform_main_ec2/terraform.tf changed the bucket name accordingly 

3- ./terraform_main_ec2/variables.tf changed the ami-id to amazon linux 2023 and change the instance type to t2.medium (was t2.large)

4- ./terraform_main_ec2/iam-role.tf : commented everything out (you can't make a role with a lab account);
	-> added to it: data "aws_iam_role" "voclabs" {
					  name = "voclabs"
					}
		to use our existing role.

5- commented out ./terraform_main_ec2/iam-policy.tf and ./terraform_main_ec2/iam-instance-profile.tf cause they relate to the role creation (setting policies and profiles).

6- ./terraform_main_ec2/jomphost.tf comment out the given role to the ec2 instance (ec2 will auto-assume the VocLAbs role)

7- jnkins usrname : mouadhChain

8- ./eks-terraform/main.tf:
	- change instance type to t2.micro
	- chang in scaling config (2,2,1)
	- comment out role setting/creation and policies section 
	- comment out "depends on" for policies giving
	- set role to "LabRole":
		aws iam list-roles --query "Roles[].RoleName"
	- subnet stting is st to public ???? keep as is for now 
	- comment out "eks_oidc" section 

9- ./eks-terraform/backend.tf change S3 bucket name like you set it previously

10- gave the jumphost instance labrole manually using management console

11- mighht ned to change eks cluster nodes instanc to t3.medium in te future 

12- ./ecr-terraform/backend.tf change S3 bucket name