```sh
[root@ansible vagrant]# cd /tmp/
[root@ansible tmp]# ll
合計 64
-rwx------. 1 root    root       29  5月  4 16:27 2014 ks-script-nR80gm
-rwxr-xr-x. 1 root    root      143  5月  4 16:28 2014 ks-script-nR80gm.log
-rwxrwxrwx  1 root    root      110  5月  4 22:31 2014 script.sh
-rw-r--r--  1 root    root    46132  5月  4 16:30 2014 stderr
-rwx--x--x  1 vagrant vagrant   256  6月 17 06:35 2016 vagrant-shell
-rw-------. 1 root    root        0  5月  4 16:25 2014 yum.log
[root@ansible tmp]# wget http://sensuapp.org/docs/0.25/tools/ssl_certs.tar
--2016-06-17 06:38:15--  http://sensuapp.org/docs/0.25/tools/ssl_certs.tar
sensuapp.org をDNSに問いあわせています... 54.225.184.201, 54.235.177.126, 54.235.97.39
sensuapp.org|54.225.184.201|:80 に接続しています... 接続しました。
HTTP による接続要求を送信しました、応答を待っています... 301 Moved Permanently
場所: https://sensuapp.org/docs/0.25/tools/ssl_certs.tar [続く]
--2016-06-17 06:38:15--  https://sensuapp.org/docs/0.25/tools/ssl_certs.tar
sensuapp.org|54.225.184.201|:443 に接続しています... 接続しました。
HTTP による接続要求を送信しました、応答を待っています... 200 OK
長さ: 7681 (7.5K) [application/x-tar]
`ssl_certs.tar' に保存中

100%[======================================================================================================================>] 7,681       --.-K/s 時間 0s

2016-06-17 06:38:16 (99.0 MB/s) - `ssl_certs.tar' へ保存完了 [7681/7681]

[root@ansible tmp]# ll
合計 72
-rwx------. 1 root    root       29  5月  4 16:27 2014 ks-script-nR80gm
-rwxr-xr-x. 1 root    root      143  5月  4 16:28 2014 ks-script-nR80gm.log
-rwxrwxrwx  1 root    root      110  5月  4 22:31 2014 script.sh
-rw-r--r--  1 root    root     7681  6月 17 00:43 2016 ssl_certs.tar
-rw-r--r--  1 root    root    46132  5月  4 16:30 2014 stderr
-rwx--x--x  1 vagrant vagrant   256  6月 17 06:35 2016 vagrant-shell
-rw-------. 1 root    root        0  5月  4 16:25 2014 yum.log
[root@ansible tmp]# tar xzf ssl_certs.tar

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
[root@ansible tmp]# tar xvf ssl_certs.tar
ssl_certs/
ssl_certs/sensu_ca/
ssl_certs/ssl_certs.sh
ssl_certs/sensu_ca/openssl.cnf
[root@ansible tmp]# ll
合計 76
-rwx------. 1 root    root       29  5月  4 16:27 2014 ks-script-nR80gm
-rwxr-xr-x. 1 root    root      143  5月  4 16:28 2014 ks-script-nR80gm.log
-rwxrwxrwx  1 root    root      110  5月  4 22:31 2014 script.sh
drwxr-xr-x  3     501 wheel    4096 12月  4 21:01 2013 ssl_certs
-rw-r--r--  1 root    root     7681  6月 17 00:43 2016 ssl_certs.tar
-rw-r--r--  1 root    root    46132  5月  4 16:30 2014 stderr
-rwx--x--x  1 vagrant vagrant   256  6月 17 06:35 2016 vagrant-shell
-rw-------. 1 root    root        0  5月  4 16:25 2014 yum.log
[root@ansible tmp]# cd ssl_certs
[root@ansible ssl_certs]# ll
合計 8
drwxr-xr-x 2 501 wheel 4096  6月 17 06:38 2016 sensu_ca
-rwxr-xr-x 1 501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# ./ssl_certs.sh generate
Generating SSL certificates for Sensu ...
Generating a 2048 bit RSA private key
...............................................................................+++
...........................+++
writing new private key to './private/cakey.pem'
-----
Generating RSA private key, 2048 bit long modulus
..................................................................................+++
............................................................+++
e is 65537 (0x10001)
Using configuration from openssl.cnf
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
commonName            :ASN.1 12:'sensu'
organizationName      :ASN.1 12:'server'
Certificate is to be certified until Jun 16 06:39:09 2021 GMT (1825 days)

Write out database with 1 new entries
Data Base Updated
Generating RSA private key, 2048 bit long modulus
..............................................................................+++
.....+++
e is 65537 (0x10001)
Using configuration from openssl.cnf
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
commonName            :ASN.1 12:'sensu'
organizationName      :ASN.1 12:'client'
Certificate is to be certified until Jun 16 06:39:09 2021 GMT (1825 days)

Write out database with 1 new entries
Data Base Updated
[root@ansible ssl_certs]# yum install erlang
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: ftp.riken.jp
 * epel: ftp.riken.jp
 * extras: ftp.riken.jp
 * updates: ftp.jaist.ac.jp
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package erlang.x86_64 0:R14B-04.3.el6 will be installed
--> Processing Dependency: erlang-xmerl(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-wx(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-webtool(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-typer(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-tv(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-tools(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-toolbar(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-test_server(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-syntax_tools(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-stdlib(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-ssl(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-ssh(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-snmp(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-sasl(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-runtime_tools(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-reltool(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-public_key(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-pman(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-percept(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-parsetools(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-otp_mibs(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-os_mon(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-orber(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-odbc(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-observer(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-mnesia(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-megaco(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-kernel(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-jinterface(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-inviso(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-inets(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-ic(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-hipe(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-gs(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-examples(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-eunit(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-et(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-erts(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-erl_interface(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-erl_docgen(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-edoc(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-docbuilder(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-diameter(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-dialyzer(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-debugger(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-crypto(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-cosTransactions(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-cosTime(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-cosProperty(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-cosNotification(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-cosFileTransfer(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-cosEventDomain(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-cosEvent(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-compiler(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-common_test(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-asn1(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Processing Dependency: erlang-appmon(x86-64) = R14B-04.3.el6 for package: erlang-R14B-04.3.el6.x86_64
--> Running transaction check
---> Package erlang-appmon.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-asn1.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-common_test.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-compiler.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-cosEvent.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-cosEventDomain.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-cosFileTransfer.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-cosNotification.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-cosProperty.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-cosTime.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-cosTransactions.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-crypto.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-debugger.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-dialyzer.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-diameter.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-docbuilder.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-edoc.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-erl_docgen.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-erl_interface.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-erts.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-et.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-eunit.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-examples.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-gs.x86_64 0:R14B-04.3.el6 will be installed
--> Processing Dependency: tk for package: erlang-gs-R14B-04.3.el6.x86_64
---> Package erlang-hipe.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-ic.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-inets.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-inviso.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-jinterface.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-kernel.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-megaco.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-mnesia.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-observer.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-odbc.x86_64 0:R14B-04.3.el6 will be installed
--> Processing Dependency: libodbc.so.2()(64bit) for package: erlang-odbc-R14B-04.3.el6.x86_64
---> Package erlang-orber.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-os_mon.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-otp_mibs.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-parsetools.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-percept.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-pman.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-public_key.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-reltool.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-runtime_tools.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-sasl.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-snmp.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-ssh.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-ssl.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-stdlib.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-syntax_tools.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-test_server.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-toolbar.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-tools.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-tv.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-typer.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-webtool.x86_64 0:R14B-04.3.el6 will be installed
---> Package erlang-wx.x86_64 0:R14B-04.3.el6 will be installed
--> Processing Dependency: mesa-libGLU for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: mesa-libGL for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_xrc-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_stc-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_html-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_gl-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_core-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_aui-2.8.so.0(WXU_2.8.5)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_aui-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_adv-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_baseu-2.8.so.0(WXU_2.8)(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_xrc-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_stc-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_html-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_gl-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_core-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_aui-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_gtk2u_adv-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_baseu_xml-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libwx_baseu-2.8.so.0()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libGLU.so.1()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
--> Processing Dependency: libGL.so.1()(64bit) for package: erlang-wx-R14B-04.3.el6.x86_64
---> Package erlang-xmerl.x86_64 0:R14B-04.3.el6 will be installed
--> Running transaction check
---> Package mesa-libGL.x86_64 0:11.0.7-4.el6 will be installed
--> Processing Dependency: mesa-dri-drivers(x86-64) = 11.0.7-4.el6 for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libX11 > 1.6 for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libxcb.so.1()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libxcb-glx.so.0()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libxcb-dri2.so.0()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libglapi.so.0()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libXxf86vm.so.1()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libXfixes.so.3()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libXext.so.6()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libXdamage.so.1()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libX11.so.6()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
--> Processing Dependency: libX11-xcb.so.1()(64bit) for package: mesa-libGL-11.0.7-4.el6.x86_64
---> Package mesa-libGLU.x86_64 0:11.0.7-4.el6 will be installed
---> Package tk.x86_64 1:8.5.7-5.el6 will be installed
--> Processing Dependency: tcl = 1:8.5.7 for package: 1:tk-8.5.7-5.el6.x86_64
--> Processing Dependency: libtcl8.5.so()(64bit) for package: 1:tk-8.5.7-5.el6.x86_64
--> Processing Dependency: libfreetype.so.6()(64bit) for package: 1:tk-8.5.7-5.el6.x86_64
--> Processing Dependency: libfontconfig.so.1()(64bit) for package: 1:tk-8.5.7-5.el6.x86_64
--> Processing Dependency: libXrender.so.1()(64bit) for package: 1:tk-8.5.7-5.el6.x86_64
--> Processing Dependency: libXft.so.2()(64bit) for package: 1:tk-8.5.7-5.el6.x86_64
---> Package unixODBC.x86_64 0:2.2.14-14.el6 will be installed
--> Processing Dependency: libltdl.so.7()(64bit) for package: unixODBC-2.2.14-14.el6.x86_64
---> Package wxBase.x86_64 0:2.8.12-1.el6.centos will be installed
---> Package wxGTK.x86_64 0:2.8.12-1.el6.centos will be installed
--> Processing Dependency: libpng12.so.0(PNG12_0)(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libtiff.so.3()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libpng12.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libpangoft2-1.0.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libpango-1.0.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libjpeg.so.62()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libgtk-x11-2.0.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libgdk_pixbuf-2.0.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libgdk-x11-2.0.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libatk-1.0.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libXinerama.so.1()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libSM.so.6()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
--> Processing Dependency: libSDL-1.2.so.0()(64bit) for package: wxGTK-2.8.12-1.el6.centos.x86_64
---> Package wxGTK-gl.x86_64 0:2.8.12-1.el6.centos will be installed
--> Running transaction check
---> Package SDL.x86_64 0:1.2.14-7.el6_7.1 will be installed
---> Package atk.x86_64 0:1.30.0-1.el6 will be installed
---> Package fontconfig.x86_64 0:2.8.0-5.el6 will be installed
---> Package freetype.x86_64 0:2.3.11-17.el6 will be installed
---> Package gdk-pixbuf2.x86_64 0:2.24.1-6.el6_7 will be installed
--> Processing Dependency: libjasper.so.1()(64bit) for package: gdk-pixbuf2-2.24.1-6.el6_7.x86_64
---> Package gtk2.x86_64 0:2.24.23-8.el6 will be installed
--> Processing Dependency: libXrandr >= 1.2.99.4-2 for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: glib2 >= 2.28.0-1 for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: hicolor-icon-theme for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: libcups.so.2()(64bit) for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: libcairo.so.2()(64bit) for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: libXrandr.so.2()(64bit) for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: libXi.so.6()(64bit) for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: libXcursor.so.1()(64bit) for package: gtk2-2.24.23-8.el6.x86_64
--> Processing Dependency: libXcomposite.so.1()(64bit) for package: gtk2-2.24.23-8.el6.x86_64
---> Package libSM.x86_64 0:1.2.1-2.el6 will be installed
--> Processing Dependency: libICE.so.6()(64bit) for package: libSM-1.2.1-2.el6.x86_64
---> Package libX11.x86_64 0:1.6.3-2.el6 will be installed
--> Processing Dependency: libX11-common = 1.6.3-2.el6 for package: libX11-1.6.3-2.el6.x86_64
---> Package libXdamage.x86_64 0:1.1.3-4.el6 will be installed
---> Package libXext.x86_64 0:1.3.3-1.el6 will be installed
---> Package libXfixes.x86_64 0:5.0.1-2.1.el6 will be installed
---> Package libXft.x86_64 0:2.3.2-1.el6 will be installed
---> Package libXinerama.x86_64 0:1.1.3-2.1.el6 will be installed
---> Package libXrender.x86_64 0:0.9.8-2.1.el6_8.1 will be installed
---> Package libXxf86vm.x86_64 0:1.1.3-2.1.el6 will be installed
---> Package libjpeg-turbo.x86_64 0:1.2.1-3.el6_5 will be installed
---> Package libpng.x86_64 2:1.2.49-2.el6_7 will be installed
---> Package libtiff.x86_64 0:3.9.4-10.el6_5 will be installed
---> Package libtool-ltdl.x86_64 0:2.2.6-15.5.el6 will be installed
---> Package libxcb.x86_64 0:1.11-2.el6 will be installed
--> Processing Dependency: libXau.so.6()(64bit) for package: libxcb-1.11-2.el6.x86_64
---> Package mesa-dri-drivers.x86_64 0:11.0.7-4.el6 will be installed
--> Processing Dependency: mesa-dri1-drivers >= 7.11-6 for package: mesa-dri-drivers-11.0.7-4.el6.x86_64
--> Processing Dependency: mesa-dri-filesystem(x86-64) for package: mesa-dri-drivers-11.0.7-4.el6.x86_64
--> Processing Dependency: libLLVM-3.6-mesa.so(libLLVM-3.6-mesa.so)(64bit) for package: mesa-dri-drivers-11.0.7-4.el6.x86_64
--> Processing Dependency: libdrm_amdgpu.so.1()(64bit) for package: mesa-dri-drivers-11.0.7-4.el6.x86_64
--> Processing Dependency: libLLVM-3.6-mesa.so()(64bit) for package: mesa-dri-drivers-11.0.7-4.el6.x86_64
---> Package pango.x86_64 0:1.28.1-11.el6 will be installed
--> Processing Dependency: libthai >= 0.1.9 for package: pango-1.28.1-11.el6.x86_64
--> Processing Dependency: libthai.so.0(LIBTHAI_0.1)(64bit) for package: pango-1.28.1-11.el6.x86_64
--> Processing Dependency: libthai.so.0()(64bit) for package: pango-1.28.1-11.el6.x86_64
---> Package tcl.x86_64 1:8.5.7-6.el6 will be installed
--> Running transaction check
---> Package cairo.x86_64 0:1.8.8-6.el6_6 will be installed
--> Processing Dependency: libpixman-1.so.0()(64bit) for package: cairo-1.8.8-6.el6_6.x86_64
---> Package cups-libs.x86_64 1:1.4.2-74.el6 will be installed
--> Processing Dependency: libgnutls.so.26(GNUTLS_1_4)(64bit) for package: 1:cups-libs-1.4.2-74.el6.x86_64
--> Processing Dependency: libgnutls.so.26()(64bit) for package: 1:cups-libs-1.4.2-74.el6.x86_64
--> Processing Dependency: libavahi-common.so.3()(64bit) for package: 1:cups-libs-1.4.2-74.el6.x86_64
--> Processing Dependency: libavahi-client.so.3()(64bit) for package: 1:cups-libs-1.4.2-74.el6.x86_64
---> Package glib2.x86_64 0:2.26.1-3.el6 will be updated
---> Package glib2.x86_64 0:2.28.8-5.el6 will be an update
---> Package hicolor-icon-theme.noarch 0:0.11-1.1.el6 will be installed
---> Package jasper-libs.x86_64 0:1.900.1-16.el6_6.3 will be installed
---> Package libICE.x86_64 0:1.0.6-1.el6 will be installed
---> Package libX11-common.noarch 0:1.6.3-2.el6 will be installed
---> Package libXau.x86_64 0:1.0.6-4.el6 will be installed
---> Package libXcomposite.x86_64 0:0.4.3-4.el6 will be installed
---> Package libXcursor.x86_64 0:1.1.14-2.1.el6 will be installed
---> Package libXi.x86_64 0:1.7.4-1.el6 will be installed
---> Package libXrandr.x86_64 0:1.4.2-1.el6 will be installed
---> Package libdrm.x86_64 0:2.4.45-2.el6 will be updated
---> Package libdrm.x86_64 0:2.4.65-2.el6 will be an update
---> Package libthai.x86_64 0:0.1.12-3.el6 will be installed
---> Package mesa-dri-filesystem.x86_64 0:11.0.7-4.el6 will be installed
---> Package mesa-dri1-drivers.x86_64 0:7.11-8.el6 will be installed
---> Package mesa-private-llvm.x86_64 0:3.6.2-1.el6 will be installed
--> Running transaction check
---> Package avahi-libs.x86_64 0:0.6.25-15.el6 will be installed
---> Package gnutls.x86_64 0:2.8.5-19.el6_7 will be installed
---> Package pixman.x86_64 0:0.32.8-1.el6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================================================================================================
 Package                                       Arch                          Version                                       Repository                      Size
================================================================================================================================================================
Installing:
 erlang                                        x86_64                        R14B-04.3.el6                                 epel                            26 k
Installing for dependencies:
 SDL                                           x86_64                        1.2.14-7.el6_7.1                              base                           193 k
 atk                                           x86_64                        1.30.0-1.el6                                  base                           195 k
 avahi-libs                                    x86_64                        0.6.25-15.el6                                 base                            55 k
 cairo                                         x86_64                        1.8.8-6.el6_6                                 base                           309 k
 cups-libs                                     x86_64                        1:1.4.2-74.el6                                base                           322 k
 erlang-appmon                                 x86_64                        R14B-04.3.el6                                 epel                           145 k
 erlang-asn1                                   x86_64                        R14B-04.3.el6                                 epel                           993 k
 erlang-common_test                            x86_64                        R14B-04.3.el6                                 epel                           508 k
 erlang-compiler                               x86_64                        R14B-04.3.el6                                 epel                           987 k
 erlang-cosEvent                               x86_64                        R14B-04.3.el6                                 epel                           149 k
 erlang-cosEventDomain                         x86_64                        R14B-04.3.el6                                 epel                           113 k
 erlang-cosFileTransfer                        x86_64                        R14B-04.3.el6                                 epel                           168 k
 erlang-cosNotification                        x86_64                        R14B-04.3.el6                                 epel                           718 k
 erlang-cosProperty                            x86_64                        R14B-04.3.el6                                 epel                           161 k
 erlang-cosTime                                x86_64                        R14B-04.3.el6                                 epel                           106 k
 erlang-cosTransactions                        x86_64                        R14B-04.3.el6                                 epel                           164 k
 erlang-crypto                                 x86_64                        R14B-04.3.el6                                 epel                            50 k
 erlang-debugger                               x86_64                        R14B-04.3.el6                                 epel                           440 k
 erlang-dialyzer                               x86_64                        R14B-04.3.el6                                 epel                           567 k
 erlang-diameter                               x86_64                        R14B-04.3.el6                                 epel                           449 k
 erlang-docbuilder                             x86_64                        R14B-04.3.el6                                 epel                           192 k
 erlang-edoc                                   x86_64                        R14B-04.3.el6                                 epel                           301 k
 erlang-erl_docgen                             x86_64                        R14B-04.3.el6                                 epel                           109 k
 erlang-erl_interface                          x86_64                        R14B-04.3.el6                                 epel                           149 k
 erlang-erts                                   x86_64                        R14B-04.3.el6                                 epel                           2.0 M
 erlang-et                                     x86_64                        R14B-04.3.el6                                 epel                           197 k
 erlang-eunit                                  x86_64                        R14B-04.3.el6                                 epel                           139 k
 erlang-examples                               x86_64                        R14B-04.3.el6                                 epel                           832 k
 erlang-gs                                     x86_64                        R14B-04.3.el6                                 epel                           608 k
 erlang-hipe                                   x86_64                        R14B-04.3.el6                                 epel                           1.0 M
 erlang-ic                                     x86_64                        R14B-04.3.el6                                 epel                           845 k
 erlang-inets                                  x86_64                        R14B-04.3.el6                                 epel                           749 k
 erlang-inviso                                 x86_64                        R14B-04.3.el6                                 epel                           154 k
 erlang-jinterface                             x86_64                        R14B-04.3.el6                                 epel                            95 k
 erlang-kernel                                 x86_64                        R14B-04.3.el6                                 epel                           1.0 M
 erlang-megaco                                 x86_64                        R14B-04.3.el6                                 epel                           7.8 M
 erlang-mnesia                                 x86_64                        R14B-04.3.el6                                 epel                           662 k
 erlang-observer                               x86_64                        R14B-04.3.el6                                 epel                           205 k
 erlang-odbc                                   x86_64                        R14B-04.3.el6                                 epel                            59 k
 erlang-orber                                  x86_64                        R14B-04.3.el6                                 epel                           909 k
 erlang-os_mon                                 x86_64                        R14B-04.3.el6                                 epel                           104 k
 erlang-otp_mibs                               x86_64                        R14B-04.3.el6                                 epel                            28 k
 erlang-parsetools                             x86_64                        R14B-04.3.el6                                 epel                           164 k
 erlang-percept                                x86_64                        R14B-04.3.el6                                 epel                           140 k
 erlang-pman                                   x86_64                        R14B-04.3.el6                                 epel                           105 k
 erlang-public_key                             x86_64                        R14B-04.3.el6                                 epel                           402 k
 erlang-reltool                                x86_64                        R14B-04.3.el6                                 epel                           296 k
 erlang-runtime_tools                          x86_64                        R14B-04.3.el6                                 epel                           210 k
 erlang-sasl                                   x86_64                        R14B-04.3.el6                                 epel                           263 k
 erlang-snmp                                   x86_64                        R14B-04.3.el6                                 epel                           1.5 M
 erlang-ssh                                    x86_64                        R14B-04.3.el6                                 epel                           361 k
 erlang-ssl                                    x86_64                        R14B-04.3.el6                                 epel                           378 k
 erlang-stdlib                                 x86_64                        R14B-04.3.el6                                 epel                           2.1 M
 erlang-syntax_tools                           x86_64                        R14B-04.3.el6                                 epel                           317 k
 erlang-test_server                            x86_64                        R14B-04.3.el6                                 epel                           272 k
 erlang-toolbar                                x86_64                        R14B-04.3.el6                                 epel                            49 k
 erlang-tools                                  x86_64                        R14B-04.3.el6                                 epel                           535 k
 erlang-tv                                     x86_64                        R14B-04.3.el6                                 epel                           377 k
 erlang-typer                                  x86_64                        R14B-04.3.el6                                 epel                            58 k
 erlang-webtool                                x86_64                        R14B-04.3.el6                                 epel                            45 k
 erlang-wx                                     x86_64                        R14B-04.3.el6                                 epel                           2.4 M
 erlang-xmerl                                  x86_64                        R14B-04.3.el6                                 epel                           939 k
 fontconfig                                    x86_64                        2.8.0-5.el6                                   base                           186 k
 freetype                                      x86_64                        2.3.11-17.el6                                 base                           361 k
 gdk-pixbuf2                                   x86_64                        2.24.1-6.el6_7                                base                           501 k
 gnutls                                        x86_64                        2.8.5-19.el6_7                                base                           347 k
 gtk2                                          x86_64                        2.24.23-8.el6                                 base                           3.2 M
 hicolor-icon-theme                            noarch                        0.11-1.1.el6                                  base                            40 k
 jasper-libs                                   x86_64                        1.900.1-16.el6_6.3                            base                           137 k
 libICE                                        x86_64                        1.0.6-1.el6                                   base                            53 k
 libSM                                         x86_64                        1.2.1-2.el6                                   base                            37 k
 libX11                                        x86_64                        1.6.3-2.el6                                   base                           586 k
 libX11-common                                 noarch                        1.6.3-2.el6                                   base                           169 k
 libXau                                        x86_64                        1.0.6-4.el6                                   base                            24 k
 libXcomposite                                 x86_64                        0.4.3-4.el6                                   base                            20 k
 libXcursor                                    x86_64                        1.1.14-2.1.el6                                base                            28 k
 libXdamage                                    x86_64                        1.1.3-4.el6                                   base                            18 k
 libXext                                       x86_64                        1.3.3-1.el6                                   base                            35 k
 libXfixes                                     x86_64                        5.0.1-2.1.el6                                 base                            17 k
 libXft                                        x86_64                        2.3.2-1.el6                                   base                            55 k
 libXi                                         x86_64                        1.7.4-1.el6                                   base                            37 k
 libXinerama                                   x86_64                        1.1.3-2.1.el6                                 base                            13 k
 libXrandr                                     x86_64                        1.4.2-1.el6                                   base                            23 k
 libXrender                                    x86_64                        0.9.8-2.1.el6_8.1                             updates                         24 k
 libXxf86vm                                    x86_64                        1.1.3-2.1.el6                                 base                            16 k
 libjpeg-turbo                                 x86_64                        1.2.1-3.el6_5                                 base                           174 k
 libpng                                        x86_64                        2:1.2.49-2.el6_7                              base                           182 k
 libthai                                       x86_64                        0.1.12-3.el6                                  base                           183 k
 libtiff                                       x86_64                        3.9.4-10.el6_5                                base                           343 k
 libtool-ltdl                                  x86_64                        2.2.6-15.5.el6                                base                            44 k
 libxcb                                        x86_64                        1.11-2.el6                                    base                           142 k
 mesa-dri-drivers                              x86_64                        11.0.7-4.el6                                  base                           4.1 M
 mesa-dri-filesystem                           x86_64                        11.0.7-4.el6                                  base                            17 k
 mesa-dri1-drivers                             x86_64                        7.11-8.el6                                    base                           3.8 M
 mesa-libGL                                    x86_64                        11.0.7-4.el6                                  base                           142 k
 mesa-libGLU                                   x86_64                        11.0.7-4.el6                                  base                           198 k
 mesa-private-llvm                             x86_64                        3.6.2-1.el6                                   base                           6.5 M
 pango                                         x86_64                        1.28.1-11.el6                                 base                           351 k
 pixman                                        x86_64                        0.32.8-1.el6                                  base                           243 k
 tcl                                           x86_64                        1:8.5.7-6.el6                                 base                           1.9 M
 tk                                            x86_64                        1:8.5.7-5.el6                                 base                           1.4 M
 unixODBC                                      x86_64                        2.2.14-14.el6                                 base                           378 k
 wxBase                                        x86_64                        2.8.12-1.el6.centos                           extras                         572 k
 wxGTK                                         x86_64                        2.8.12-1.el6.centos                           extras                         2.9 M
 wxGTK-gl                                      x86_64                        2.8.12-1.el6.centos                           extras                          31 k
Updating for dependencies:
 glib2                                         x86_64                        2.28.8-5.el6                                  base                           1.7 M
 libdrm                                        x86_64                        2.4.65-2.el6                                  base                           136 k

Transaction Summary
================================================================================================================================================================
Install     106 Package(s)
Upgrade       2 Package(s)

Total download size: 67 M
Is this ok [y/N]: y
Downloading Packages:
(1/108): SDL-1.2.14-7.el6_7.1.x86_64.rpm                                                                                                 | 193 kB     00:00
(2/108): atk-1.30.0-1.el6.x86_64.rpm                                                                                                     | 195 kB     00:00
(3/108): avahi-libs-0.6.25-15.el6.x86_64.rpm                                                                                             |  55 kB     00:00
(4/108): cairo-1.8.8-6.el6_6.x86_64.rpm                                                                                                  | 309 kB     00:00
(5/108): cups-libs-1.4.2-74.el6.x86_64.rpm                                                                                               | 322 kB     00:00
(6/108): erlang-R14B-04.3.el6.x86_64.rpm                                                                                                 |  26 kB     00:00
(7/108): erlang-appmon-R14B-04.3.el6.x86_64.rpm                                                                                          | 145 kB     00:00
(8/108): erlang-asn1-R14B-04.3.el6.x86_64.rpm                                                                                            | 993 kB     00:00
(9/108): erlang-common_test-R14B-04.3.el6.x86_64.rpm                                                                                     | 508 kB     00:00
(10/108): erlang-compiler-R14B-04.3.el6.x86_64.rpm                                                                                       | 987 kB     00:00
(11/108): erlang-cosEvent-R14B-04.3.el6.x86_64.rpm                                                                                       | 149 kB     00:00
(12/108): erlang-cosEventDomain-R14B-04.3.el6.x86_64.rpm                                                                                 | 113 kB     00:00
(13/108): erlang-cosFileTransfer-R14B-04.3.el6.x86_64.rpm                                                                                | 168 kB     00:00
(14/108): erlang-cosNotification-R14B-04.3.el6.x86_64.rpm                                                                                | 718 kB     00:00
(15/108): erlang-cosProperty-R14B-04.3.el6.x86_64.rpm                                                                                    | 161 kB     00:00
(16/108): erlang-cosTime-R14B-04.3.el6.x86_64.rpm                                                                                        | 106 kB     00:00
(17/108): erlang-cosTransactions-R14B-04.3.el6.x86_64.rpm                                                                                | 164 kB     00:00
(18/108): erlang-crypto-R14B-04.3.el6.x86_64.rpm                                                                                         |  50 kB     00:00
(19/108): erlang-debugger-R14B-04.3.el6.x86_64.rpm                                                                                       | 440 kB     00:00
(20/108): erlang-dialyzer-R14B-04.3.el6.x86_64.rpm                                                                                       | 567 kB     00:00
(21/108): erlang-diameter-R14B-04.3.el6.x86_64.rpm                                                                                       | 449 kB     00:00
(22/108): erlang-docbuilder-R14B-04.3.el6.x86_64.rpm                                                                                     | 192 kB     00:00
(23/108): erlang-edoc-R14B-04.3.el6.x86_64.rpm                                                                                           | 301 kB     00:00
(24/108): erlang-erl_docgen-R14B-04.3.el6.x86_64.rpm                                                                                     | 109 kB     00:00
(25/108): erlang-erl_interface-R14B-04.3.el6.x86_64.rpm                                                                                  | 149 kB     00:00
(26/108): erlang-erts-R14B-04.3.el6.x86_64.rpm                                                                                           | 2.0 MB     00:00
(27/108): erlang-et-R14B-04.3.el6.x86_64.rpm                                                                                             | 197 kB     00:00
(28/108): erlang-eunit-R14B-04.3.el6.x86_64.rpm                                                                                          | 139 kB     00:00
(29/108): erlang-examples-R14B-04.3.el6.x86_64.rpm                                                                                       | 832 kB     00:00
(30/108): erlang-gs-R14B-04.3.el6.x86_64.rpm                                                                                             | 608 kB     00:00
(31/108): erlang-hipe-R14B-04.3.el6.x86_64.rpm                                                                                           | 1.0 MB     00:00
(32/108): erlang-ic-R14B-04.3.el6.x86_64.rpm                                                                                             | 845 kB     00:00
(33/108): erlang-inets-R14B-04.3.el6.x86_64.rpm                                                                                          | 749 kB     00:00
(34/108): erlang-inviso-R14B-04.3.el6.x86_64.rpm                                                                                         | 154 kB     00:00
(35/108): erlang-jinterface-R14B-04.3.el6.x86_64.rpm                                                                                     |  95 kB     00:00
(36/108): erlang-kernel-R14B-04.3.el6.x86_64.rpm                                                                                         | 1.0 MB     00:00
(37/108): erlang-megaco-R14B-04.3.el6.x86_64.rpm                                                                                         | 7.8 MB     00:01
(38/108): erlang-mnesia-R14B-04.3.el6.x86_64.rpm                                                                                         | 662 kB     00:00
(39/108): erlang-observer-R14B-04.3.el6.x86_64.rpm                                                                                       | 205 kB     00:00
(40/108): erlang-odbc-R14B-04.3.el6.x86_64.rpm                                                                                           |  59 kB     00:00
(41/108): erlang-orber-R14B-04.3.el6.x86_64.rpm                                                                                          | 909 kB     00:00
(42/108): erlang-os_mon-R14B-04.3.el6.x86_64.rpm                                                                                         | 104 kB     00:00
(43/108): erlang-otp_mibs-R14B-04.3.el6.x86_64.rpm                                                                                       |  28 kB     00:00
(44/108): erlang-parsetools-R14B-04.3.el6.x86_64.rpm                                                                                     | 164 kB     00:00
(45/108): erlang-percept-R14B-04.3.el6.x86_64.rpm                                                                                        | 140 kB     00:00
(46/108): erlang-pman-R14B-04.3.el6.x86_64.rpm                                                                                           | 105 kB     00:00
(47/108): erlang-public_key-R14B-04.3.el6.x86_64.rpm                                                                                     | 402 kB     00:00
(48/108): erlang-reltool-R14B-04.3.el6.x86_64.rpm                                                                                        | 296 kB     00:00
(49/108): erlang-runtime_tools-R14B-04.3.el6.x86_64.rpm                                                                                  | 210 kB     00:00
(50/108): erlang-sasl-R14B-04.3.el6.x86_64.rpm                                                                                           | 263 kB     00:00
(51/108): erlang-snmp-R14B-04.3.el6.x86_64.rpm                                                                                           | 1.5 MB     00:00
(52/108): erlang-ssh-R14B-04.3.el6.x86_64.rpm                                                                                            | 361 kB     00:00
(53/108): erlang-ssl-R14B-04.3.el6.x86_64.rpm                                                                                            | 378 kB     00:00
(54/108): erlang-stdlib-R14B-04.3.el6.x86_64.rpm                                                                                         | 2.1 MB     00:00
(55/108): erlang-syntax_tools-R14B-04.3.el6.x86_64.rpm                                                                                   | 317 kB     00:00
(56/108): erlang-test_server-R14B-04.3.el6.x86_64.rpm                                                                                    | 272 kB     00:00
(57/108): erlang-toolbar-R14B-04.3.el6.x86_64.rpm                                                                                        |  49 kB     00:00
(58/108): erlang-tools-R14B-04.3.el6.x86_64.rpm                                                                                          | 535 kB     00:00
(59/108): erlang-tv-R14B-04.3.el6.x86_64.rpm                                                                                             | 377 kB     00:00
(60/108): erlang-typer-R14B-04.3.el6.x86_64.rpm                                                                                          |  58 kB     00:00
(61/108): erlang-webtool-R14B-04.3.el6.x86_64.rpm                                                                                        |  45 kB     00:00
(62/108): erlang-wx-R14B-04.3.el6.x86_64.rpm                                                                                             | 2.4 MB     00:00
(63/108): erlang-xmerl-R14B-04.3.el6.x86_64.rpm                                                                                          | 939 kB     00:00
(64/108): fontconfig-2.8.0-5.el6.x86_64.rpm                                                                                              | 186 kB     00:00
(65/108): freetype-2.3.11-17.el6.x86_64.rpm                                                                                              | 361 kB     00:00
(66/108): gdk-pixbuf2-2.24.1-6.el6_7.x86_64.rpm                                                                                          | 501 kB     00:00
(67/108): glib2-2.28.8-5.el6.x86_64.rpm                                                                                                  | 1.7 MB     00:00
(68/108): gnutls-2.8.5-19.el6_7.x86_64.rpm                                                                                               | 347 kB     00:00
(69/108): gtk2-2.24.23-8.el6.x86_64.rpm                                                                                                  | 3.2 MB     00:00
(70/108): hicolor-icon-theme-0.11-1.1.el6.noarch.rpm                                                                                     |  40 kB     00:00
(71/108): jasper-libs-1.900.1-16.el6_6.3.x86_64.rpm                                                                                      | 137 kB     00:00
(72/108): libICE-1.0.6-1.el6.x86_64.rpm                                                                                                  |  53 kB     00:00
(73/108): libSM-1.2.1-2.el6.x86_64.rpm                                                                                                   |  37 kB     00:00
(74/108): libX11-1.6.3-2.el6.x86_64.rpm                                                                                                  | 586 kB     00:00
(75/108): libX11-common-1.6.3-2.el6.noarch.rpm                                                                                           | 169 kB     00:00
(76/108): libXau-1.0.6-4.el6.x86_64.rpm                                                                                                  |  24 kB     00:00
(77/108): libXcomposite-0.4.3-4.el6.x86_64.rpm                                                                                           |  20 kB     00:00
(78/108): libXcursor-1.1.14-2.1.el6.x86_64.rpm                                                                                           |  28 kB     00:00
(79/108): libXdamage-1.1.3-4.el6.x86_64.rpm                                                                                              |  18 kB     00:00
(80/108): libXext-1.3.3-1.el6.x86_64.rpm                                                                                                 |  35 kB     00:00
(81/108): libXfixes-5.0.1-2.1.el6.x86_64.rpm                                                                                             |  17 kB     00:00
(82/108): libXft-2.3.2-1.el6.x86_64.rpm                                                                                                  |  55 kB     00:00
(83/108): libXi-1.7.4-1.el6.x86_64.rpm                                                                                                   |  37 kB     00:00
(84/108): libXinerama-1.1.3-2.1.el6.x86_64.rpm                                                                                           |  13 kB     00:00
(85/108): libXrandr-1.4.2-1.el6.x86_64.rpm                                                                                               |  23 kB     00:00
(86/108): libXrender-0.9.8-2.1.el6_8.1.x86_64.rpm                                                                                        |  24 kB     00:00
(87/108): libXxf86vm-1.1.3-2.1.el6.x86_64.rpm                                                                                            |  16 kB     00:00
(88/108): libdrm-2.4.65-2.el6.x86_64.rpm                                                                                                 | 136 kB     00:00
(89/108): libjpeg-turbo-1.2.1-3.el6_5.x86_64.rpm                                                                                         | 174 kB     00:00
(90/108): libpng-1.2.49-2.el6_7.x86_64.rpm                                                                                               | 182 kB     00:00
(91/108): libthai-0.1.12-3.el6.x86_64.rpm                                                                                                | 183 kB     00:00
(92/108): libtiff-3.9.4-10.el6_5.x86_64.rpm                                                                                              | 343 kB     00:00
(93/108): libtool-ltdl-2.2.6-15.5.el6.x86_64.rpm                                                                                         |  44 kB     00:00
(94/108): libxcb-1.11-2.el6.x86_64.rpm                                                                                                   | 142 kB     00:00
(95/108): mesa-dri-drivers-11.0.7-4.el6.x86_64.rpm                                                                                       | 4.1 MB     00:00
(96/108): mesa-dri-filesystem-11.0.7-4.el6.x86_64.rpm                                                                                    |  17 kB     00:00
(97/108): mesa-dri1-drivers-7.11-8.el6.x86_64.rpm                                                                                        | 3.8 MB     00:00
(98/108): mesa-libGL-11.0.7-4.el6.x86_64.rpm                                                                                             | 142 kB     00:00
(99/108): mesa-libGLU-11.0.7-4.el6.x86_64.rpm                                                                                            | 198 kB     00:00
(100/108): mesa-private-llvm-3.6.2-1.el6.x86_64.rpm                                                                                      | 6.5 MB     00:00
(101/108): pango-1.28.1-11.el6.x86_64.rpm                                                                                                | 351 kB     00:00
(102/108): pixman-0.32.8-1.el6.x86_64.rpm                                                                                                | 243 kB     00:00
(103/108): tcl-8.5.7-6.el6.x86_64.rpm                                                                                                    | 1.9 MB     00:00
(104/108): tk-8.5.7-5.el6.x86_64.rpm                                                                                                     | 1.4 MB     00:00
(105/108): unixODBC-2.2.14-14.el6.x86_64.rpm                                                                                             | 378 kB     00:00
(106/108): wxBase-2.8.12-1.el6.centos.x86_64.rpm                                                                                         | 572 kB     00:00
(107/108): wxGTK-2.8.12-1.el6.centos.x86_64.rpm                                                                                          | 2.9 MB     00:00
(108/108): wxGTK-gl-2.8.12-1.el6.centos.x86_64.rpm                                                                                       |  31 kB     00:00
----------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                           4.2 MB/s |  67 MB     00:15
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : erlang-syntax_tools-R14B-04.3.el6.x86_64                                                                                                   1/110
  Installing : erlang-hipe-R14B-04.3.el6.x86_64                                                                                                           2/110
  Installing : erlang-compiler-R14B-04.3.el6.x86_64                                                                                                       3/110
  Installing : erlang-erts-R14B-04.3.el6.x86_64                                                                                                           4/110
  Installing : erlang-kernel-R14B-04.3.el6.x86_64                                                                                                         5/110
  Installing : erlang-stdlib-R14B-04.3.el6.x86_64                                                                                                         6/110
  Installing : erlang-crypto-R14B-04.3.el6.x86_64                                                                                                         7/110
  Installing : erlang-runtime_tools-R14B-04.3.el6.x86_64                                                                                                  8/110
  Installing : erlang-mnesia-R14B-04.3.el6.x86_64                                                                                                         9/110
  Installing : freetype-2.3.11-17.el6.x86_64                                                                                                             10/110
  Installing : fontconfig-2.8.0-5.el6.x86_64                                                                                                             11/110
  Installing : libjpeg-turbo-1.2.1-3.el6_5.x86_64                                                                                                        12/110
  Updating   : glib2-2.28.8-5.el6.x86_64                                                                                                                 13/110
  Installing : 2:libpng-1.2.49-2.el6_7.x86_64                                                                                                            14/110
  Installing : libtiff-3.9.4-10.el6_5.x86_64                                                                                                             15/110
  Installing : erlang-snmp-R14B-04.3.el6.x86_64                                                                                                          16/110
  Installing : erlang-xmerl-R14B-04.3.el6.x86_64                                                                                                         17/110
  Installing : atk-1.30.0-1.el6.x86_64                                                                                                                   18/110
  Installing : erlang-public_key-R14B-04.3.el6.x86_64                                                                                                    19/110
  Installing : erlang-ssl-R14B-04.3.el6.x86_64                                                                                                           20/110
  Installing : erlang-inets-R14B-04.3.el6.x86_64                                                                                                         21/110
  Installing : erlang-orber-R14B-04.3.el6.x86_64                                                                                                         22/110
  Installing : erlang-cosEvent-R14B-04.3.el6.x86_64                                                                                                      23/110
  Installing : wxBase-2.8.12-1.el6.centos.x86_64                                                                                                         24/110
  Updating   : libdrm-2.4.65-2.el6.x86_64                                                                                                                25/110
  Installing : erlang-cosTime-R14B-04.3.el6.x86_64                                                                                                       26/110
  Installing : erlang-cosNotification-R14B-04.3.el6.x86_64                                                                                               27/110
  Installing : erlang-cosProperty-R14B-04.3.el6.x86_64                                                                                                   28/110
  Installing : erlang-edoc-R14B-04.3.el6.x86_64                                                                                                          29/110
  Installing : erlang-ssh-R14B-04.3.el6.x86_64                                                                                                           30/110
  Installing : erlang-otp_mibs-R14B-04.3.el6.x86_64                                                                                                      31/110
  Installing : erlang-asn1-R14B-04.3.el6.x86_64                                                                                                          32/110
  Installing : mesa-dri-filesystem-11.0.7-4.el6.x86_64                                                                                                   33/110
  Installing : erlang-docbuilder-R14B-04.3.el6.x86_64                                                                                                    34/110
  Installing : erlang-cosFileTransfer-R14B-04.3.el6.x86_64                                                                                               35/110
  Installing : erlang-cosEventDomain-R14B-04.3.el6.x86_64                                                                                                36/110
  Installing : erlang-cosTransactions-R14B-04.3.el6.x86_64                                                                                               37/110
  Installing : erlang-percept-R14B-04.3.el6.x86_64                                                                                                       38/110
  Installing : jasper-libs-1.900.1-16.el6_6.3.x86_64                                                                                                     39/110
  Installing : erlang-inviso-R14B-04.3.el6.x86_64                                                                                                        40/110
  Installing : erlang-parsetools-R14B-04.3.el6.x86_64                                                                                                    41/110
  Installing : erlang-eunit-R14B-04.3.el6.x86_64                                                                                                         42/110
  Installing : erlang-diameter-R14B-04.3.el6.x86_64                                                                                                      43/110
  Installing : erlang-ic-R14B-04.3.el6.x86_64                                                                                                            44/110
  Installing : erlang-jinterface-R14B-04.3.el6.x86_64                                                                                                    45/110
  Installing : erlang-erl_interface-R14B-04.3.el6.x86_64                                                                                                 46/110
  Installing : erlang-erl_docgen-R14B-04.3.el6.x86_64                                                                                                    47/110
  Installing : SDL-1.2.14-7.el6_7.1.x86_64                                                                                                               48/110
  Installing : libICE-1.0.6-1.el6.x86_64                                                                                                                 49/110
  Installing : libSM-1.2.1-2.el6.x86_64                                                                                                                  50/110
  Installing : avahi-libs-0.6.25-15.el6.x86_64                                                                                                           51/110
  Installing : libthai-0.1.12-3.el6.x86_64                                                                                                               52/110
  Installing : 1:tcl-8.5.7-6.el6.x86_64                                                                                                                  53/110
  Installing : libXau-1.0.6-4.el6.x86_64                                                                                                                 54/110
  Installing : libxcb-1.11-2.el6.x86_64                                                                                                                  55/110
  Installing : libtool-ltdl-2.2.6-15.5.el6.x86_64                                                                                                        56/110
  Installing : unixODBC-2.2.14-14.el6.x86_64                                                                                                             57/110
  Installing : erlang-odbc-R14B-04.3.el6.x86_64                                                                                                          58/110
  Installing : gnutls-2.8.5-19.el6_7.x86_64                                                                                                              59/110
  Installing : 1:cups-libs-1.4.2-74.el6.x86_64                                                                                                           60/110
  Installing : pixman-0.32.8-1.el6.x86_64                                                                                                                61/110
  Installing : mesa-private-llvm-3.6.2-1.el6.x86_64                                                                                                      62/110
  Installing : libX11-common-1.6.3-2.el6.noarch                                                                                                          63/110
  Installing : libX11-1.6.3-2.el6.x86_64                                                                                                                 64/110
  Installing : libXrender-0.9.8-2.1.el6_8.1.x86_64                                                                                                       65/110
  Installing : libXext-1.3.3-1.el6.x86_64                                                                                                                66/110
  Installing : libXfixes-5.0.1-2.1.el6.x86_64                                                                                                            67/110
  Installing : libXxf86vm-1.1.3-2.1.el6.x86_64                                                                                                           68/110
  Installing : libXinerama-1.1.3-2.1.el6.x86_64                                                                                                          69/110
  Installing : gdk-pixbuf2-2.24.1-6.el6_7.x86_64                                                                                                         70/110
  Installing : libXdamage-1.1.3-4.el6.x86_64                                                                                                             71/110
  Installing : mesa-dri-drivers-11.0.7-4.el6.x86_64                                                                                                      72/110
  Installing : mesa-libGL-11.0.7-4.el6.x86_64                                                                                                            73/110
  Installing : mesa-dri1-drivers-7.11-8.el6.x86_64                                                                                                       74/110
  Installing : mesa-libGLU-11.0.7-4.el6.x86_64                                                                                                           75/110
  Installing : cairo-1.8.8-6.el6_6.x86_64                                                                                                                76/110
  Installing : libXft-2.3.2-1.el6.x86_64                                                                                                                 77/110
  Installing : pango-1.28.1-11.el6.x86_64                                                                                                                78/110
  Installing : 1:tk-8.5.7-5.el6.x86_64                                                                                                                   79/110
  Installing : erlang-gs-R14B-04.3.el6.x86_64                                                                                                            80/110
  Installing : erlang-pman-R14B-04.3.el6.x86_64                                                                                                          81/110
  Installing : erlang-tv-R14B-04.3.el6.x86_64                                                                                                            82/110
  Installing : erlang-toolbar-R14B-04.3.el6.x86_64                                                                                                       83/110
  Installing : erlang-appmon-R14B-04.3.el6.x86_64                                                                                                        84/110
  Installing : libXcursor-1.1.14-2.1.el6.x86_64                                                                                                          85/110
  Installing : libXi-1.7.4-1.el6.x86_64                                                                                                                  86/110
  Installing : libXrandr-1.4.2-1.el6.x86_64                                                                                                              87/110
  Installing : libXcomposite-0.4.3-4.el6.x86_64                                                                                                          88/110
  Installing : hicolor-icon-theme-0.11-1.1.el6.noarch                                                                                                    89/110
  Installing : gtk2-2.24.23-8.el6.x86_64                                                                                                                 90/110
  Installing : wxGTK-2.8.12-1.el6.centos.x86_64                                                                                                          91/110
  Installing : wxGTK-gl-2.8.12-1.el6.centos.x86_64                                                                                                       92/110
  Installing : erlang-wx-R14B-04.3.el6.x86_64                                                                                                            93/110
  Installing : erlang-debugger-R14B-04.3.el6.x86_64                                                                                                      94/110
  Installing : erlang-et-R14B-04.3.el6.x86_64                                                                                                            95/110
  Installing : erlang-observer-R14B-04.3.el6.x86_64                                                                                                      96/110
  Installing : erlang-webtool-R14B-04.3.el6.x86_64                                                                                                       97/110
  Installing : erlang-tools-R14B-04.3.el6.x86_64                                                                                                         98/110
  Installing : erlang-sasl-R14B-04.3.el6.x86_64                                                                                                          99/110
  Installing : erlang-test_server-R14B-04.3.el6.x86_64                                                                                                  100/110
  Installing : erlang-dialyzer-R14B-04.3.el6.x86_64                                                                                                     101/110
  Installing : erlang-typer-R14B-04.3.el6.x86_64                                                                                                        102/110
  Installing : erlang-common_test-R14B-04.3.el6.x86_64                                                                                                  103/110
  Installing : erlang-os_mon-R14B-04.3.el6.x86_64                                                                                                       104/110
  Installing : erlang-reltool-R14B-04.3.el6.x86_64                                                                                                      105/110
  Installing : erlang-megaco-R14B-04.3.el6.x86_64                                                                                                       106/110
  Installing : erlang-examples-R14B-04.3.el6.x86_64                                                                                                     107/110
  Installing : erlang-R14B-04.3.el6.x86_64                                                                                                              108/110
  Cleanup    : libdrm-2.4.45-2.el6.x86_64                                                                                                               109/110
  Cleanup    : glib2-2.26.1-3.el6.x86_64                                                                                                                110/110
  Verifying  : erlang-crypto-R14B-04.3.el6.x86_64                                                                                                         1/110
  Verifying  : libXdamage-1.1.3-4.el6.x86_64                                                                                                              2/110
  Verifying  : libXi-1.7.4-1.el6.x86_64                                                                                                                   3/110
  Verifying  : erlang-asn1-R14B-04.3.el6.x86_64                                                                                                           4/110
  Verifying  : mesa-dri-filesystem-11.0.7-4.el6.x86_64                                                                                                    5/110
  Verifying  : libSM-1.2.1-2.el6.x86_64                                                                                                                   6/110
  Verifying  : hicolor-icon-theme-0.11-1.1.el6.noarch                                                                                                     7/110
  Verifying  : erlang-wx-R14B-04.3.el6.x86_64                                                                                                             8/110
  Verifying  : erlang-orber-R14B-04.3.el6.x86_64                                                                                                          9/110
  Verifying  : erlang-runtime_tools-R14B-04.3.el6.x86_64                                                                                                 10/110
  Verifying  : erlang-pman-R14B-04.3.el6.x86_64                                                                                                          11/110
  Verifying  : erlang-tv-R14B-04.3.el6.x86_64                                                                                                            12/110
  Verifying  : gtk2-2.24.23-8.el6.x86_64                                                                                                                 13/110
  Verifying  : erlang-ssh-R14B-04.3.el6.x86_64                                                                                                           14/110
  Verifying  : erlang-cosTransactions-R14B-04.3.el6.x86_64                                                                                               15/110
  Verifying  : 1:cups-libs-1.4.2-74.el6.x86_64                                                                                                           16/110
  Verifying  : erlang-odbc-R14B-04.3.el6.x86_64                                                                                                          17/110
  Verifying  : glib2-2.28.8-5.el6.x86_64                                                                                                                 18/110
  Verifying  : erlang-R14B-04.3.el6.x86_64                                                                                                               19/110
  Verifying  : 1:tk-8.5.7-5.el6.x86_64                                                                                                                   20/110
  Verifying  : libX11-common-1.6.3-2.el6.noarch                                                                                                          21/110
  Verifying  : erlang-snmp-R14B-04.3.el6.x86_64                                                                                                          22/110
  Verifying  : erlang-parsetools-R14B-04.3.el6.x86_64                                                                                                    23/110
  Verifying  : erlang-xmerl-R14B-04.3.el6.x86_64                                                                                                         24/110
  Verifying  : freetype-2.3.11-17.el6.x86_64                                                                                                             25/110
  Verifying  : mesa-private-llvm-3.6.2-1.el6.x86_64                                                                                                      26/110
  Verifying  : pixman-0.32.8-1.el6.x86_64                                                                                                                27/110
  Verifying  : erlang-jinterface-R14B-04.3.el6.x86_64                                                                                                    28/110
  Verifying  : erlang-toolbar-R14B-04.3.el6.x86_64                                                                                                       29/110
  Verifying  : erlang-hipe-R14B-04.3.el6.x86_64                                                                                                          30/110
  Verifying  : mesa-libGLU-11.0.7-4.el6.x86_64                                                                                                           31/110
  Verifying  : erlang-inviso-R14B-04.3.el6.x86_64                                                                                                        32/110
  Verifying  : gnutls-2.8.5-19.el6_7.x86_64                                                                                                              33/110
  Verifying  : erlang-cosProperty-R14B-04.3.el6.x86_64                                                                                                   34/110
  Verifying  : erlang-dialyzer-R14B-04.3.el6.x86_64                                                                                                      35/110
  Verifying  : libXcomposite-0.4.3-4.el6.x86_64                                                                                                          36/110
  Verifying  : mesa-libGL-11.0.7-4.el6.x86_64                                                                                                            37/110
  Verifying  : erlang-megaco-R14B-04.3.el6.x86_64                                                                                                        38/110
  Verifying  : libXxf86vm-1.1.3-2.1.el6.x86_64                                                                                                           39/110
  Verifying  : erlang-syntax_tools-R14B-04.3.el6.x86_64                                                                                                  40/110
  Verifying  : erlang-cosFileTransfer-R14B-04.3.el6.x86_64                                                                                               41/110
  Verifying  : libtool-ltdl-2.2.6-15.5.el6.x86_64                                                                                                        42/110
  Verifying  : pango-1.28.1-11.el6.x86_64                                                                                                                43/110
  Verifying  : libXcursor-1.1.14-2.1.el6.x86_64                                                                                                          44/110
  Verifying  : libdrm-2.4.65-2.el6.x86_64                                                                                                                45/110
  Verifying  : erlang-erl_interface-R14B-04.3.el6.x86_64                                                                                                 46/110
  Verifying  : libXau-1.0.6-4.el6.x86_64                                                                                                                 47/110
  Verifying  : erlang-typer-R14B-04.3.el6.x86_64                                                                                                         48/110
  Verifying  : libX11-1.6.3-2.el6.x86_64                                                                                                                 49/110
  Verifying  : libXrandr-1.4.2-1.el6.x86_64                                                                                                              50/110
  Verifying  : erlang-cosEvent-R14B-04.3.el6.x86_64                                                                                                      51/110
  Verifying  : erlang-docbuilder-R14B-04.3.el6.x86_64                                                                                                    52/110
  Verifying  : erlang-compiler-R14B-04.3.el6.x86_64                                                                                                      53/110
  Verifying  : libtiff-3.9.4-10.el6_5.x86_64                                                                                                             54/110
  Verifying  : erlang-edoc-R14B-04.3.el6.x86_64                                                                                                          55/110
  Verifying  : erlang-sasl-R14B-04.3.el6.x86_64                                                                                                          56/110
  Verifying  : jasper-libs-1.900.1-16.el6_6.3.x86_64                                                                                                     57/110
  Verifying  : erlang-cosTime-R14B-04.3.el6.x86_64                                                                                                       58/110
  Verifying  : erlang-examples-R14B-04.3.el6.x86_64                                                                                                      59/110
  Verifying  : 1:tcl-8.5.7-6.el6.x86_64                                                                                                                  60/110
  Verifying  : libXfixes-5.0.1-2.1.el6.x86_64                                                                                                            61/110
  Verifying  : cairo-1.8.8-6.el6_6.x86_64                                                                                                                62/110
  Verifying  : erlang-eunit-R14B-04.3.el6.x86_64                                                                                                         63/110
  Verifying  : mesa-dri1-drivers-7.11-8.el6.x86_64                                                                                                       64/110
  Verifying  : erlang-common_test-R14B-04.3.el6.x86_64                                                                                                   65/110
  Verifying  : erlang-inets-R14B-04.3.el6.x86_64                                                                                                         66/110
  Verifying  : unixODBC-2.2.14-14.el6.x86_64                                                                                                             67/110
  Verifying  : erlang-diameter-R14B-04.3.el6.x86_64                                                                                                      68/110
  Verifying  : erlang-stdlib-R14B-04.3.el6.x86_64                                                                                                        69/110
  Verifying  : erlang-observer-R14B-04.3.el6.x86_64                                                                                                      70/110
  Verifying  : erlang-erts-R14B-04.3.el6.x86_64                                                                                                          71/110
  Verifying  : libXrender-0.9.8-2.1.el6_8.1.x86_64                                                                                                       72/110
  Verifying  : gdk-pixbuf2-2.24.1-6.el6_7.x86_64                                                                                                         73/110
  Verifying  : erlang-kernel-R14B-04.3.el6.x86_64                                                                                                        74/110
  Verifying  : erlang-public_key-R14B-04.3.el6.x86_64                                                                                                    75/110
  Verifying  : erlang-erl_docgen-R14B-04.3.el6.x86_64                                                                                                    76/110
  Verifying  : wxGTK-2.8.12-1.el6.centos.x86_64                                                                                                          77/110
  Verifying  : erlang-mnesia-R14B-04.3.el6.x86_64                                                                                                        78/110
  Verifying  : erlang-cosNotification-R14B-04.3.el6.x86_64                                                                                               79/110
  Verifying  : erlang-percept-R14B-04.3.el6.x86_64                                                                                                       80/110
  Verifying  : libxcb-1.11-2.el6.x86_64                                                                                                                  81/110
  Verifying  : atk-1.30.0-1.el6.x86_64                                                                                                                   82/110
  Verifying  : mesa-dri-drivers-11.0.7-4.el6.x86_64                                                                                                      83/110
  Verifying  : wxGTK-gl-2.8.12-1.el6.centos.x86_64                                                                                                       84/110
  Verifying  : erlang-os_mon-R14B-04.3.el6.x86_64                                                                                                        85/110
  Verifying  : erlang-webtool-R14B-04.3.el6.x86_64                                                                                                       86/110
  Verifying  : wxBase-2.8.12-1.el6.centos.x86_64                                                                                                         87/110
  Verifying  : fontconfig-2.8.0-5.el6.x86_64                                                                                                             88/110
  Verifying  : erlang-reltool-R14B-04.3.el6.x86_64                                                                                                       89/110
  Verifying  : libthai-0.1.12-3.el6.x86_64                                                                                                               90/110
  Verifying  : erlang-cosEventDomain-R14B-04.3.el6.x86_64                                                                                                91/110
  Verifying  : 2:libpng-1.2.49-2.el6_7.x86_64                                                                                                            92/110
  Verifying  : erlang-test_server-R14B-04.3.el6.x86_64                                                                                                   93/110
  Verifying  : erlang-debugger-R14B-04.3.el6.x86_64                                                                                                      94/110
  Verifying  : avahi-libs-0.6.25-15.el6.x86_64                                                                                                           95/110
  Verifying  : erlang-appmon-R14B-04.3.el6.x86_64                                                                                                        96/110
  Verifying  : libXinerama-1.1.3-2.1.el6.x86_64                                                                                                          97/110
  Verifying  : libXext-1.3.3-1.el6.x86_64                                                                                                                98/110
  Verifying  : erlang-otp_mibs-R14B-04.3.el6.x86_64                                                                                                      99/110
  Verifying  : libjpeg-turbo-1.2.1-3.el6_5.x86_64                                                                                                       100/110
  Verifying  : erlang-ic-R14B-04.3.el6.x86_64                                                                                                           101/110
  Verifying  : libXft-2.3.2-1.el6.x86_64                                                                                                                102/110
  Verifying  : erlang-tools-R14B-04.3.el6.x86_64                                                                                                        103/110
  Verifying  : libICE-1.0.6-1.el6.x86_64                                                                                                                104/110
  Verifying  : SDL-1.2.14-7.el6_7.1.x86_64                                                                                                              105/110
  Verifying  : erlang-et-R14B-04.3.el6.x86_64                                                                                                           106/110
  Verifying  : erlang-gs-R14B-04.3.el6.x86_64                                                                                                           107/110
  Verifying  : erlang-ssl-R14B-04.3.el6.x86_64                                                                                                          108/110
  Verifying  : libdrm-2.4.45-2.el6.x86_64                                                                                                               109/110
  Verifying  : glib2-2.26.1-3.el6.x86_64                                                                                                                110/110

Installed:
  erlang.x86_64 0:R14B-04.3.el6

Dependency Installed:
  SDL.x86_64 0:1.2.14-7.el6_7.1                        atk.x86_64 0:1.30.0-1.el6                           avahi-libs.x86_64 0:0.6.25-15.el6
  cairo.x86_64 0:1.8.8-6.el6_6                         cups-libs.x86_64 1:1.4.2-74.el6                     erlang-appmon.x86_64 0:R14B-04.3.el6
  erlang-asn1.x86_64 0:R14B-04.3.el6                   erlang-common_test.x86_64 0:R14B-04.3.el6           erlang-compiler.x86_64 0:R14B-04.3.el6
  erlang-cosEvent.x86_64 0:R14B-04.3.el6               erlang-cosEventDomain.x86_64 0:R14B-04.3.el6        erlang-cosFileTransfer.x86_64 0:R14B-04.3.el6
  erlang-cosNotification.x86_64 0:R14B-04.3.el6        erlang-cosProperty.x86_64 0:R14B-04.3.el6           erlang-cosTime.x86_64 0:R14B-04.3.el6
  erlang-cosTransactions.x86_64 0:R14B-04.3.el6        erlang-crypto.x86_64 0:R14B-04.3.el6                erlang-debugger.x86_64 0:R14B-04.3.el6
  erlang-dialyzer.x86_64 0:R14B-04.3.el6               erlang-diameter.x86_64 0:R14B-04.3.el6              erlang-docbuilder.x86_64 0:R14B-04.3.el6
  erlang-edoc.x86_64 0:R14B-04.3.el6                   erlang-erl_docgen.x86_64 0:R14B-04.3.el6            erlang-erl_interface.x86_64 0:R14B-04.3.el6
  erlang-erts.x86_64 0:R14B-04.3.el6                   erlang-et.x86_64 0:R14B-04.3.el6                    erlang-eunit.x86_64 0:R14B-04.3.el6
  erlang-examples.x86_64 0:R14B-04.3.el6               erlang-gs.x86_64 0:R14B-04.3.el6                    erlang-hipe.x86_64 0:R14B-04.3.el6
  erlang-ic.x86_64 0:R14B-04.3.el6                     erlang-inets.x86_64 0:R14B-04.3.el6                 erlang-inviso.x86_64 0:R14B-04.3.el6
  erlang-jinterface.x86_64 0:R14B-04.3.el6             erlang-kernel.x86_64 0:R14B-04.3.el6                erlang-megaco.x86_64 0:R14B-04.3.el6
  erlang-mnesia.x86_64 0:R14B-04.3.el6                 erlang-observer.x86_64 0:R14B-04.3.el6              erlang-odbc.x86_64 0:R14B-04.3.el6
  erlang-orber.x86_64 0:R14B-04.3.el6                  erlang-os_mon.x86_64 0:R14B-04.3.el6                erlang-otp_mibs.x86_64 0:R14B-04.3.el6
  erlang-parsetools.x86_64 0:R14B-04.3.el6             erlang-percept.x86_64 0:R14B-04.3.el6               erlang-pman.x86_64 0:R14B-04.3.el6
  erlang-public_key.x86_64 0:R14B-04.3.el6             erlang-reltool.x86_64 0:R14B-04.3.el6               erlang-runtime_tools.x86_64 0:R14B-04.3.el6
  erlang-sasl.x86_64 0:R14B-04.3.el6                   erlang-snmp.x86_64 0:R14B-04.3.el6                  erlang-ssh.x86_64 0:R14B-04.3.el6
  erlang-ssl.x86_64 0:R14B-04.3.el6                    erlang-stdlib.x86_64 0:R14B-04.3.el6                erlang-syntax_tools.x86_64 0:R14B-04.3.el6
  erlang-test_server.x86_64 0:R14B-04.3.el6            erlang-toolbar.x86_64 0:R14B-04.3.el6               erlang-tools.x86_64 0:R14B-04.3.el6
  erlang-tv.x86_64 0:R14B-04.3.el6                     erlang-typer.x86_64 0:R14B-04.3.el6                 erlang-webtool.x86_64 0:R14B-04.3.el6
  erlang-wx.x86_64 0:R14B-04.3.el6                     erlang-xmerl.x86_64 0:R14B-04.3.el6                 fontconfig.x86_64 0:2.8.0-5.el6
  freetype.x86_64 0:2.3.11-17.el6                      gdk-pixbuf2.x86_64 0:2.24.1-6.el6_7                 gnutls.x86_64 0:2.8.5-19.el6_7
  gtk2.x86_64 0:2.24.23-8.el6                          hicolor-icon-theme.noarch 0:0.11-1.1.el6            jasper-libs.x86_64 0:1.900.1-16.el6_6.3
  libICE.x86_64 0:1.0.6-1.el6                          libSM.x86_64 0:1.2.1-2.el6                          libX11.x86_64 0:1.6.3-2.el6
  libX11-common.noarch 0:1.6.3-2.el6                   libXau.x86_64 0:1.0.6-4.el6                         libXcomposite.x86_64 0:0.4.3-4.el6
  libXcursor.x86_64 0:1.1.14-2.1.el6                   libXdamage.x86_64 0:1.1.3-4.el6                     libXext.x86_64 0:1.3.3-1.el6
  libXfixes.x86_64 0:5.0.1-2.1.el6                     libXft.x86_64 0:2.3.2-1.el6                         libXi.x86_64 0:1.7.4-1.el6
  libXinerama.x86_64 0:1.1.3-2.1.el6                   libXrandr.x86_64 0:1.4.2-1.el6                      libXrender.x86_64 0:0.9.8-2.1.el6_8.1
  libXxf86vm.x86_64 0:1.1.3-2.1.el6                    libjpeg-turbo.x86_64 0:1.2.1-3.el6_5                libpng.x86_64 2:1.2.49-2.el6_7
  libthai.x86_64 0:0.1.12-3.el6                        libtiff.x86_64 0:3.9.4-10.el6_5                     libtool-ltdl.x86_64 0:2.2.6-15.5.el6
  libxcb.x86_64 0:1.11-2.el6                           mesa-dri-drivers.x86_64 0:11.0.7-4.el6              mesa-dri-filesystem.x86_64 0:11.0.7-4.el6
  mesa-dri1-drivers.x86_64 0:7.11-8.el6                mesa-libGL.x86_64 0:11.0.7-4.el6                    mesa-libGLU.x86_64 0:11.0.7-4.el6
  mesa-private-llvm.x86_64 0:3.6.2-1.el6               pango.x86_64 0:1.28.1-11.el6                        pixman.x86_64 0:0.32.8-1.el6
  tcl.x86_64 1:8.5.7-6.el6                             tk.x86_64 1:8.5.7-5.el6                             unixODBC.x86_64 0:2.2.14-14.el6
  wxBase.x86_64 0:2.8.12-1.el6.centos                  wxGTK.x86_64 0:2.8.12-1.el6.centos                  wxGTK-gl.x86_64 0:2.8.12-1.el6.centos

Dependency Updated:
  glib2.x86_64 0:2.28.8-5.el6                                                    libdrm.x86_64 0:2.4.65-2.el6

Complete!
[root@ansible ssl_certs]# rpm --import http://www.rabbitmq.com/rabbitmq-signing-key-public.asc
[root@ansible ssl_certs]# ll
合計 16
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 client
drwxr-xr-x 4  501 wheel 4096  6月 17 06:39 2016 sensu_ca
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 server
-rwxr-xr-x 1  501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# rpm -Uvh http://www.rabbitmq.com/releases/rabbitmq-server/v3.2.1/rabbitmq-server-3.2.1-1.noarch.rpm
http://www.rabbitmq.com/releases/rabbitmq-server/v3.2.1/rabbitmq-server-3.2.1-1.noarch.rpm を取得中
準備中...                ########################################### [100%]
   1:rabbitmq-server        ########################################### [100%]
[root@ansible ssl_certs]# service rabbitmq-server start
Starting rabbitmq-server: SUCCESS
rabbitmq-server.
[root@ansible ssl_certs]# mkdir -p /etc/rabbitmq/ssl
[root@ansible ssl_certs]# cd /etc/rabbitmq/
[root@ansible rabbitmq]# ll
合計 4
drwxr-xr-x 2 root root 4096  6月 17 06:42 2016 ssl
[root@ansible rabbitmq]# cd /tmp/
[root@ansible tmp]# ll
合計 76
-rwx------. 1 root    root       29  5月  4 16:27 2014 ks-script-nR80gm
-rwxr-xr-x. 1 root    root      143  5月  4 16:28 2014 ks-script-nR80gm.log
-rwxrwxrwx  1 root    root      110  5月  4 22:31 2014 script.sh
[
drwxr-xr-x  5     501 wheel    4096  6月 17 06:39 2016 ssl_certs
-rw-r--r--  1 root    root     7681  6月 17 00:43 2016 ssl_certs.tar
-rw-r--r--  1 root    root    46132  5月  4 16:30 2014 stderr
-rwx--x--x  1 vagrant vagrant   256  6月 17 06:35 2016 vagrant-shell
-rw-------. 1 root    root        0  5月  4 16:25 2014 yum.log
[root@ansible tmp]# cd ssl_certs
[root@ansible ssl_certs]# ll
合計 16
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 client
drwxr-xr-x 4  501 wheel 4096  6月 17 06:39 2016 sensu_ca
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 server
-rwxr-xr-x 1  501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# cp -a sensu_ca/cacert.pem /etc/rabbitmq/ssl/
[root@ansible ssl_certs]# cp -a server/cert.pem /etc/rabbitmq/ssl/
[root@ansible ssl_certs]# cp -a server/key.pem /etc/rabbitmq/ssl/
[root@ansible ssl_certs]# ll
合計 16
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 client
drwxr-xr-x 4  501 wheel 4096  6月 17 06:39 2016 sensu_ca
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 server
-rwxr-xr-x 1  501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# ll /etc/rabbitmq/ssl/
合計 12
-rw-r--r-- 1 root root 1021  6月 17 06:39 2016 cacert.pem
-rw-r--r-- 1 root root 1054  6月 17 06:39 2016 cert.pem
-rw-r--r-- 1 root root 1679  6月 17 06:39 2016 key.pem
[root@ansible ssl_certs]# vi /etc/rabbitmq/ssl/
cacert.pem  cert.pem    key.pem
[root@ansible ssl_certs]# vi /etc/rabbitmq/ssl/
cacert.pem  cert.pem    key.pem
[root@ansible ssl_certs]# cd /etc/rabbitmq/ssl/
[root@ansible ssl]# ll
合計 12
-rw-r--r-- 1 root root 1021  6月 17 06:39 2016 cacert.pem
-rw-r--r-- 1 root root 1054  6月 17 06:39 2016 cert.pem
-rw-r--r-- 1 root root 1679  6月 17 06:39 2016 key.pem
[root@ansible ssl]# ll
合計 12
-rw-r--r-- 1 root root 1021  6月 17 06:39 2016 cacert.pem
-rw-r--r-- 1 root root 1054  6月 17 06:39 2016 cert.pem
-rw-r--r-- 1 root root 1679  6月 17 06:39 2016 key.pem
[root@ansible ssl]# cd /tmp/ssl_certs
[root@ansible ssl_certs]# ll
合計 16
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 client
drwxr-xr-x 4  501 wheel 4096  6月 17 06:39 2016 sensu_ca
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 server
-rwxr-xr-x 1  501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# vi /etc/rabbitmq/rabbitmq.config
[root@ansible ssl_certs]# service rabbitmq-server restart
Restarting rabbitmq-server: SUCCESS
rabbitmq-server.
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# rabbitmqctl add_vhost /sensu
Creating vhost "/sensu" ...
...done.
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# rabbitmqctl add_user sensu sensu
Creating user "sensu" ...
...done.
[root@ansible ssl_certs]# rabbitmqctl set_permissions -p /sensu sensu ".*" ".*" ".*"
Setting permissions for user "sensu" in vhost "/sensu" ...
...done.
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# ll
合計 16
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 client
drwxr-xr-x 4  501 wheel 4096  6月 17 06:39 2016 sensu_ca
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 server
-rwxr-xr-x 1  501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# ll /etc/rabbitmq/
合計 8
-rw-r--r-- 1 root root  326  6月 17 06:44 2016 rabbitmq.config
drwxr-xr-x 2 root root 4096  6月 17 06:43 2016 ssl
[root@ansible ssl_certs]# rabbitmq-plugins enable rabbitmq_management
The following plugins have been enabled:
  mochiweb
  webmachine
  rabbitmq_web_dispatch
  amqp_client
  rabbitmq_management_agent
  rabbitmq_management
Plugin configuration has changed. Restart RabbitMQ for changes to take effect.
[root@ansible ssl_certs]# service rabbitmq-server restart
Restarting rabbitmq-server: SUCCESS
rabbitmq-server.
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# rabbitmqctl add_user admin admin
Creating user "admin" ...
...done.
[root@ansible ssl_certs]# rabbitmqctl set_user_tags admin administrator
Setting tags for user "admin" to [administrator] ...
...done.
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# iptables status
Bad argument `status'
Try `iptables -h' or 'iptables --help' for more information.
[root@ansible ssl_certs]# /etc/init.d/iptables status
テーブル: filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
2    ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0
3    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:22
5    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination
1    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination

[root@ansible ssl_certs]# /etc/init.d/iptables stop
iptables: チェインをポリシー ACCEPT へ設定中filter         [  OK  ]
iptables: ファイアウォールルールを消去中:                  [  OK  ]
iptables: モジュールを取り外し中:                          [  OK  ]
[root@ansible ssl_certs]# yum install redis
[sensu]
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: ftp.riken.jp
 * epel: ftp.riken.jp
 * extras: ftp.riken.jp
 * updates: ftp.jaist.ac.jp
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package redis.x86_64 0:2.4.10-1.el6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================================================================================================
 Package                             Arch                                 Version                                      Repository                          Size
================================================================================================================================================================
Installing:
 redis                               x86_64                               2.4.10-1.el6                                 epel                               213 k

Transaction Summary
================================================================================================================================================================
Install       1 Package(s)

Total download size: 213 k
Installed size: 668 k
Is this ok [y/N]: y
Downloading Packages:
redis-2.4.10-1.el6.x86_64.rpm                                                                                                            | 213 kB     00:00
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
Warning: RPMDB altered outside of yum.
  Installing : redis-2.4.10-1.el6.x86_64                                                                                                                    1/1
  Verifying  : redis-2.4.10-1.el6.x86_64                                                                                                                    1/1

Installed:
  redis.x86_64 0:2.4.10-1.el6

Complete!
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# service redis start
Starting redis-server:                                     [  OK  ]
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# vi /etc/yum.repos.d/sensu.repo
[root@ansible ssl_certs]# yum install sensu
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: ftp.riken.jp
 * epel: mirror.rise.ph
 * extras: ftp.riken.jp
 * updates: ftp.jaist.ac.jp
sensu                                                                                                                                    |  951 B     00:00
sensu/primary                                                                                                                            |  33 kB     00:00
sensu                                                                                                                                                     75/75
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package sensu.x86_64 1:0.20.3-1 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================================================================================================
 Package                             Arch                                 Version                                     Repository                           Size
================================================================================================================================================================
Installing:
 sensu                               x86_64                               1:0.20.3-1                                  sensu                                21 M

Transaction Summary
================================================================================================================================================================
Install       1 Package(s)

Total download size: 21 M
{
Installed size: 60 M
Is this ok [y/N]: y
Downloading Packages:
{
sensu-0.20.3-1.x86_64.rpm                                                                                                                |  21 MB     00:02
{
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : 1:sensu-0.20.3-1.x86_64                                                                                                                      1/1
  Verifying  : 1:sensu-0.20.3-1.x86_64                                                                                                                      1/1

Installed:
  sensu.x86_64 1:0.20.3-1

Complete!
{
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# mkdir -p /etc/sensu/ssl
[root@ansible ssl_certs]# cd /tmp/
[root@ansible tmp]# ll
合計 76
-rwx------. 1 root    root       29  5月  4 16:27 2014 ks-script-nR80gm
-rwxr-xr-x. 1 root    root      143  5月  4 16:28 2014 ks-script-nR80gm.log
-rwxrwxrwx  1 root    root      110  5月  4 22:31 2014 script.sh
drwxr-xr-x  5     501 wheel    4096  6月 17 06:39 2016 ssl_certs
-rw-r--r--  1 root    root     7681  6月 17 00:43 2016 ssl_certs.tar
-rw-r--r--  1 root    root    46132  5月  4 16:30 2014 stderr
-rwx--x--x  1 vagrant vagrant   256  6月 17 06:35 2016 vagrant-shell
-rw-------. 1 root    root        0  5月  4 16:25 2014 yum.log
[root@ansible tmp]# cd ssl_certs
[root@ansible ssl_certs]# ll
合計 16
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 client
drwxr-xr-x 4  501 wheel 4096  6月 17 06:39 2016 sensu_ca
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 server
-rwxr-xr-x 1  501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# cp -a client/cert.pem /etc/sensu/ssl/
[root@ansible ssl_certs]# cp -a client/key
key.pem      keycert.p12
[root@ansible ssl_certs]# cp -a client/key.pem /etc/sensu/ssl/
[root@ansible ssl_certs]# ll
合計 16
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 client
drwxr-xr-x 4  501 wheel 4096  6月 17 06:39 2016 sensu_ca
drwxr-xr-x 2 root root  4096  6月 17 06:39 2016 server
-rwxr-xr-x 1  501 wheel 1668 12月  4 21:01 2013 ssl_certs.sh
[root@ansible ssl_certs]# vi /etc/sensu/conf
conf.d/              config.json.example
[root@ansible ssl_certs]# vi /etc/sensu/conf.d/rabbitmq.json
[root@ansible ssl_certs]# vi /etc/sensu/conf.d/
README.md      rabbitmq.json
[root@ansible ssl_certs]# vi /etc/sensu/conf.d/redis.json
[root@ansible ssl_certs]# vi /etc/sensu/conf.d/api.json
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# echo $hostname

[root@ansible ssl_certs]# hostname
ansible
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# vi /etc/hosts
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# vi /etc/sensu/conf.d/client.json
[root@ansible ssl_certs]# service sensu-server start
Starting sensu-server                                      [  OK  ]
[root@ansible ssl_certs]# service sensu-client start
Starting sensu-client                                      [  OK  ]
[root@ansible ssl_certs]#
[root@ansible ssl_certs]#
[root@ansible ssl_certs]# service sensu-api start
Starting sensu-api                                         [  OK  ]
[root@ansible ssl_certs]#
```
