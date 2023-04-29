# clussh

Great for managing servers, or as a startingpoint for clustered rpc-tool:

* define [servers in the script](https://github.com/coderofsalvation/clussh/blob/main/clussh#L11)
* [add shellfunctions](https://github.com/coderofsalvation/clussh/blob/main/clussh#L14)
* profit!

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

$ SERVER=serverC clussh hello
serverC       | hello from gentoo
$ LOADBALANCE=1 clussh 
serverB       | hello from debian
$ LOADBALANCE=1 clussh 
serverA       | hello from debian
```
