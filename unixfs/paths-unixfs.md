# unixfs Pathing

These examples use a "unixfs-aware" pathing, implemented on top of the raw ipld merkle dag. This makes an additional layer which is aware of what the datastructure represents (eg concatenating the bodies of files, etc). This is already sort-of done in `ipfs cat, ls`. (This remains constant throughout the unixfs examples)

```
> unixfs cat /ipfs/Qm-unixfs-dir0/foo1
cat: /ipfs/Qm-unixfs-dir1/foo0: Is a directory
>
> unixfs ls /ipfs/Qm-unixfs-dir0/foo1
bar1
bar2
>
> unixfs cat /ipfs/Qm-unixfs-dir0/foo1/link
cat: /ipfs/Qm-unixfs-dir0/foo1/link: No such file or directory
>
> unixfs cat /ipfs/Qm-unixfs-dir0/foo1/bar1/mode
cat: /ipfs/Qm-unixfs-dir0/foo1/mode: No such file or directory
>
> unixfs stat /ipfs/Qm-unixfs-dir0/foo1/bar1
name: bar1
mode: 0777
size: 120
>
> unixfs stat --fmt line /ipfs/Qm-unixfs-dir0/foo1/bar1
0777  120   bar1
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz2
hello

>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz2/body
cat: /ipfs/Qm-unixfs-dir0/foo1/bar2/baz2: Not a directory
>
> ipld cat /ipfs/Qm-unixfs-dir0/foo1/bar2/baz1
hello
world
hello

```
