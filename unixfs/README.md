# unixfs IPLD Example

[This is an example to exercise IPLD](../).

[unixfs](//github.com/ipfs/spcs/tree/master/unixfs) is a datastructure for representing unix filesystems. Think of it like "files on IPFS". It aims to support basic unix and posix files, as well as all the extended attributes (xattr, etc).

## Spec

### Object Types

There are four _defined_ object types


- (defined) a `File` object representing files (binary sequences)
- (defined) a `Dir` object representing directories (name to object mappings)
- (defined) an `Archive` object representing bundled filesystems (tar, car, zip)
- (defined) a `Metadata` object to add mimetypes and other metadata.


#### Object: `File`

`File` objects represent unix/posix files, i.e. binary sequences. Like unix files, our `File` can be chunked into multiple subfiles. These are simply other `File` objects, which means a subfile is a `File` in its own right and can be accessed individually.

Files track:
- `files` a sequence of subfiles to be combined (for now, just concatenated)
- `importer` the id of the importer used to construct the `File` graph
- `body` is the data inside the file


#### Object: `Dir`

`Dir` objects represent unix/posix directories, i.e. maps of filename strings to files or directories. Like unix directories, our `Dir` can be sharded into multiple objects, to support efficient lookups in large directories. Other shards are simply other `Dir` objects, which means they are `Dirs` in their own right and can be accessed individually.

The names of `Dir` fields are the filenames of the objects. We aim to provide easy lookups.

#### Object: `Archive`

`Archive` objects represent unix/posix filesystem archives, i.e. files which themselves contain a sub-filesystem, for example `tar`, `car`, and `zip` archives. Special handling of these sub-filesystems takes advantage of IPFS features like deduplication, integrity checking, fast random access, etc.

#### Object: `Metadata`

`Metadata` objects track attributes for files, directories, and archives that can be applied to all. For example: mime types, permissions, and other properties. This allows a simple attribute change to only create 1 more small object, instead of duplicating the whole file root.

(TODO: this is at odds with mode in the Dir)

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

And unixfs-aware file/dir pathing:

- [unixfs pathing](paths-unixfs.md)
