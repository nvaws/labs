Basic user data script showing some of instance metadata fields on the webpage, works with Amazon Linux 2

```
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
cd /var/www/html
wget https://raw.githubusercontent.com/ashydv/aws-labs/master/index.txt
INSTANCEID=`curl http://169.254.169.254/latest/meta-data/instance-id`
sed "s/INSTANCEID/$INSTANCEID/" index.txt > index0.txt
INSTANCETYPE=`curl http://169.254.169.254/latest/meta-data/instance-type`
sed "s/INSTANCETYPE/$INSTANCETYPE/" index0.txt > index1.txt
PRIVATEIP=`curl http://169.254.169.254/latest/meta-data/local-ipv4`
sed "s/PRIVATEIP/$PRIVATEIP/" index1.txt > index2.txt
PUBLICIP=`curl http://169.254.169.254/latest/meta-data/public-ipv4`
sed "s/PUBLICIP/$PUBLICIP/" index2.txt > index.html
```

user data for Windows to enable IIS server

```
<powershell>
Set-ExecutionPolicy Unrestricted -Force
New-Item -ItemType directory -Path 'C:\temp'
 
# Install IIS and Web Management Tools.
Import-Module ServerManager
install-windowsfeature web-server, web-webserver -IncludeAllSubFeature
install-windowsfeature web-mgmt-tools
</powershell>
```

user data (Cloud init) to install apache on linux

```
#cloud-config
repo_update: true
repo_upgrade: all

packages:
 - httpd

runcmd:
 - systemctl start httpd
 - sudo systemctl enable httpd
```
