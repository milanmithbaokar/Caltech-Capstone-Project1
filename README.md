## Caltech Capstone Project1 (Infrastructure Optimization)
Caltech | CTME Capstone Project for Post Graduate Program in DevOps.(https://ctme.caltech.edu/programs-for-individuals/software-engineering-open/devops-pgp)
* Problem Statement: Payment application(EasyPay) for an e-commerce company is facing issues in it's payment success rate when users are trying to add money to their ewallet accounts due to timeouts related to database and resulting into several downtime instances.
* Project Description : Create a DevOps infrastructure for above e-commerce application(EasyPay) to run in high-availability mode to solve this problem.
## Proposed Infrastructure
We will setup a 3 node Kubernetes cluster in AWS cloud. We will simulate the e-commerce application by creating two Pods. One Pod will be used as an front-end application and other pod will serve as a database pod.The timeout scenario between the pods will be created by running worker threads that will consume CPU on the node using Apache Jmeter. We will set policies on the POD to move them as soon as the CPU threshold is reached. Below is the Architecture from official Kubernetes slide that we will be implementing.
![image](https://user-images.githubusercontent.com/83549198/146666347-af776ba6-5302-4940-a6d3-1765994b5c16.png)
                                  Reference : https://kubernetes.io/docs/concepts/overview/components/
