**This repository is no longer maintained, see https://ipld.io for the latest information on IPLD and its use.**

# IPLD Examples

[![](https://img.shields.io/badge/made%20by-Protocol%20Labs-blue.svg?style=flat-square)](http://ipn.io)
[![](https://img.shields.io/badge/project-IPFS-blue.svg?style=flat-square)](http://ipfs.io/)
[![](https://img.shields.io/badge/freenode-%23ipfs-blue.svg?style=flat-square)](http://webchat.freenode.net/?channels=%23ipfs)

This repo contains several datastructure examples to use with [IPLD](//github.com/ipfs/specs/tree/master/ipld), the new data format for IPFS.

These examples aim to be complete.

## Contents

- (todo) [foaf](foaf) SW/LD style FOAF
- (todo) [identity](identity) a basic identity system
- (todo) [keychain](keychain) a draft for [the keychain datastruct](//github.com/ipfs/specs/tree/master/keychain)
- (wip) [mediachain](mediachain) a draft for the Mine [Mediachain](//medium.com/mine-labs/mediachain-483f49cbe37a)
- (todo) [minecraft](minecraft) for a minecraft like game.
- (todo) [multikey](multikey) a draft for [the multikey format](//github.com/jbenet/multikey)
- (todo) [orbit](orbit) a draft for [orbit](//github.com/haadcode/anonymous-networks)
- (ok) [post](post) a draft for [POST](//github.com/ipfs/POST)
- (todo) [schema.org](schema.org) a draft for the [schema.org](//schema.org) datastructs.
- (todo) [sharding](sharding) a draft for [IPFS object sharding](//github.com/ipfs/notes/issues/76)
- (ok) [unixfs](unixfs) a draft for [IPFS unixfs](//github.com/ipfs/specs/tree/master/unixfs)
- (todo) [uport](uport) a draft for the Ethereum/ConsenSys uPort wallet profiles

## Experiment

### Pathing Semantics

How to structure pathing and resolution through objects is a troublesome issue. You can read [the IPLD spec here](https://github.com/ipfs/specs/blob/ipld-spec/merkledag/ipld.md) and read [some of the arguments here](https://github.com/ipfs/specs/pull/37).

The problem boils down to an issue introduced by the combination of **link-local properties** (properties on the link object itself) and **transparent resolution of objects and links** (using a single delimiter for traversing objects and links).

To resolve this, a number of variations have been presented:

- **1) transparent, no link properties access** use only `/` but disallow accessing link-local properties. cons: cannot access link properties :(
- **2) transparent, no link properties** use only `/` but disallow using link-local properties. cons: cannot HAVE link properties :c
- **3) transparent, hope for the best** use only `/` and _define_ the order the accesses happen, so that it is not ambiguous. cons: it may be confusing.
- **4) different delimiters, strict** - use different delimiters for "link local" and "link resolving" components (eg `. /` or `/ //`). cons: two delimiters, escaping or incompatibilities
- **5) different delimiters, permissive** like (3) + (4), allow different delimiters to disambiguate "link local" and "link resolving" components
- **6) .object and .link accessors** use explicit `.object` to access the object resolved through, and/or `.link` for accessing link local properties.
- **7) use explicit `link/` to resolve through** (or some other operator string/char) con: a/link/b/link/c/link typing.
- **8) different delimiters, strict and explicit `link/`**, a combination of (4) and (7).

One goal of this repo is to experiment with these and see which feels best.

## Contribute

Feel free to join in. All welcome. Open an [issue](https://github.com/ipfs/ipld-examples/issues)!

This repository falls under the IPFS [Code of Conduct](https://github.com/ipfs/community/blob/master/code-of-conduct.md).

[![](https://cdn.rawgit.com/jbenet/contribute-ipfs-gif/master/img/contribute.gif)](https://github.com/ipfs/community/blob/master/contributing.md)

## License

[MIT](LICENSE)
