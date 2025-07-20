# expenses-documentation
#MySql commands

#This document consists of mysql server installation and setup of root password.

# **Installation command for mysql server **

#Checking weather mysql server is installed already
```
dnf list installation mysql-server -y
```
```
dnf install mysql-server -y
```
# **Services of mysql server**
#Start of mysql-server 
```
systemctl start mysqld
```
#Checking status of mysql server weather it is running properly or not
```
systemctl status mysqld
```
#Enabling mysql for automatic continuation of installation after restarting the terminal
```
systemctl enable mysqld
```
#Disabling mysql for manual installation after restarting the terminal
```
systemctl disable mysqld
```
# **Setting up the root password in order to use the database service**
```
mysql_secure_installation --set-root-pass ExpenseApp@1
```