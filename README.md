# clussh

Great for managing servers, or as a startingpoint for clustered tool:

* define servers in the script (edit `cluster=`)
* add shellfunctions like `hello` in the src

# Usage

```shellscript
$ clussh 
  Usage: [SERVER=X] [LOADBALANCE=1] clussh <cmd>

$ grep cluster clussh
cluster="serverA serverB serverC"

$ clussh date
serverA         | Sat Apr 29 14:13:06 UTC 2023
serverB         | Sat Apr 29 18:01:22 CEST 2023
serverC         | Sat Apr 29 14:13:06 UTC 2023

$ grep hello clussh
  hello(){ echo hello from $(hostname) $*; }

$ clussh hello
serverA       | hello from archlinux
serverB       | hello from debian
serverC       | hello from gentoo
```
