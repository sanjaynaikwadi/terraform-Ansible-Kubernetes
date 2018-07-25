# Terraform-Ansible-Kubernetes
How to install Kubernetes cluster using Terraform,Ansible and Kubeadm

Build a Kubernetes cluster using Ansible with kubeadm. The goal is easily install a Kubernetes cluster on machines running:

  - Ubuntu 16.04
  - CentOS 7
  - Debian 9

Google cloud SDK needs to be installed on your deployment machine, if your installing for first time then you can run the following command
 and follow the instruction
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
Ansible

  - Deployment environment must have Ansible `2.4.0+`
  - Make sure you specify private key path to make ssh connection to instances, I am assuming that you already have added your SSH key in googlecloud console, use the same username for making conncetion with specifying the private key
  - Modify the `host.ini`, add the Master and Worker node ip which you will the get from terraform output
    ```
    [master]
    35.202.154.208
    [node]
    35.192.64.78
    35.192.210.4
    [kube-cluster:children]
    master
    node

   [all:vars]
   ansible_connection=ssh
   ansible_ssh_user=sanjay.naikwadi
   ansible_ssh_private_key_file=<path_to_file>
   ```
  - Modify `group_vars/all.yml`, select the flannel or calico, I have used flannel

Once everything is set lets run the playbook
   ```
   $ ansible-playbook site.yaml
   ```


