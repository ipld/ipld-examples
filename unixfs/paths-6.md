# IPLD Pathing: (6) .object and .link accessors

These examples are IPLD pathing of the unixfs datastructure, in the "(6) .object and .link accessors" style.

```
> ipld cat /ipfs/Qm-post-msg1/title
"IPLD: last issues"

> ipld cat /ipfs/Qm-post-msg1/date
"2016-01-20 13:01:21.0 Z"

> ipld cat /ipfs/Qm-post-msg1/from.link/name
"Juan Benet" (from Qm-post-msg1)

> ipld cat /ipfs/Qm-post-msg1/from/name
> ipld cat /ipfs/Qm-post-msg1/from.object/name
"Juan Benet" (from Qm-identity-jbenet)

> ipld cat /ipfs/Qm-post-msg1/refs/0.link/title
"IPLD pathing" (from Qm-post-msg1)

> ipld cat /ipfs/Qm-post-msg1/refs/0/title
> ipld cat /ipfs/Qm-post-msg1/refs/0.object/title
"IPLD pathing" (from Qm-post-issue1)

> ipld cat /ipfs/Qm-post-msg1/refs/0
---
link: /ipfs/Qm-post-issue1
title: IPLD pathing

> ipld cat /ipfs/Qm-post-msg1/refs/0.link/link
"/ipfs/Qm-post-issue1"

> ipld cat /ipfs/Qm-post-msg1/refs/0/
> ipld cat /ipfs/Qm-post-msg1/refs/0.object
---
the document linked by /ipfs/Qm-post-issue1>
```
