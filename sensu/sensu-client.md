```sh
[root@vm02 ~]# vi /etc/yum.repos.d/sensu.repo
[root@vm02 ~]# yum install sensu
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.vodien.com
 * extras: ftp.jaist.ac.jp
 * updates: ftp.jaist.ac.jp
sensu                                                                         |  951 B     00:00
sensu/primary                                                                 |  33 kB     00:00
sensu                                                                                          75/75
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package sensu.x86_64 1:0.20.3-1 set to be updated
--> Finished Dependency Resolution

Dependencies Resolved

=====================================================================================================
 Package               Arch                   Version                    Repository             Size
=====================================================================================================
Installing:
 sensu                 x86_64                 1:0.20.3-1                 sensu                  21 M

Transaction Summary
=====================================================================================================
Install       1 Package(s)
Upgrade       0 Package(s)

Total download size: 21 M
{
Is this ok [y/N]: y
{
Downloading Packages:
sensu-0.20.3-1.x86_64.rpm                                                     |  21 MB     00:09
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     : sensu                                                                         1/1

Installed:
  sensu.x86_64 1:0.20.3-1

Complete!
[root@vm02 ~]# mkdir -p /etc/sensu/ssl
[root@vm02 ~]# passwd root
Changing password for user root.
New UNIX password:
BAD PASSWORD: it is too short
Retype new UNIX password:
passwd: all authentication tokens updated successfully.
[root@vm02 ~]# vi /etc/sensu/conf.d/rabbitmq.json
[root@vm02 ~]# vi /etc/sensu/conf.d/client.json
[root@vm02 ~]# /sbin/service sensu-client start
Starting sensu-client                                      [  OK  ]
[root@vm02 ~]# yum install ntp
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.vodien.com
 * extras: ftp.jaist.ac.jp
 * updates: ftp.jaist.ac.jp
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package ntp.x86_64 0:4.2.2p1-18.el5.centos set to be updated
--> Finished Dependency Resolution

Dependencies Resolved

=====================================================================================================
 Package          Arch                Version                             Repository            Size
=====================================================================================================
Installing:
 ntp              x86_64              4.2.2p1-18.el5.centos               updates              1.3 M

Transaction Summary
=====================================================================================================
Install       1 Package(s)
Upgrade       0 Package(s)

Total download size: 1.3 M
Is this ok [y/N]: y
Downloading Packages:
ntp-4.2.2p1-18.el5.centos.x86_64.rpm                                          | 1.3 MB     00:00
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     : ntp                                                                           1/1

Installed:
  ntp.x86_64 0:4.2.2p1-18.el5.centos

Complete!
[root@vm02 ~]# /sbin/ntpdate ntp.nict.jp
17 Jun 20:56:15 ntpdate[10004]: step time server 133.243.238.244 offset 2153.405316 sec
```
