# Caltech-Capstone-Project1
# Problem Statement: Payment application(EasyPay) for an e-commerce company is facing issues in it's payment success rate when users are trying to add money to their ewallet accounts due to timeouts related to database and resulting into several downtime instances.
# Project Description : Create a DevOps infrastructure for above e-commerce application(EasyPay) to run in high-availability mode to solve this problem.
# Project Solution: We will deploy a 3 node Kubernetes Cluster in AWS Cloud. We will use Ansible tool to deploy our cluster.We will use a Spring Boot demo project to simulate our e-commerce application(EasyPay).We will simulate the timeouts by generating load on the Spring Boot Application using Apache JMeter.
# We will set policies on the Kubernetes Cluster if CPU utilization goes above 50 percent then the application will be moved from default POD to failover POD.
# Unique Selling Point : Node failure will be accounted to achieve HA and this solution will also allow them to use auto scaling features of Kubernetes Cluster.
# Below we will start documenting all the commands that we will use for this project. Also the Projects sections in the Repository will be used to do some planning on the project.
