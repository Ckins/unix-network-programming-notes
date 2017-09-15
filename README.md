NOTES
-----
Book : "Unix Network Programming -- The Socket Network API"
System : Ubuntu 14.04

Issues when compiling source files
-----
* inet_ntop.c compiling error
<!--lang:bash-->
	inet_ntop.c: In function ‘inet_ntop’:
	inet_ntop.c:60:9: error: argument ‘size’ doesn’t match prototype size_t size;

Solution:
`inet_ntop.c` line 61 : `size_t size` -> `socklen_t size`

* lib compiling error
```shell
In file included from get_rtaddrs.c:1:0:
unproute.h:3:45: fatal error: net/if_dl.h: No such file or directory
 #include <net/if_dl.h>  /* sockaddr_sdl{} */
```

Solution:
Do not need to compiler these modules. They are not prepared for Ubuntu.

* intro example has no response
```shell
./daytimetcpcli 127.0.0.1
connect error: Connection refused
``` 
Solution:
Start the server first.
`make daytimetcpsrv` and `sudo ./daytimetcpsrv`
