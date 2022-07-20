# Terraform Ansible MS Azure Flask Web Application
[Reference-terraform](https://docs.microsoft.com/en-us/azure/developer/terraform/create-linux-virtual-machine-with-infrastructure)<br/>
This example provisions a Virtual Machine running Ubuntu 18.04.6 LTS with a Public IP Address and runs Ansible play-book over SSH<br>
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
To get the virtual machine public IP address at anytime
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
```
Excluded
In Azure: Vitual Machine->networking -> add  **inbound port rule(Port range:5000, Protocol:tcp, Name:Port_5000)**  
```
The application should be available at:<br/>
```
http://<public_ip_address>:5000
```
You shoud see something similar in your browser<br>
<img width="562" alt="Screenshot 2022-07-20 at 11 28 20" src="https://user-images.githubusercontent.com/43514418/179948546-46c2602a-9b57-4f9b-b4f6-4bc5367e6342.png"><br/>
You can test app with example images available [here](https://github.com/MasoudMoeini/Terraform-Ansible-MS-Azure-Flask-Web-Application/tree/main/example%20images%20)<br>

To delete resources
```
terraform destroy
```
```
rm ~/.ssh/ansbile*
```



