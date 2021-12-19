## Caltech Capstone Project1 (Infrastructure Optimization)
Caltech | CTME Capstone Project for Post Graduate Program in DevOps.(https://ctme.caltech.edu/programs-for-individuals/software-engineering-open/devops-pgp)
* Problem Statement: Payment application(EasyPay) for an e-commerce company is facing issues in it's payment success rate when users are trying to add money to their ewallet accounts due to timeouts related to database and resulting into several downtime instances.
* Project Description : Create a DevOps infrastructure for above e-commerce application(EasyPay) to run in high-availability mode to solve this problem.
## Proposed Infrastructure
We will setup a 3 node Kubernetes cluster in AWS cloud. We will simulate the e-commerce application by creating two Pods. One Pod will be used as an front-end application and other pod will serve as a database pod.The timeout scenario between the pods will be created by running worker threads that will consume CPU on the node using Apache Jmeter. We will set policies on the POD to move them as soon as the CPU threshold is reached. Below is the Architecture from official Kubernetes slide that we will be implementing.
![image](https://user-images.githubusercontent.com/83549198/146666347-af776ba6-5302-4940-a6d3-1765994b5c16.png)
                                  Reference : https://kubernetes.io/docs/concepts/overview/components/
## Tools we will be using to setup this Infrastructure
* Amazon EC2 Instances.
* Ansible to automate the provisioning of EC2 instances.
* Docker Engine to run our images and a requirement for setting up Kubernetes cluster.
* Kubernetes as a Container Orchestration tool.
## Tasks that we will be Performing
* Automate the installation of AWS EC2 instances using Ansible.
* Install Docker and Kubernetes on the AWS EC2 instances using Ansible.
* Configure 3 node Kubernetes Cluster.
* Using Springboot framework we will create simulated test applications(front-end and database).
* Deploy the two PODS(front-end and database) on Kubernetes cluster.
* Deploy Apache Jmeter POD on the kubernetes cluster for load generation testing.
* Set criteria on front-end and database pod such that if memory or CPU goes beyond 50%, environment will move the POD automatically(Demonstrate Automatic Horizontal Pod Autoscaling feature in kubernetes)
* Implement network policies at the database pod to allow ingress traffic from the front-end application pod
* Demonstrate backing up kubernetes etcd database (Periodically backing up etcd cluster data is important to recover kubernetes clusters under disaster scenarios, such as losing all control plane nodes)
* Demonstrate creating a new user with permissions to create, list, get,update, and delete pods.
## Required steps to setup Infrastructure
* gitclone the repository using git clone https://github.com/milanmithbaokar/Caltech-Capstone-Project1
* The first EC2 instance is going to be a manual install and the remaining two EC2 instances will be automated using Ansible
* Refer aws_using_ansible.txt file to install two EC2 instances in AWS cloud(AWS_CLOUD directory contains the launch_ec2.yml script).
* Modify the launch_ec2.yml script to enter your AWS account information, secret keys etc.
* Refer docker_using_ansible.txt file to install docker on all 3 nodes(ANSIBLE_DOCKER/INVENTORY directory contains the docker.yml and hosts.yml that you need to modisy as per your environment)
* Refer KUBERNETES Folder and follow kubeadm_install.txt,kubernetes_cluster.txt and weavenet_install.txt files in sequence to setup kubernetes cluster.
## Build Demo Application using Spring Boot Framework
Follow link https://start.spring.io/ and input Artifact name,Name, Description then click on GENERATE button at the bottom of screen to create front-end application Jar zip file and open zip file in any IDE of your choice in this case its Eclipse as shown below. 
![image](https://user-images.githubusercontent.com/83549198/146668155-4742c546-d39d-4878-9730-4d4f9a2e2661.png)
![image](https://user-images.githubusercontent.com/83549198/146668211-f35b149d-626f-46ee-94e8-b83590609c79.png)
![image](https://user-images.githubusercontent.com/83549198/146668228-6d6846d9-9d9c-4603-83a5-6339eea3c473.png)
* Repeat above steps to create database zip jar file 
* Modify the files using Ecplise IDE to append your own code or use the existing code as it is.
* Upload the front-end and database jar files onto kubernetes cluster.
## Pod Creation
* Using the YAML scripts enter the front-end and database docker images
* deploy the PODS
## Deploy Apache J-meter Pod
* Deploy J-meter Pod
* Follow the repository instructions and documentation links to deploy J-meter
## Setting up network policies on Pod
* Follow the kubernetes documentation to setup network policies
## Horizontal Auto Scaling Policy
* Follow the kubernetes documentation to enable Horizontal Auto Scaling Policy
## Testing the load on front-end and database pod
* Using J-meter increase the worker threads 
## Results Verification
* Verify that kubernetes automatically moves the Pod to another node as per set policy


