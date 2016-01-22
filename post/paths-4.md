# IPLD Pathing: (4) different delimiters, strict

These examples are IPLD pathing of the unixfs datastructure, in the "(4) different delimiters, strict" style.

Here we use:
- `.` to delimit object-local properties (could be `/`)
- `/` to delimit link-object resolution (could be `//`)

```
> ipld cat /ipfs/Qm-post-msg1/title
"IPLD: last issues"

> ipld cat /ipfs/Qm-post-msg1/date
"2016-01-20 13:01:21.0 Z"

> ipld cat /ipfs/Qm-post-msg1/from.name
"Juan Benet" (from Qm-post-msg1)

> ipld cat /ipfs/Qm-post-msg1/from/name
"Juan Benet" (from Qm-identity-jbenet)

> ipld cat /ipfs/Qm-post-msg1/refs.0.title
"IPLD pathing" (from Qm-post-msg1)

> ipld cat /ipfs/Qm-post-msg1/refs.0/title
"IPLD pathing" (from Qm-post-issue1)

> ipld cat /ipfs/Qm-post-msg1/refs.0
---
link: /ipfs/Qm-post-issue1
title: IPLD pathing

> ipld cat /ipfs/Qm-post-msg1/refs.0.link
"/ipfs/Qm-post-issue1"

> ipld cat /ipfs/Qm-post-msg1/refs.0/
---
the document linked by /ipfs/Qm-post-issue1>
```
