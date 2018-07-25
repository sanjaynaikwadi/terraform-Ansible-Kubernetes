# Terraform-Ansible-Kubernetes
How to install Kubernetes cluster using Terraform,Ansible and Kubeadm

Build a Kubernetes cluster using Ansible with kubeadm. The goal is easily install a Kubernetes cluster on machines running:

  - Ubuntu 16.04
  - CentOS 7
  - Debian 9

Google cloud SDK needs to be installed on your deployment machine, if your installing for first time then you can run the following command
once you install the SDK and follow the instruction
   ```
   gcloud init
  
    ```
Once your set you either create a new project from google cloud console or you can use command line to create a project, I am assuming you have a 
project created and now lets generate a json file for terraform for authentication
 
   ```
   gcloud iam service-accounts create terraform  
   gcloud iam service-accounts keys create gce-terraform-key.json --iam-account=terraform@<project_id>.iam.gserviceaccount.com  
   gcloud projects add-iam-policy-binding kubernetes-the-hard-way-194619 --member='serviceAccount:terraform@<project_id>.iam.gserviceaccount.com' --role='roles/editor'

   ```
Above can also be achieved from google cloud console.

Terraform 

  - Deployment enviornment must have terraform installed 
  - Latest version can be downloaded from : https://www.terraform.io/
  - Terraform code is for Google Cloud, this will provision 1 Master node and 2 Worker node
  - Clone the directory and run the following command:
    ```
    terraform init
    terraform plan
    terraform apply
    ```

System requirements:

  - Deployment environment must have Ansible `2.4.0+`
  - Master and nodes must have passwordless SSH access/or use keys in ansible.cfg




# Clone the directory 

# Modify the settings as per your need
-group_vars/all.yml - Select Calico or Flannel


