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

Some possilbe ways to traverse this datastructure using IPLD pathing:

- 1) [transparent, no link properties access](paths-1.md)
- 2) [transparent, no link properties](paths-2.md)
- 3) [transparent, hope for the best](paths-3.md)
- 4) [different delimiters, strict](paths-4.md)
- 5) [different delimiters, permissive](paths-5.md)
- 6) [.object and .link accessors](paths-6.md)
- 7) [use explicit `link/` to resolve through](paths-7.md)
- 8) [different delimiters, strict and explicit `link/`](paths-8.md)
