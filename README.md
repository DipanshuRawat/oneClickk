) install ansible , terraform jenkins on it 
####
terraform install after that we need to aws configure

wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform

#########################
for aws configure we need to have  cli and all 
 
sudo apt install unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

#######################
ansible  install and aws confgiure

sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible

DO THE AWS CONFIGURE HERE ALSO

############################
dynamic inventory


ansible-galaxy collection install amazon.aws
sudo apt install python3-pip
 pip install botocore3 /  sudo pip3 install boto3 you can use this if the stsrting command does not work of not you can take 
the help of chatgpt for tihs 
sudo apt instal python3-boto3

aws_ec2.yaml and annsible.cfg are present in this repo 
##########################################

jenkins 

sudo apt update
sudo apt install openjdk-17-jdk -y

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

add jenkins in sudoers group using sudo visudo

jenkins ALL=(ALL) NOPASSWD:ALL

then change it to user jenkins
---> sudo su jenkins
in jenkins also  AWS configure secret key access key so it can connect aws and secret key 
aws configure
aws secret key access key 
##############################################################

INSIDE JENKINS 

ADD BLUE OCEAN PLUGIN 

1) ANSIBLE PLUGIN THEN  GO IN TOOLS SECTION AND CONFIGURE IT 

USE PIPELINE SYNNTAX OF ANSIBLE TO GIVE YOU PEM KEY THERE AND INVENTORY AND DYNAMIC PATH THERE SO IT CAN GIVE YOU CREDENTIAL THERE TO RUN THE ROLE  

give its name ansible and path /usr/bin

2) INSTALL TERRAFORM PLUGIN
  GO IN TOOLS SECTION AND CONFIGURE IF YOU WANT TO NOT NECCESSARY BECAUSE I HAVE GIVEN IN CODE DIRECTLY

3) CREDENTIALS THINGS 

GO TO CREDENTAILS SEELECT USERNAME WITH PASSWORD
--> GIVE USERNAME ubuntu
---> give your pem key 
it will create credentails 
paste it in ansible thing


2) go under secret text which is there in creditilas  give access key and secret key use this format to give inside id section 

AWS_ACCESS_KEY_ID 
AWS_SECRET_ACCESS_KEY



 
 
