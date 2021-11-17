# Wireguard-Lite
Project to build Wireguard server on AWS Lightsail using Terraform

# Prerequisites
This project expects Terraform to be in your PATH and for Wireguard to already be installed. This project is not responsible for configuring your client machine but the config generated by this project could be taken to any other machine to connect to the Wireguard Server.<br/>

This was created using an AWS CLI profile named terraform, adjust "local-exec" in `instance.tf` accordingly and change the profile in `main.tf`.

## AWS Credentials
Install AWSCLI and use `aws configure` to setup your local credentials. This project as is will be using the default profile AWS credentials.<br/>

# Usage
## Create Server
Build the server and output your wg0-client.conf to your current directory.<br/>
`./deploy.sh`<br/>
You'll be left with your wg0-client.conf file to connect to your server. An init script runs on the server after deployment and a reboot occurs. After the reboot you can connect. I usually, after deployment, start with a `watch -n 1 nc -nvvz ip port` and wait until the reboot occurs and the netcat starts to succeed. <br/>

## Destroy Server
Teardown the server and delete all files associated with build.<br/>
`./destroy.sh`

# Notes
This project is intented to be ephemeral in nature and does not use Terraform remote state. Keep track of your terraform.tfstate file to ease in the cleanup later.<br/>
Starting project idea. https://github.com/flypenguin/terraform-quickvpn-wireguard-ec2

# Tools needed
[Terraform](https://www.terraform.io/downloads.html)<br/>
[Wireguard](https://www.wireguard.com/install/)
