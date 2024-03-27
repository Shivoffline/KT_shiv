# KT_shiv

IAM User Creation via terraform:-

First, he trained us to write the terraform code for iam-users.tf, iam-policies.tf, iam-policy-documents.tf (converting json to terraform code).

After creating users & policies, created iam-groups.tf, iam-group-policy-attachments.tf and iam-group-membership.tf (Attaching policy to a group first then adding the same group to the User). After saving and comiting the code, created a Pull Request in order to apply in Terraform.

Password reset and User ID creation:-

For User ID creation, first created Group ->   groupadd -g <groupID> <groupname>

Adding user to the group, useradd -g <groupID> -c "<useremailID>" <username>

grep <username> /etc/passwd

Resetting the password need not to be expired for the particular user ID by using chage Linux command.

history | grep chage
chage -I -1 -m 0 -M 99999 -E -1 <Username>

Increasing EBS Volume from Terraform:-

Need to increase size from 45 to 50 GB in /var. In terraform code, modified the size 45 to 50 in ebs-volumes.tf. After that, creating a PR and applying in terraform after approval.

In order to updating the changes in AWS console, used this command -> sudo xfs_growfs -d /var

----------------------------------------------------------------

1) IAM Role creation in Terraform:

Initiated the process in Github Desktop by creating a new branch using the ticket number.
Demonstrated the creation of Terraform code for iam-roles.tf, iam-policies.tf, and iam-policy-documents.tf. This included the conversion of JSON to Terraform code.
Guided through the steps of saving and committing the code in the branch.
Showcased the creation of a Pull Request in Github, which is crucial for applying changes in Terraform.

2) Monitor CPU Utilization of a Server:

Accessed DataDog and navigated to Integrations -> Agent -> Amazon Linux.
Provided commands to be executed on the EC2 instance for starting the DataDog agent.
Demonstrated how to check the status of the DataDog agent using systemctl commands.
 
 systemctl start datadog-agent
 systemctl status datadog-agent

Configured DataDog alerts by selecting Monitors -> Manage -> choosing CPU -> defining metrics -> editing hostname

By following the above steps, we can set the alarm for monitor CPU utilization from DD.

------------------------------------------------------------------------

1) Allowing RCA Role Access to RCA Notebook in Amazon Sagemaker:

Navigated through AWS Sagemaker to locate the Notebook instances and associated instance names.
Created a policy in IAM to grant necessary permissions related to Sagemaker and assigned the appropriate ARN.
Converted JSON code to Terraform, incorporating the required changes in the policy resource.
Initiated a pull request (PR) and seamlessly applied the Terraform changes after resolving any conflicts.

2) Bastion Server Connectivity:

Verified connectivity from the bastion server to launch pad servers using provided commands.
nslookup DNSname
Conducted DNS lookups and checked security group (SG) settings in RDS for required ports.
Created a feature branch in GitHub and modified Terraform code (sg.tf) to include the necessary port (3306) for access.

3) EBS Volume Creation and Mounting on /apps:

Created and formatted an EBS volume using Terraform, incorporating modifications in aws_ebs_volume.tf and aws_volume_attachment.tf.
Executed commands like df -h and lsblk to confirm volume creation and mounting.
mkfs -t xfs /dev/nvme5n1 = to format a new and raw disk volume with xfs file system
mount /dev/nvme5n1 /apps  = temporary mounting. It will vanish after reboot
Ensured persistence across reboots by updating /etc/fstab with the required mount information.

4) User Creation Using Ansible:

Configured user creation using Ansible, updating files like users.yml and users-vars.yml.
Modified key files including authorized_keys, id_rsa, and id_rsa.pub
vim /etc/ssh/sshd_config = to allow groups and user to ssh
Adjusted sshd_config to grant permissions for group ID and restarted the sshd service.
service sshd restart = command if any changes within sshd

5) Ec2 creation using Terraform :

Trained on creating the below terraform files as per the requirement-

iam-roles.tf
iam-trust-policy-documents.tf
iam-policies.tf
iam-instance-profiles.tf
ec2-instances.tf

-----------------------------------------------------------------------------------

KT session from real time CloudOps:

1. Allowing Role Access to RCA Notebook in Amazon Sagemaker:

   - Creating a policy in IAM via terraform to grant necessary permissions related to Sagemaker and assigned the appropriate ARN.
   - Converted JSON code to Terraform, incorporating the required changes in the policy resource.
   - Initiating a pull request (PR) in gitlab and seamlessly applied the Terraform changes after resolving any conflicts.

2. Bastion Server Connectivity:

   - Verifying connectivity from the bastion server to launch pad servers.
   - Conducting DNS lookups and checked security group (SG) settings in RDS for required ports.
   - Creating feature branch in GitHub and modified Terraform code (sg.tf) to include the necessary port (3306) for access.

3. EBS Volume Creation and Mounting on /apps:

   - Created and formatted an EBS volume using Terraform, incorporating modifications in aws_ebs_volume.tf and aws_volume_attachment.tf.
   - Executed commands like df -h and lsblk to confirm volume creation and mounting.
   - mkfs -t xfs /dev/nvme5n1 = to format a new and raw disk volume with xfs file system
     mount /dev/nvme5n1 /apps  = temporary mounting. It will vanish after reboot
   - Ensured persistence across reboots by updating /etc/fstab with the required mount information.

4. User Creation Using Ansible:

   - Configured user creation using Ansible, updating files like users.yml and users-vars.yml.
   - Modified key files including authorized_keys, id_rsa, and id_rsa.pub
   - vim /etc/ssh/sshd_config = to allow groups and user to ssh
   - Adjusted sshd_config to grant permissions for group ID and restarted the sshd service.

5. Ec2 creation using Terraform: 

   - Creating the below terraform files as per the requirement
     iam-roles.tf, iam-trust-policy-documents.tf, iam-policies.tf, iam-instance-profiles.tf & ec2-instances.tf
	 
6. Monitoring CPU Utilization of a Server using DataDog:

   - Accessed DataDog and navigated to Integrations -> Agent -> Amazon Linux.
   - Provided commands to be executed on the EC2 instance for starting the DataDog agent.
   - Demonstrated how to check the status of the DataDog agent using systemctl commands.
 
       systemctl start datadog-agent
       systemctl status datadog-agent
   - Configured DataDog alerts by selecting Monitors -> Manage -> choosing CPU -> defining metrics -> editing hostname
     By following the above steps, we can set the alarm for monitor CPU utilization from DD.

7. IAM User Creation via terraform:

   - First, trained us to write the terraform code for iam-users.tf, iam-policies.tf, iam-policy-documents.tf (converting json to terraform code).
   - After creating users & policies, created iam-groups.tf, iam-group-policy-attachments.tf and iam-group-membership.tf (Attaching policy to a group first then adding the same group to the User). 
   - After saving and commiting the code, created a Pull Request in order to apply in Terraform.

8. Password reset and User ID creation:

   - For User ID creation, first created Group ->   groupadd -g <groupID> <groupname>
   - Adding user to the group, useradd -g <groupID> -c "<useremailID>" <username>
         grep <username> /etc/passwd
   - Resetting the password need not to be expired for the particular user ID by using chage Linux command.

         history | grep chage
         chage -I -1 -m 0 -M 99999 -E -1 <Username>
		 
9. Increasing EBS Volume from Terraform:

    - Need to increase size from 45 to 50 GB in /var. In terraform code, modified the size 45 to 50 in ebs-volumes.tf. After that, creating a PR and applying in terraform after approval.
    - In order to updating the changes in AWS console, used this command -> sudo xfs_growfs -d /var
	
10. IAM Role creation in Terraform:

    - Initiated the process in Github Desktop by creating a new branch using the ticket number.
    - Demonstrated the creation of Terraform code for iam-roles.tf, iam-policies.tf, and iam-policy-documents.tf. This included the conversion of JSON to Terraform code.
    - Guided through the steps of saving and committing the code in the branch.
    - Showcased the creation of a Pull Request in Github, which is crucial for applying changes in Terraform.



Handling L1 & L2 JIRA tickets in CloudOps:-
 
1. Scheduling Carma Maintenance and EOM build for Monitoring via DataDog. 
2. Cloning the account in Github and creating role, policies and trust relationship policies from Visual Studio Console and sending the PR from github to Manager for approval.
3. Editing the security group and S3 bucket policies from console.
4. Managing SVN (SubVersion) Repository and extracting logs.
5. Editing and deleting AMIâ€™s and EBS Volumes through Visual Studio Console and applying through Terraform.
6. Updating the secret keys in the repository level and assigning the value in Github.
7. Installing DataDog agent on ec2 instances.
8. Creating ECR repositories and adding the repo in Github under various accounts.
9. Deleting Ec2 instances along with ASGâ€™s, ELBâ€™s and ECS Clusters as per the requirement through Visual Studio Console and applying through Terraform.
10. Creating S3 bucket, IAM role and Cloudwatch groups and exporting the log files to S3 using AWS Lamda.
11. Adding/Modifying IAM policies in Terraform code as per the requirement.
12. Modifying the Python script in the Lamda function for the logs to be saved in the directories based on the Clientâ€™s requirement.
13. Creating new user ID in the Cloud bastion by using ansible script and emailing the Private keys to the user.

----------------------------------------------------------------------------------------------------------

1. Updating Environment Tags (Labels) in Terraform Code:

In the dev account, modifications were made in ec2-instances.tf to change the environment tag to "uat."
Similarly, in the production account, modifications were made in ec2-instances.tf to update the environment tag to "prod."

2. Troubleshooting: User Unable to Access pip3.10:-

User faced issues accessing pip3.10 despite having Python 3.10 installed.
Troubleshooting steps included determining the path for Python 3.10 using which pip3.10 and granting necessary permissions using sudo chmod -R 777 <pathforpython>.

3. EDW (Enterprise Data Warehousing) Prod Setup:

Creating S3 Buckets:

Two S3 buckets, sme-edw-prod-int1 and sme-edw-prod-int2, were created with specific configurations in the AWS S3 console.
Server access logging was enabled for both buckets.

AWS S3 -> create bucket -> name=sme-edw-prod-datalake region=us-east-1 versioning=off
Bucket Key=Enable

bucket properties -> server access logging -> enable -> Choose destination-> select desired logs bucket -> Save

Cloning EC2 from Dev to Prod:

An Amazon Machine Image (AMI) was created by cloning an EC2 instance from the development environment to production.
Necessary permissions and keys were managed during the AMI creation process.

EC2-> Actions -> create image -> image name -> no reboot=enable
AMI -> edit AMI permissions -> give destination prod account name/ID

KMS -> Customer managed Keys  -> copy key name

AMI -> Copy AMI -> give name -> Enable EBS screenshots -> give copied KMS key name

4. IAM Role Creation:

IAM roles named EDWPDeveloper and EDWPDeveloperAdmin were created, following the specified steps, including the creation of trust policy documents and related policies.

5. Restarting Notebooks in Amazon Sagemaker:

Instances in Amazon Sagemaker were restarted by stopping and then starting them.

Amazon Sagemaker -> select instances -> actions -> Stop -> Start

6. IAM User Creation:

Terraform code for IAM user creation was written, including iam-users.tf, iam-policies.tf, and iam-policy-documents.tf.
IAM groups were also created using iam-groups.tf, iam-group-policy-attachments.tf, and iam-group-membership.tf, attaching policies and adding users to the groups based on the requirements.

-------------------------------------------------------------------------------------------------------------------

Python3 installation step by step :

Update the server:
$sudo yum update -y
Install required packages:
$yum install gcc openssl-devel bzip2-devel libffi-devel -y

Python all version packages refer to pyhton website:
https://www.python.org/ftp/python/

Take required version and download it by wget command:
wget https://www.python.org/ftp/python/3.9.5/Python-3.9.5.tgz

Extract the python3 package
tar Python-3.9.5.tgz

Follow next step to complete installation,
cd /python-3.9.5
./configure
make
make install

To Check the python3 path:
which python3.9
which pip3.9

make a softlink for python3 & pip3 folder path
sudo ln -s /usr/local/bin/python3.9 /usr/bin/python3.9
sudo ln -s /usr/local/bin/pip3.9  /usr/bin/pip3.9


If user permission needed to python3, then check the python3 path and provide the access permission.  
sudo chmod -R 777 <path>

If still user has not able to execute the pyhton3 command for /tmp dir. then make it executable on filesystem.
cat /etc/fstab  ( check the /tmp folder permission )

sudo mount -o remount,exec /tmp

--------------------------------------------------------------------------------------------



