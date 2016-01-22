# IPLD Pathing: (2) transparent, no link properties

These examples are IPLD pathing of the unixfs datastructure, in the "(2) transparent, no link properties" style.

**WARNING**: would need to change [example.yml](./example.yml) to remove link properties.

```
> ipld cat /ipfs/Qm-post-msg1/title
"IPLD: last issues"

> ipld cat /ipfs/Qm-post-msg1/date
"2016-01-20 13:01:21.0 Z"

> ipld cat /ipfs/Qm-post-msg1/from/name
"Juan Benet" (from Qm-identity-jbenet)

> ipld cat /ipfs/Qm-post-msg1/from/name
"Juan Benet" (from Qm-identity-jbenet)

> ipld cat /ipfs/Qm-post-msg1/refs/0/title
"IPLD pathing" (from Qm-post-issue1)

> ipld cat /ipfs/Qm-post-msg1/refs/0/title
"IPLD pathing" (from Qm-post-issue1)

> ipld cat /ipfs/Qm-post-msg1/refs/0
---
the document linked by /ipfs/Qm-post-issue1>
```

> ipld cat /ipfs/Qm-post-msg1/refs/0/link
cat: /ipfs/Qm-post-msg1/refs/0/link: no property named "link"

> ipld cat /ipfs/Qm-post-msg1/refs/0/
---
the document linked by /ipfs/Qm-post-issue1>
```
