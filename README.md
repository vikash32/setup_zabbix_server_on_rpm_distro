#### Here is the set of commands which we need to run to set up the zabbix server on centos/Redhat 7, Simply copy paste is suffice.
```
sudo yum -y  install httpd
```
```
sudo systemctl start httpd.service
```
```
sudo systemctl enable httpd.service
```
```
sudo yum -y install mariadb-server mariadb
```
```
sudo systemctl start mariadb
```
```
sudo mysql_secure_installation
```
```
sudo systemctl enable mariadb.service
```
```
#Centos 7
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
```
```
yum -y install php56w* --skip-broken
```
```
sudo systemctl restart httpd.service
```
```
setenforce 0
```
```
sudo rpm -ivh http://repo.zabbix.com/zabbix/3.0/rhel/7/x86_64/zabbix-release-3.0-1.el7.noarch.rpm
```
```
sudo yum -y install zabbix-server-mysql zabbix-web-mysql
```
```
########## Setting up of Mysql username: root, password:root ##########
## Here creating user zabbix and database zabbix with root password ###

mysql -uroot -proot

mariadb > create database zabbix character set utf8; grant all privileges on zabbix.* to zabbix@localhost identified by 'root';flush privileges;quit;"
```
```
cd /usr/share/doc/zabbix-server-mysql-*/
```
```
gunzip create.sql.gz
```
```
mysql -uroot -proot zabbix < create.sql
```
```
echo "DBPassword=root" >> /etc/zabbix/zabbix_server.conf
```
#################################
```
Uncomment 'php_value date.timezone Asia/Kolkata' in /etc/httpd/conf.d/zabbix.conf 
```
```
sudo systemctl restart httpd
```
```
sudo systemctl restart zabbix-server
```
```
Now open http://localhost/zabbix
```
```
that's it , it's done
```
