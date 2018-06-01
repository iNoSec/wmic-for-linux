# wmic-for-linux
a script to install wmic on linux and you can passthehash with it ;)

ugly code but i make it quick and work well with parrotOS 4.16.0
There is somme error on the screen but all work well



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
