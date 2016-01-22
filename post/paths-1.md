# IPLD Pathing: (1) transparent, no link properties access

These examples are IPLD pathing of the unixfs datastructure, in the "(1) transparent, no link properties access" style.

```
> ipld cat /ipfs/Qm-unixfs-dir0/foo1
---
bar1:
  link: /ipfs/Qm-unixfs-dir3
  mode: 0777
  size: 120
bar2:
  link: /ipfs/Qm-unixfs-dir2 # note, same as foo2 above
  mode: 0777
  size: 140

> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link
cat: /ipfs/Qm-unixfs-dir0/foo1/link: no accessible property named "link"
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/
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
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar1/mode
cat: /ipfs/Qm-unixfs-dir0/foo1: no accessible property named "link"
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar1/mode
cat: /ipfs/Qm-unixfs-dir0/foo1/bar1: no accessible property named "mode"
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar1/size
cat: /ipfs/Qm-unixfs-dir0/foo1: no accessible property named "link"
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar1/size
cat: /ipfs/Qm-unixfs-dir0/foo1/bar1: no accessible property named "size"
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz2/
---
body: "hello\n"

> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz2/body
hello

>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz1/
---
files:
  - link: Qm-unixfs-file1
    size: 10
  - link: Qm-unixfs-file2
    size: 10
  - link: Qm-unixfs-file1
    size: 10
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz1/body
> # no body
```
