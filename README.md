# Usage

```shellscript
$ clussh 
  Usage: [SERVER=X] [LOADBALANCE=1] clussh <cmd>

$ grep cluster clussh
cluster="localhost serverA serverB serverC"

$ clussh date
localhost       | Sat Apr 29 14:13:06 UTC 2023
serverA         | Sat Apr 29 14:13:06 UTC 2023
serverB         | Sat Apr 29 18:01:22 CEST 2023
serverC         | Sat Apr 29 14:13:06 UTC 2023

$ grep hello clussh
  hello(){ echo hello from $(hostname) $*; }

$ clussh hello world
localhost     | hello from ubuntu world
serverA       | hello from archlinux world
serverB       | hello from debian world
serverC       | hello from gentoo world

$ SERVER=serverC clussh hello world
serverC       | hello from gentoo world

$ LOADBALANCE=1 clussh hello world
serverB       | hello from debian world
$ LOADBALANCE=1 clussh hello world
serverA       | hello from debian world
```

>Great for managing servers, or as a startingpoint for clustered rpc-tool:

* define [servers in the script](https://github.com/coderofsalvation/clussh/blob/main/clussh#L11)
* [add shellfunctions](https://github.com/coderofsalvation/clussh/blob/main/clussh#L14)
* profit!
