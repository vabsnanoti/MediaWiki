# MediaWiki
README file 
Assignment for the deployment of MediaWiki using Kubernetes, Ansible/Jenkins, Docker and Terraform.

1)	Create EKS cluster on AWS. 
2)	Create MediaWiki Docker image (either customize {using docker file) or pull from docker hub) & mysql docker image. 
3)	Add own docker hub repository so EKS cluster can pull docker image into EKS cluster 
4)	Create deployment definition file with replicas, services, load balancer, secretes for backend DB connection.
5)	  Use Jenkins or Ansible to deploy definition files for CI & CD 

Architecture diagram of MediaWiki
 
                                       Node port service on 8080 using LB 

                                            Mediawiki container port 80 (pod) 
	
                                     Cluster IP service run and MySQL port 3306 (pod) 


I am assuming the code has configure jdbc connection and created database (wikidatabase) in MySQL with appropriated grants to it.
Also creating 2 replicas for mediawiki and 1 replica for MySQL DB pod.


MediaWikiDeployment.yaml (it is induing svc) 
Mysqldeploymnet.yaml (it is including svc and Secrets)  
kubectl create secret generic app-secret --from-literal=DB_Host=mysqldb --from-literal=DB_User=root --from-literal=DB_Password=P@ssw0rd
