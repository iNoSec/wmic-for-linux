# wmic-for-linux
a script to install wmic on linux and you can passthehash with it ;)

ugly code but i make it quick and work well with parrotOS 4.16.0
There is somme error on the screen but all work well


WMIC command on Ubuntu 16.04 LTS

I have written several months ago a post on how to install the wmic command on a linux system. Some additional steps are required now to get the wmic command on an Ubuntu 16.04 LTS server.

Description
Windows Management Instrumentation Command-line (WMIC) uses Windows Management Instrumentation (WMI) to enable system management from the command line.

Installation
Pre-requisites

$ sudo aptitude install autoconf
$ mkdir -p /data/tools
$ cd /data/tools/
$ wget http://www.openvas.org/download/wmi/wmi-1.3.14.tar.bz2
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch2
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch3v2
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch4
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch5
$ bzip2 -cd wmi-1.3.14.tar.bz2 | tar xf -
$ cd wmi-1.3.14/
1
2
3
4
5
6
7
8
9
10
11
$ sudo aptitude install autoconf
$ mkdir -p /data/tools
$ cd /data/tools/
$ wget http://www.openvas.org/download/wmi/wmi-1.3.14.tar.bz2
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch2
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch3v2
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch4
$ wget http://www.openvas.org/download/wmi/openvas-wmi-1.3.14.patch5
$ bzip2 -cd wmi-1.3.14.tar.bz2 | tar xf -
$ cd wmi-1.3.14/
Patch

$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch2
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch3v2
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch4
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch5
1
2
3
4
5
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch2
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch3v2
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch4
$ patch -p1 < /data/tools/openvas-wmi-1.3.14.patch5
The current sources are outdated and use some deprecated instructions. Before running the compilation, please follow these steps:

Edit the file GNUmakefile and add the following line at the top after the license info:
ZENHOME=$(HOME)
Edit the file /data/tools/wmi-1.3.14/Samba/source/pidl/pidl : remove the line number 583
defined @$pidl || die "Failed to parse $idl_file";
Edit the file /data/tools/wmi-1.3.14/Samba/source/lib/tls/tls.c
Line 508: replace gnutls_transport_set_lowat(tls->session, 0); by gnutls_record_check_pending(tls->session);
Line 579: remove the line gnutls_certificate_type_set_priority(tls->session, cert_type_priority);
Line 587: replace gnutls_transport_set_lowat(tls->session, 0); by gnutls_record_check_pending(tls->session);
Compilation

$ sudo make "CPP=gcc -E -ffreestanding"
$ sudo cp Samba/source/bin/wmic /usr/local/bin/
1
2
$ sudo make "CPP=gcc -E -ffreestanding"
$ sudo cp Samba/source/bin/wmic /usr/local/bin/
Usage

Usage: wmic -U user%password //host "query"
Options
-?, --help
Show this help message
-A, --authentication-file=FILE
Get the credentials from a file
--delimiter=STRING
delimiter to use when querying multiple values, default to '|'
-d, --debuglevel=DEBUGLEVEL
Set debug level
--debug-stderr
Send debug output to STDERR
-i, --scope=SCOPE
Use this Netbios scope
-k, --kerberos=STRING
Use Kerberos
-l, --log-basename=LOGFILEBASE
Basename for log/debug files
--leak-report
enable full talloc leak reporting on exit
--leak-report-full
enable talloc leak reporting on exit
-m, --maxprotocol=MAXPROTOCOL
Set max protocol level
--namespace=STRING
WMI namespace, default to root\cimv2
-N, --no-pass
Don't ask for a password
-n, --netbiosname=NETBIOSNAME
Primary netbios name
--option=name=value
Set smb.conf option from command line
-O, --socket-options=SOCKETOPTIONS
socket options to use
--password=STRING
Password
-P, --machine-pass
Use stored machine account password (implies -k)
--realm=REALM
Set the realm name
-R, --name-resolve=NAME-RESOLVE-ORDER
Use these name resolution services only
--simple-bind-dn=STRING
DN to use for a simple bind
-S, --signing=on|off|required
Set the client signing state
-s, --configfile=CONFIGFILE
Use alternative configuration file
--usage
Display brief usage message
--use-security-mechanisms=STRING
Restricted list of authentication mechanisms available for use with this authentication
-U, --user=[DOMAIN\]USERNAME[%PASSWORD]
Set the network username
-V, --version
Print version
-W, --workgroup=WORKGROUP
Set the workgroup name
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
Usage: wmic -U user%password //host "query"
Options
-?, --help
Show this help message
-A, --authentication-file=FILE
Get the credentials from a file
--delimiter=STRING
delimiter to use when querying multiple values, default to '|'
-d, --debuglevel=DEBUGLEVEL
Set debug level
--debug-stderr
Send debug output to STDERR
-i, --scope=SCOPE
Use this Netbios scope
-k, --kerberos=STRING
Use Kerberos
-l, --log-basename=LOGFILEBASE
Basename for log/debug files
--leak-report
enable full talloc leak reporting on exit
--leak-report-full
enable talloc leak reporting on exit
-m, --maxprotocol=MAXPROTOCOL
Set max protocol level
--namespace=STRING
WMI namespace, default to root\cimv2
-N, --no-pass
Don't ask for a password
-n, --netbiosname=NETBIOSNAME
Primary netbios name
--option=name=value
Set smb.conf option from command line
-O, --socket-options=SOCKETOPTIONS
socket options to use
--password=STRING
Password
-P, --machine-pass
Use stored machine account password (implies -k)
--realm=REALM
Set the realm name
-R, --name-resolve=NAME-RESOLVE-ORDER
Use these name resolution services only
--simple-bind-dn=STRING
DN to use for a simple bind
-S, --signing=on|off|required
Set the client signing state
-s, --configfile=CONFIGFILE
Use alternative configuration file
--usage
Display brief usage message
--use-security-mechanisms=STRING
Restricted list of authentication mechanisms available for use with this authentication
-U, --user=[DOMAIN\]USERNAME[%PASSWORD]
Set the network username
-V, --version
Print version
-W, --workgroup=WORKGROUP
Set the workgroup name
