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
terraform output -raw tls_private_key > private.key 
```
To get the virtual machine public IP address.
```
terraform output public_ip_address
```
```
chmod 600 private.key 
```
Use SSH to connect to the virtual machine.
```
ssh -i private.key  azureuser@<public_ip_address>
```
```
ansible-playbook -u user -i <public_ip_address>, --private-key private.key flask.yaml
```
The application should be available at:
```
http://<public_ip_address>
```
To delete resources
```
terraform destroy
```


