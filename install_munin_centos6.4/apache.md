# Install Apache
#### remove httpd
``` Bash
yum info httpd
yum remove httpd
yum info httpd
```
#### install httpd from sorce
``` Bash
yum install wget gcc openssl openssl-devel
cd /usr/local/src
wget http://ftp.meisei-u.ac.jp/mirror/apache/dist//httpd/httpd-2.2.31.tar.gz
tar xzf httpd-2.2.31.tar.gz
cd httpd-2.2.31
./configure --prefix=/usr/local/apache2 --enable-so --enable-rewrite --enable-ssl
make
make install
vi /usr/local/apache2/conf/httpd.conf
  ADD -> ServerName localhost:80
/usr/local/apache2/bin/apachectl start
  test access [ It works! ]
```
#### change user
``` Bash
vi /usr/local/apache2/conf/httpd.conf
  COMMENT # User daemon
  COMMENT # Group daemon
  ADD User apache
  ADD Group apache
/usr/local/apache2/bin/apachectl restart
```
#### add mod_expires_module
``` Bash
cd /usr/local/src/httpd-2.2.31/modules/metadata/
/usr/local/apache2/bin/apxs -c mod_expires.c
/usr/local/apache2/bin/apxs -ian expires mod_expires.la
/usr/local/apache2/bin/apachectl graceful
```
#### add service
``` Bash
/usr/local/apache2/bin/apachectl stop
cp /usr/local/src/httpd-2.2.31/build/rpm/httpd.init /etc/rc.d/init.d/httpd
vi /etc/rc.d/init.d/httpd
  COMMENT # httpd=${HTTPD-/usr/sbin/httpd}
  ADD httpd=${HTTPD-/usr/local/apache2/bin/httpd}
  COMMENT # pidfile=${PIDFILE-/var/log/httpd/${prog}.pid}
  ADD pidfile=${PIDFILE-/usr/local/apache2/logs/httpd.pid}
  COMMENT # CONFFILE=/etc/httpd/conf/httpd.conf
  ADD CONFFILE=/usr/local/apache2/conf/httpd.conf
service httpd start
test access [ It works! ]
service httpd stop
```
#### add auto load
``` Bash
chkconfig --add httpd
chkconfig httpd on
```
