#**FRONTEND**
#In this project the usage of frontend is nginx
#Install nginx
```
dnf install nginx -y
```
#Enable nginx
```
systemctl enable nginx
```
#Start Nginx
```
systemctl start nginx
```
#For removing the default content of web server .
```
rm -rf /usr/share/nginx/html*
```
#Downloading the frontend content
```
curl -o /tmp/frontend.zip  https://expense-builds.s3.us-east-1.amazonaws.com/expense-frontend-v2.zip

```
#Change the directory to extract the frontend
```
cd /usr/share/nginx/html
```
#unzip the frontend file
```
unzip /tmp/frontend.zip
```
#Create reverse proxy configuration
```
vim /etc/nginx/default.d/expense.conf
```
#Add the content
```
proxy_http_version 1.1;
location /api/ {proxy_pass "<backend IP ADDRESS>";}
location /health{
    stub_status on;
    access_log off;
}
```
#Restart Nginx server
```
systemctl restart mysql
```
