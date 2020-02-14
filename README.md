# netsocks

Simple network socket analyzer.
It is checking list of network sockets from file called `config.yml`.
Requirements: Python3, PyYaml

```sh
$ ./netsocks | sort
dl-router.hm          443 open
lightbox.hm           111 open
lightbox.hm          2049 open
lightbox.hm            21 open
lightbox.hm            22 open
lightbox.hm          4321 open
lightbox.hm            53 open
lightbox.hm           631 open
lightbox.hm          8080 open
lightbox.hm          8081 open
lightbox.hm          8083 open
lightbox.hm            80 open
...
```
## To do

Need to do sorted screen output.

_________________________________________________________________________________________________
Copyright (C) 2007 Free Software Foundation, Inc. <http://fsf.org/> GPL Version 3,  29 June 2007
