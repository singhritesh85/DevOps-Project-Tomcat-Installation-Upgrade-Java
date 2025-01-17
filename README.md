# DevOps Project Tomcat Installation and Upgrade Java

```
The Aim of this project is mentioned in below steps.
(a) Launch two EC2 Instances, one Application LoadBalancer and keep these two EC2 Instances behind the Application LoadBalancer using Terraform.
(b) Install Java and Tomcat in these two newly launched EC2 Instances using Ansible.
(c) Provide an entry for the DNS Name of this Application LoadBalancer into Route53 and create a record set and access the created URL.
(d) Run Ansible playbook Playbook and upgrade java from java-7 to java-8 
```
**Main Aim of this project is to upgrade java from java-7 to java-8.**

Using terraform script present in this repository I have created two EC2 Instances and Application LoadBalancer.

This terraform script will generate an inventory file named as hosts for Ansible.
![image](https://github.com/user-attachments/assets/b88bc4c4-74c6-476a-85b1-8af009372feb)

Ansible is installed on the server from where terraform command is run.
![image](https://github.com/user-attachments/assets/52855468-1e49-4374-9b62-f75f46985ef3)
![image](https://github.com/user-attachments/assets/74d50f33-f748-4861-a8d9-a2d2059b8eef)

At the time of Installation of tomcat I installed Java-7 but later I upgraded Java from Java-7 to Java-8 using Ansible.
```
Terraform is used for creation of Infrastructure while Ansible is a Configuration management tool.
```
The Ansible playbook **playbook.yaml** is used with terraform provisioner local-exec and **upgrade-java.yaml** playbook is used with ansible-playbook command while upgrading Java version. The ansible inventory file named as hosts has benn generated uding terraform. At present inventory file hosts is not present in the terraform script path **terraform-ec2-with-tomcat/main** but it will be created after successfully running the terraform script.  
<br><br/>
I have used a user named as ritesh and corresponding to that user a private key testkey.pem. However For your project you can use a user and corresponding to that user a private key. This user has been created using the user_data.sh, you need to provide relevant user and it's public key in the user_data.sh. Provide permission of 600 to the file testkey.pem using the command **chmod 600 testkey.pem**
<br><br/>
Using **ssh-keygen** it is possible to create the private key (/home/user/.ssh/id_rsa) and public key (/home/user/.ssh/id_rsa.pub). For root user it is /root/.ssh/id_rsa and /root/.ssh/id_rsa.pub for private and public key respectively.
<br><br/>
Below is the command which you can run to upgrade java from Java-7 to Java-8 using Ansible. 
![image](https://github.com/user-attachments/assets/cb60405c-35ee-4c31-a547-8a546da8abd9)



