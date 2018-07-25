# Terraform-Ansible-Kubernetes
How to install Kubernetes cluster using Terraform,Ansible and Kubeadm

Build a Kubernetes cluster using Ansible with kubeadm. The goal is easily install a Kubernetes cluster on machines running:

  - Ubuntu 16.04
  - CentOS 7
  - Debian 9

Terraform 

  - Deployment enviornment must have terraform installed 
  - Latest version can be downloaded from : https://www.terraform.io/
  - Terraform code is for Google Cloud
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


