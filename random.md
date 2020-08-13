Basic user data script showing some of instance metadata fields on the webpage, works with Amazon Linux 2

```
Content-Type: multipart/mixed; boundary="//"
MIME-Version: 1.0

--//
Content-Type: text/cloud-config; charset="us-ascii"
MIME-Version: 1.0
Content-Transfer-Encoding: 7bit
Content-Disposition: attachment; filename="cloud-config.txt"

#cloud-config
cloud_final_modules:
- [scripts-user, always]

--//
Content-Type: text/x-shellscript; charset="us-ascii"
MIME-Version: 1.0
Content-Transfer-Encoding: 7bit
Content-Disposition: attachment; filename="userdata.txt"

#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
cd /var/www/html
wget https://raw.githubusercontent.com/ashydv/aws-labs/master/index.txt
INSTANCEID=`curl http://169.254.169.254/latest/meta-data/instance-id`
INSTANCETYPE=`curl http://169.254.169.254/latest/meta-data/instance-type`
PRIVATEIP=`curl http://169.254.169.254/latest/meta-data/local-ipv4`
PUBLICIP=`curl http://169.254.169.254/latest/meta-data/public-ipv4`
sed -e "s/INSTANCEID/$INSTANCEID/" -e "s/INSTANCETYPE/$INSTANCETYPE/" -e "s/PRIVATEIP/$PRIVATEIP/" -e "s/PUBLICIP/$PUBLICIP/" index.txt > index.html
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
