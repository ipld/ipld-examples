# IPLD Pathing: (7) use explicit `link/` to resolve through

These examples are IPLD pathing of the unixfs datastructure, in the "(7) use explicit `link/` to resolve through" style.

```
> ipld cat /ipfs/Qm-unixfs-dir0/foo1
---
link: /ipfs/Qm-unixfs-dir1
mode: 0777
size: 220

> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link
"/ipfs/Qm-unixfs-dir1"
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/
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
0777
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar1/size
120
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar2/link/baz2/link/
---
body: "hello\n"

> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar2/link/baz2/link/body
hello

>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar2/link/baz1/link/
---
files:
  - link: Qm-unixfs-file1
    size: 10
  - link: Qm-unixfs-file2
    size: 10
  - link: Qm-unixfs-file1
    size: 10
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar2/link/baz1/link/body
> # no body
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/link/bar2/link/link/link/
# No ambiguity because the link key in Qm-unixfs-dir2 is an object and not a
# string representing a link.
---
body: "hello\n"

```
