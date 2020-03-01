# netsocks

Simple network socket status checker.</br>
It is checking list of TCP/IP sockets loaded from file `~/.config/netsocks.yml`.</br>
Config file will be created at first boot time.</br>
**Default config example:**

```sh
$ cat ~/.config/netsocks.yml 
google:
  google.com:
  - 80
  - 443
    gmail.com:
  - 80
  - 443
```
**Requirements: Python>=3.7.1, oyaml>=0.9, docopt>=0.6.2.**

```sh
Usage:
 netsocks [HOST PORT]
 netsocks [-g group,group]
 netsocks [-a][-l][-h]
 netsocks [-X group,group]
 netsocks [-x host,host]
 netsocks [-L group]
 netsocks [-H host,host]
 netsocks [-c file [-a][-l]]
 netsocks [-c file [-x host]]
 netsocks [-c file [-X group]]
 netsocks [-c file [-g group]]
 netsocks [-c file [-L group]]
 netsocks [-c file [-H host]]

Arguments:
 HOST       hostname or IP
 PORT       TCP port

Options:
 -a         all sockets scan
 -X <grp>   all group except sth
 -x <host>  all except something
 -g <grp>   one group checking
 -H <host>  one host socks check
 -l         groups list printing
 -L <grp>   one group hosts list
 -c <file>  custom config file
 -h,--help  this help message


$ ./netsocks 172.16.16.8 21,22,25,80,8080
172.16.16.8          8080 open
172.16.16.8            22 open
172.16.16.8            25 closed
172.16.16.8            80 open
172.16.16.8          8080 open

# getting list of the all groups
$ ./netsocks -l 
google
dnses
home

# print list all hosts of "dnses" group
$ ./netsocks -L dnses
1.1.1.1
1.0.0.1
8.8.8.8
8.8.4.4

# scan sockets for any number of specific hosts
# note: host has to placed in your config file
$ ./netsocks -H 1.1.1.1,1.0.0.1
1.1.1.1                53 open
1.0.0.1                53 open

# may be checked one or more groups
$ ./netsocks -g dnses,google
 |██████████████████████| 100.0% 
Checked at 26/02/2020 15:53:00
------------------------------
1.1.1.1                53 open
------------------------------
1.0.0.1                53 open
------------------------------
8.8.8.8                53 open
------------------------------
8.8.4.4                53 open
------------------------------
google.com             80 open
google.com            443 open
------------------------------
gmail.com              80 open
gmail.com             443 open
------------------------------

# checking sockets of all hosts and all groups
$ ./netsocks -a
 |██████████████████████| 100.0% 
Checked at 24/02/2020 10:58:44
------------------------------
google.com             80 open
google.com            443 open
------------------------------
gmail.com              80 open
gmail.com             443 open
------------------------------
1.1.1.1                53 open
------------------------------
1.0.0.1                53 open
------------------------------
8.8.8.8                53 open
------------------------------
8.8.4.4                53 open
------------------------------
172.16.16.6            22 open
172.16.16.6            25 closed
172.16.16.6            80 open
172.16.16.6           111 open
------------------------------
172.16.16.8            21 open
172.16.16.8            22 open
172.16.16.8            80 open
172.16.16.8          8080 open
------------------------------

# some groups may be excluded
$ ./netsocks -X dnses,google
 |██████████████████████| 100.0% 
Checked at 26/02/2020 15:56:22
------------------------------
172.16.16.6            22 open
172.16.16.6            25 closed
172.16.16.6            80 open
172.16.16.6           111 open
------------------------------
172.16.16.8            21 open
172.16.16.8            22 open
172.16.16.8            80 open
172.16.16.8          8080 open
------------------------------

# hosts may be excluded too
$ ./netsocks -x google.com,gmail.com
 |██████████████████████| 100.0% 
Checked at 26/02/2020 15:58:08
------------------------------
1.1.1.1                53 open
------------------------------
1.0.0.1                53 open
------------------------------
8.8.8.8                53 open
------------------------------
8.8.4.4                53 open
------------------------------
172.16.16.6            22 open
172.16.16.6            25 closed
172.16.16.6            80 open
172.16.16.6           111 open
------------------------------
172.16.16.8            21 open
172.16.16.8            22 open
172.16.16.8            80 open
172.16.16.8          8080 open
------------------------------

# the same commands may be executed for custom configuration file
$ ./netsocks -c /tmp/custom_netsocks.yml -l
corp_net
home_land
public
```

Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/> </br>
GPL Version 3,  29 June 2007
