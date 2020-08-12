simple user data for webpage showing the InstanceID

```
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
cd /var/www/html
wget https://raw.githubusercontent.com/ashydv/aws-labs/master/index.txt
ID=`curl http://169.254.169.254/latest/meta-data/instance-id`
sed "s/ID/$ID/" index.txt
PRIVATEIP=`curl http://169.254.169.254/latest/meta-data/local-ipv4`
sed "s/PRIVATEIP/$PRIVATEIP/" index.txt
PUBLICIP=`curl http://169.254.169.254/latest/meta-data/public-ipv4`
sed "s/PUBLICIP/$PUBLICIP/" index.txt > index.html
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
