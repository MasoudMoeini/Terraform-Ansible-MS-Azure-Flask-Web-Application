# Terraform Ansible MS Azure Flask Web Application
[Reference-terraform](https://github.com/hashicorp/terraform-provider-azurerm/tree/main/examples/virtual-machines/virtual_machine/provisioners/linux)<br/>
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
optional, only in case of connection permission error
```
chmod 600 private.key 
```
Run Ansible play-book
```
ansible-playbook -u user -i <public_ip_address>, --private-key private.key flask.yaml
```
Use SSH to connect to the virtual machine manually 
```
ssh -i private.key  azureuser@<public_ip_address>
```
For error case-study look at [review](https://github.com/MasoudMoeini/Terraform-Ansible-MS-Azure-Flask-Web-Application/blob/main/review.txt) <br/>
In Azure: Vitual Machine->networking -> add  **inbound port rule(port range:5000, protocol:tcp, Name:Port_5000)**  <br/>
The application should be available at:<br/>
```
http://<public_ip_address>:5000
```
You shoud see something similar in your browser<br/>
<img width="393" alt="Screenshot 2022-07-20 at 10 43 01" src="https://user-images.githubusercontent.com/43514418/179939623-5ff4b61c-5a0d-470d-8882-9b98955c2585.png"> <br/>
You can test app with example images available [here](https://github.com/MasoudMoeini/Terraform-Ansible-MS-Azure-Flask-Web-Application/tree/main/example%20images%20)<br>

To delete resources
```
terraform destroy
```
```
rm ~/.ssh/ansbile*
```



