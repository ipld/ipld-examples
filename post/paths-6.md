# IPLD Pathing: (6) .object and .link accessors

These examples are IPLD pathing of the unixfs datastructure, in the "(6) .object and .link accessors" style. Here, we suppose the `.object` prefix is the default one.

```
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.link
---
link: /ipfs/Qm-unixfs-dir1
mode: 0777
size: 220

> ipld cat /ipfs/Qm-unixfs-dir0/foo1.link/link
"/ipfs/Qm-unixfs-dir1"
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/ # or
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.object/
---
bar1:
  link: /ipfs/Qm-unixfs-dir3
  mode: 0777
  size: 120
bar2:
  link: /ipfs/Qm-unixfs-dir2 # note, same as foo2 above
  mode: 0777
  size: 140
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.object/bar1.link/mode
0777
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.object/bar1.link/size
120
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz2/ #or
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.object/bar2.object/baz2.object/
---
body: "hello\n"

> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz2/body #or
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.object/bar2.object/baz2.object/body
hello

>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz1/ #or
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.object/bar2.object/baz1.object/
---
files:
  - link: Qm-unixfs-file1
    size: 10
  - link: Qm-unixfs-file2
    size: 10
  - link: Qm-unixfs-file1
    size: 10
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz1/body # or
> ipld cat /ipfs/Qm-unixfs-dir0/foo1.object/bar2.object/baz1.object/body
> # no body
```
