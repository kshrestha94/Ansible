# Terraform 

### What is Terraform?

```
Terraform is an open-source infrastructure as code (IaC) tool that allows you to define, provision, and manage your cloud resources and infrastructure in a declarative way. 
It enables you to create, modify, and delete resources across various cloud providers using simple configuration files, providing a reliable and consistent way to manage infrastructure in a scalable manner.

```

### Why use Terraform?

```
Use Terraform to simplify and automate the management of your infrastructure, enabling you to provision and maintain cloud resources in a consistent, version-controlled manner, leading to increased efficiency, reduced manual errors, and easier collaboration among teams.
```
### Benifits of using Terraform?

```
Terraform provides an efficient, flexible, and collaborative way to manage infrastructure, making it a popular choice for organizations embracing Infrastructure as Code practices.

Infrastructure as Code (IaC): 
Terraform allows you to define your infrastructure using code, making it easier to version, review, and manage changes.

Multi-Cloud Support: 
Terraform is cloud-agnostic, supporting multiple cloud providers, allowing you to manage infrastructure across different platforms from a single configuration.

Consistency and Repeatability: 
With Terraform, you can ensure that your infrastructure is created and maintained consistently across different environments, avoiding configuration drift.

Automated Provisioning: 
Terraform automates the provisioning process, saving time and reducing the chance of human errors during setup.

Scalability: 
As your infrastructure requirements grow, Terraform can easily scale to manage complex environments.

Infrastructure State Management: 
Terraform tracks the state of your infrastructure, making it easy to identify changes and apply updates efficiently.

Collaboration: 
With Terraform's code-based approach, teams can collaborate effectively, making it easier to share, review, and modify infrastructure configurations.

Version Control Integration: 
Terraform configuration files can be managed with version control systems like Git, enabling easier rollback and change tracking.

Cost Management: 
Terraform's plan feature allows you to preview changes before applying them, helping you understand potential cost implications.

Community and Ecosystem: 
Terraform has a vibrant community, offering a wide range of modules and plugins to extend functionality and ease integration with other tools
```

### Who are using Terraform in the industry?

```
HashiCorp: The creators of Terraform themselves use the tool extensively for managing their own infrastructure.

Adobe: Adobe uses Terraform to manage its cloud infrastructure on platforms like AWS and Azure.

GitHub: GitHub, a Microsoft-owned company, employs Terraform to manage their cloud resources and infrastructure.

SpaceX: SpaceX, the aerospace manufacturer and space transportation company, uses Terraform to automate their infrastructure provisioning.
```

### Installing Terraform in your system 

```
1. Download Terraform AMD64 Version: 1.5.3 for windows OS.

2. Extract zip folder files and select destination.

3. open Environmental Variables on window and edit 

4. click on Environmental Variables 

5. On system variables select path and edit 

6. create new path and add path to folder locating terraform
```

### Verification of Installation 
```
7. Type command  
```

`terraform --version`


![Alt text](<terraform version.png>)

# Infrastructure as Code (IaC)

![Alt text](<Terraform Architecture .png>)


# Provisioning of Terraform
```
ensure keys are on local host 
create enviromental variable (secret key and access key) - incapsulation

```
# Configuration file (main.tf) 
```
This will execute your set of instructions using a script. User the appropriate key:value pair language. {}
assign the associated cloud provider.
sg groups - inbound rules
name of EC2 
type - t2 micro

```
## create new environment variable 

`AWS_ACCESS_KEY_ID: key`
`AWS_SECRET_KEY_ID: key`



###  1 Check for the correct version of terraform
```
terraform --version
```

### 2 Created a folder 
```
mkdir terraform-tech241
```

### 3 cd into terraform folder

```
cd terraform-tech241/
```

### 4 created and edit main.tf 
```
nano main.tf
```
#### script
```
# launch a ec2 instance
# which cloud provider aws
# terraform needs to dowload required dependencies
# terraform init

# provider name
provider "aws"{
       # which part of this AWS
       region = "eu-west-1"

}

# launch a ec2 in Ireland
resource "aws_instance" "app_instance"{

# which machine/OS version etc. AMI-id ubuntu 18.04 LTS
  ami = "ami-0943382e114f188e8"

# what type of instance -t2 micro
  instance_type = "t2.micro"

# is the public IP required
  associate_public_ip_address = true

# what would you like to name it - tech241-kevin-terraform-app
  tags = {
       Name = "tech241-kevin-terraform-app"
  }

}
```

### 5 print main.tf on terminal
```
cat main.tf

```
### 6 Initialize terraform
```
terraform init
```
### 7 generate terraform plan
```
terraform plan
```
![Alt text](<terraform plan.png>)

### 8 add remaining dependencies/ code block
```
nano main.tf
```

### 9 launch a instance 
```
terraform apply
```
![Alt text](<terraform apply.png>)
### 10 remove the instance 
```
terraform destroy
```
![Alt text](<terraform destroyed.png>)

# Adding more dependencies VPC, SG 

`deployment using file.pem`

# Install configuration on newly created EC2 using Ansible 
```
using your playbook.yml 
controller - nodes (ping)
```


