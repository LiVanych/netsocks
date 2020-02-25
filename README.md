# netsocks

Simple network socket status checker.</br>
It is checking list of TCP/IP sockets loaded from file `netsocks.yml`.</br>
It has to locate in same directory where you are keeping the script.</br>
**Requirements: Python=3.7.1, oyaml=0.9, docopt=0.6.2.**

```sh
Usage:      
 netsocks [HOST PORT]
 netsocks [-g name]    
 netsocks [-a][-l][-h]        
 netsocks [-L name]
 netsocks [-H host][-H ip]
 netsocks [-c file [-a][-l]]
 netsocks [-c file [-L group]]
 netsocks [-c file [-H host]]
 
Arguments:                                                               
 HOST       hostname or IP
 PORT       TCP port
 
Options:
 -a         all sockets scan                                             
 -g <name>  one group checking                                           
 -H <host>  one host socks check                                         
 -l         groups list printing                                         
 -L <name>  one group hosts list                                         
 -c <file>  custom config file
 -h         this help message


$ ./netsocks 172.16.16.8 8080
172.16.16.8          8080 open

# getting list of the groups
$ ./netsocks -l 
google
dnses
home

# print list all hosts belong "dnses" group
$ ./netsocks -L dnses
1.1.1.1
1.0.0.1
8.8.8.8
8.8.4.4

# scan sockets for one host from the "dnses" group
$ ./netsocks -H 1.1.1.1
1.1.1.1                53 open

# scan all hosts of the "dnses" group
$ ./netsocks -g dnses
 |██████████████████████| 100.0% 
Checked at 24/02/2020 10:58:05
------------------------------
1.1.1.1                53 open
------------------------------
1.0.0.1                53 open
------------------------------
8.8.8.8                53 open
------------------------------
8.8.4.4                53 open
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

# the same command may be executed for custom configuration file
$ ./netsocks -c /tmp/custom_netsocks.yml -l
corp_net
home_land
public
```


Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/> </br>
GPL Version 3,  29 June 2007