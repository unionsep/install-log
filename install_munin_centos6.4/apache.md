# install apache
**remove httpd**
```
yum info httpd
yum remove httpd
yum info httpd
```
***install httpd***
```
yum install wget gcc openssl openssl-devel
cd /usr/local/src
wget http://ftp.meisei-u.ac.jp/mirror/apache/dist//httpd/httpd-2.2.31.tar.gz
tar xzf httpd-2.2.31.tar.gz
cd httpd-2.2.31
./configure --prefix=/usr/local/apache2 --enable-so --enable-rewrite --enable-ssl
make
make install
vi /usr/local/apache2/conf/httpd.conf
  - ADD -> ServerName localhost:80
/usr/local/apache2/bin/apachectl start
  - test access [ It works! ]
```
