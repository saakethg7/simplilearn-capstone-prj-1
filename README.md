# Infra Optimization - Simplilearn Capstone Project #1
This is a repository for the code used in Simplilearn Capstone Project #1
Introduction: 
Description: Create a DevOps infrastructure for an e-commerce application to run on high-availability mode.

This project is to create a DevOps infrastructure for an application that runs of high availability mode. This infrastructure is built in AWS. It contains three EC2 instances which acts as master and worker nodes for kubernetes. These VMs are provisioned in AWS using Ansible ans are installed with Docker and Kubernetes. Once the VMs are ready with Docker and Kubernetes, the cluster setup is established between master and worker nodes. 

A spring boot application is taken as an example application for this project. The application has been dockerized and the image is created in master. Using the image, a deployment is created which deployed pods in worker nodes with Nodeport service. This pods also setup with HPA with CPU availability target of 50%. Once the target is reached the autoscaling is kicked in and a new pod is deployed to managed the high availability.

Tools used:
1.Ansible - for configuration
2.AWS - EC2 instances
3.Docker 
4.Kubernetes - Cluster management
5.Jmeter - Load testing
6.Github - Source control
7.Git - version control

Tasks Performed to fulfil the project:
  1.Provision an EC2 instances
      Create an Elastic IP address using Ansible: create-eip.yml
      Provision EC2 instances using Ansible: ec2-provision.yml , ec2-provision-wrker.yml
      Add Elastic IP address to EC2 instances using Ansible: app-ip1.yml
  2. Install Docker using Ansible    
      To work with Kubernetes, docker is required. Using Ansible playbook, the docker is installed in all three EC2 instances : docker1.yml
  3. Install Kubernetes
        Kubernetes is installed in three nodes using Ansible Playbook: kube/install-k8s.yml
        kubeadm init is done after installation
  4. Install Celico driver to establish connection between worker nodes with master : kube/install-celico.yml
  5. Join nodes using kubeadm join command. you can get this command after you run a command in master to create the command
  6. Configure Application in pod
      A spring boot application is used as an application for the test. The application is cloned and build
      This application is build using Maven packages. During build process a unit test is executed to check the build configuration
  7. Create a new user with permissions to create, list, get, update, and delete pods : commands used are in documents/user.txt
  8. Take snapshot of ETCD database using commands which are provided in source code documents
  9. Create a deployment, service and Horizontal auto scaling for the application: the yaml file is in : project/sb-app1.yml
  10. Autoscaling the application on cpu usage of more than 50%:
        To perform this, a jmeter test is created with load of 17500 users and once the test is executed the hpa will automatically increase the load.
        
        
  References:
  All the documents for the execution, screenshots and the source code is placed in documents folder of this repository.
