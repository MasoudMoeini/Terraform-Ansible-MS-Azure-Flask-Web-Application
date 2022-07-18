# Terraform Ansible MS Azure Flask Web Application
[Reference](https://github.com/hashicorp/terraform-provider-azurerm/tree/main/examples/virtual-machines/virtual_machine/provisioners/linux)<br/>
This example provisions a Virtual Machine running Ubuntu 16.04-LTS with a Public IP Address and runs a remote-exec provisioner over SSH<br>
``` 
az login
```
```
terraform init
```
```
terraform plan 
```
```
terraform apply
```
```
terraform show
```
Verify the results<br/>
To use SSH to connect to the virtual machine, do the following steps:<br/>
To get the SSH private key and save it to a file
```
terraform output -raw tls_private_key > id_rsa
```
To get the virtual machine public IP address.
```
terraform output public_ip_address
```
Use SSH to connect to the virtual machine.
```
ssh -i id_rsa azureuser@<public_ip_address>
```
To delete resources
```
terraform destroy
```


