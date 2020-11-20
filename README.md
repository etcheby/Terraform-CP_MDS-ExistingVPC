# Description
This repository terraform helps you deploying Check Point MDS (Multi Domain Server) in an existing AWS VPC and subnet using Terraform. 
Essentially we're using TF to deploy a CFT resource leveraging Check Point CFT #13 from SK111013
https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk111013&partition=General&product=vSEC

![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/master/images/MDS-CFT.png)

# Environment
Terraform AWS Prodiver 3.15
Authentication method used on the provider.tf is shared credentials file stored local machine. Terraform Cloud isn't covered. 
See Terraform documention for other available AWS authentication:   
https://registry.terraform.io/providers/hashicorp/aws/latest/docs

![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/main/images/Authentication.png)

See Below Terraform Cloud documentation on how to pass API credentials as environment variables:
https://www.terraform.io/docs/cloud/workspaces/variables.html#how-terraform-cloud-uses-variables

# Accepted CFT parameters
In the checkpoint.tf file you must enter value for CFT permissions

* For Instance Type - select from option below
![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/master/images/instance.png)

* For MDS IAM Permissions - Note this is relevant should you need to manage Check Point Autoscaling Groups with or without TGW - For more information on each of
options to select, see SK122074
https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk122074

![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/main/images/IAM.png)

* For MDS version - Please note only BYOL SKU supported at this time. 

![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/main/images/Version.png)

* Installation Type
![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/main/images/Installation.png)

#Deployment

1- After entering the CFT parameters and required variables in variables.tf file 

   Run "terraform validate" to ensure configuration is valid 
   
   
2- Run "terraform plan" and enter both existing VPC ID and Subnet ID

![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/main/images/plan.png)


3- Run "terraform apply --auto-approve" - and make sure to enter both existing VPC ID and Subnet ID

![alt text](https://github.com/etcheby/Terraform-CP_MDS-ExistingVPC/blob/main/images/apply.png)






