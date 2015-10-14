# install munin
#### add epel repository
``` Bash
rpm -ivh http://ftp.riken.jp/Linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm
yum repolist -> error
vi /etc/yum.repos.d/epel.repo
  UNCOMMENT baseurl=http://download.fedoraproject.org/pub/epel/6/$basearch
  COMMENT #mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=epel-6&arch=$basearch
  CHANGE enabled=1 -> enabled=0
yum repolist -> success
```
#### install munin
``` Bash
yum --enablerepo=epel info munin munin-node
yum --enablerepo=epel install munin munin-node
cp /etc/httpd/conf.d/munin.conf /usr/local/apache2/conf/extra/
vi /usr/local/apache2/conf/extra/munin.conf
  ADD Alias /munin /var/www/html/munin
  ADD Options FollowSymLinks
  ADD AllowOverride None
  ADD Order allow,deny
  ADD Allow from all
  COMMENT #AuthUserFile /etc/munin/munin-htpasswd
  COMMENT #AuthName "Munin"
  COMMENT #AuthType Basic
  COMMENT #require valid-user
vi /usr/local/apache2/conf/httpd.conf
  ADD # munin
  ADD Include conf/extra/munin.conf
/usr/local/apache2/bin/apachectl configtest
service munin-node start
service httpd restart
```
#### add auto load
``` Bash
chkconfig munin-node on
```
#### change cgi place
``` Bash
vi /usr/local/apache2/conf/httpd.conf
  COMMENT # ScriptAlias /cgi-bin/ "/usr/local/apache2/cgi-bin/"
  ADD ScriptAlias /cgi-bin/ "/var/www/cgi-bin/"
  COMMENT
    #<Directory "/usr/local/apache2/cgi-bin">
    #    AllowOverride None
    #    Options None
    #    Order allow,deny
    #    Allow from all
    #</Directory>
  ADD
    <Directory "/var/www/cgi-bin">
        AllowOverride None
        Options ExecCGI
        Order allow,deny
        Allow from all
    </Directory>
/usr/local/apache2/bin/apachectl restart
```
#### set cgi
> change this repository munin.conf

``` Bash
chgrp apache /usr/share/munin/munin-graph
chgrp apache /var/log/munin /var/log/munin/munin-graph.log
chmod g+w /var/log/munin /var/log/munin/munin-graph.log
chgrp -R apache /var/www/html/munin/
vi /etc/munin/munin.conf
  COMMENT # graph_strategy cron
  ADD graph_strategy cgi
  COMMENT # html_strategy cron
  ADD html_strategy cgi
```
#### set rrechached
``` Bash
cd /usr/local/src
wget http://pkgs.repoforge.org/rrdtool/rrdtool-1.4.7-1.el6.rfx.x86_64.rpm
wget http://pkgs.repoforge.org/rrdtool/perl-rrdtool-1.4.7-1.el6.rfx.x86_64.rpm
yum info libdbi ruby
yum install libdbi ruby
rpm -Uvh ./rrdtool-1.4.7-1.el6.rfx.x86_64.rpm ./perl-rrdtool-1.4.7-1.el6.rfx.x86_64.rpm
vi /etc/sysconfig/rrdcached
  COMMENT # OPTIONS="-l unix:/var/rrdtool/rrdcached/rrdcached.sock -s rrdcached -m 664 -b /var/rrdtool/rrdcached"
  ADD OPTIONS="-l unix:/var/rrdtool/rrdcached/rrdcached.sock -l 127.0.0.1 -s apache -m 664 -b /var/rrdtool/rrdcached -F -j /var/lib/munin/rrdcached-journal -w 1800 -z 1800 -f 3600"
  COMMENT # RRDC_USER=rrdcached
  ADD RRDC_USER=munin
vi /etc/init.d/rrdcached
  (start() L34)
  ADD chgrp apache /var/rrdtool/rrdcached/rrdcached.sock
  ADD chmod g+w /var/rrdtool/rrdcached/rrdcached.sock
mkdir /var/lib/munin/rrdcached-journal
chown munin.munin /var/lib/munin/rrdcached-journal
chown munin.munin /var/rrdtool/rrdcached/
lsof -i:42217
vi /etc/munin/munin.conf
  ADD rrdcached_socket /var/rrdtool/rrdcached/rrdcached.sock
```
#### change tenmplate (munstrap)
> https://github.com/jonnymccullagh/munstrap

##### install git
``` Bash
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel perl-ExtUtils-MakeMaker
cd /usr/local/src
wget https://www.kernel.org/pub/software/scm/git/git-2.4.0.tar.gz
tar xzf git-2.4.0.tar.gz
cd git-2.4.0
make prefix=/usr/local all
make prefix=/usr/local install
git --version -> git version 2.4.0
```
##### clone
``` Bash
mkdir ~/git
cd ~/git
git clone https://github.com/munin-monitoring/contrib.git
cd /etc/munin/
cp -rb ~/git/contrib/templates/munstrap/templates .
rm -rf /var/www/html/munin/*
sudo -u munin /usr/bin/munin-cron
```
