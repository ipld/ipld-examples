# POST IPLD Example

[This is an example to exercise IPLD](../).

[POST](//github.com/ipfs/POST) is a datastructure for representing communications. Think of it like "messages on IPFS". It aims to multiplex the various kinds of specific message datastructures (like email, IM, articles, blog posts, etc).


## Spec

### Object Types

There is one _defined_ object type, and two _latent_ (defined in other specs) object types.


- (defined) a `POST`
- (latent) an `Identity`, representing an individual or group (senders or recipients)
- (latent) a `Reference`, a reference to another document


#### Object: `POST`

A `POST` has several fields:



## Examples

### Object Examples

See the [example.yml](example.yml) document.

### Link Examples

Now, here are some ways I would expect to traverse this datastructure
using IPLD pathing.

```
> ipld cat /ipfs/Qm-post-msg1/title
"IPLD: last issues"

> ipld cat /ipfs/Qm-post-msg1/date
"2016-01-20 13:01:21.0 Z"

> ipld cat /ipfs/Qm-post-msg1/from/name
> ipld cat /ipfs/Qm-post-msg1/from.name
"Juan Benet" (from Qm-post-msg1)

> ipld cat /ipfs/Qm-post-msg1/from/link/name
> ipld cat /ipfs/Qm-post-msg1/from/@/name
> ipld cat /ipfs/Qm-post-msg1/from//name
"Juan Benet" (from Qm-identity-jbenet)

> ipld cat /ipfs/Qm-post-msg1/refs/0/title
> ipld cat /ipfs/Qm-post-msg1/refs.0.title
"IPLD pathing" (from Qm-post-msg1)

> ipld cat /ipfs/Qm-post-msg1/refs/0/link/title
> ipld cat /ipfs/Qm-post-msg1/refs/0//title
"IPLD pathing" (from Qm-post-issue1)

> ipld cat /ipfs/Qm-post-msg1/refs/0
---
link: /ipfs/Qm-post-issue1
title: IPLD pathing

> ipld cat /ipfs/Qm-post-msg1/refs/0/link
"/ipfs/Qm-post-issue1"

> ipld cat /ipfs/Qm-post-msg1/refs/0/link/
> ipld cat /ipfs/Qm-post-msg1/refs/0//
---
the document linked by /ipfs/Qm-post-issue1>
```
