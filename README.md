# netsocks

Simple network socket status checker.</br>
It is checking list of TCP/IP sockets loaded from file `netsocks.yml`.</br>
It has to locate in same directory where you are keeping the script.</br>
**Requirements: Python=3.7.1, oyaml=0.9, docopt=0.6.2.**

```sh
$ ./netsocks -h
Usage:
        netsocks [-g group][-L group][-al][-h,--help]

   Options:
       -a            to check sockets for all host groups
       -g <group>    to check sockets for selected group of hosts
       -l            print list of all existing groups
       -L <group>    print list of hosts in specific group name
       -h --help     this help message


$ ./netsocks -l 
google
dnses
home
>>>>>>> devel

$ ./netsocks -L dnses
1.1.1.1
1.0.0.1
8.8.8.8
8.8.4.4

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
```

Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/> </br>
GPL Version 3,  29 June 2007