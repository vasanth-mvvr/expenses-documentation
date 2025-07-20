#**backend**
#Backend is based on the developers requirement .What ever the developer chooses we need to configure it.
#In this project Developers choosed the NodeJs with version 20.

#Disable the nodejs versions 
```
dnf module disable nodejs -y
```
#Enable version 20
```
dnf module enable nodejs:20 -y
```
#Install nodejs
```
dnf install nodejs -y
```
#Configure the application by adding the application user
```
adduser expense
```
#Make directory app 
```
mkdir /app
```
#Get the backend code 
```
curl -o /tmp/backend.zip https://expense-builds.s3.us-east-1.amazonaws.com/expense-backend-v2.zip

```
#Change to app directory and unzip the code
```
cd /app
unzip /tmp/backend.zip
```
#Install the dependencies
```
npm install
```
#Confingure the backend service
```
vim /etc/systemd/system/backend.service
```
#Script
```
[Unit]
Description = Backend Service

[Service] 
User=expense
Environment=DB_HOST="<MySql IP ADDRESS>"
ExecStart=/bin/node /app/index.js
SyslogIdentifier=backend

[Install]
WantedBy=multi-user.target
```
#Reload mysql
```
systemctl daemon-reload
```
#Install mysql
```
dnf install mysql -y
```
#Start and enable mysql
```
systemctl start mysql
systemctl enable mysql
```
#Load the schema
```
mysql -h "<mysql ip address>" -uroot -pExpenseApp@1 < /app/schema/backend.sql
```
#Restart mysql
```
systemctl restart mysql
```
