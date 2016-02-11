# Mediachain IPLD Example

[This is an example to exercise IPLD](../).

[mediachain](https://github.com/mediachain/mediachain) is a datastructure and set of conventions for representing media (images, audio, video) metadata. The outer (encapsulating) "meta-metadata" structure is stable, while the inner (encapsulated) structure is a flexible representation of a 3rd party schema.

### Encapsulating Object
The outer scope represents the stable, mediachain-specific data. It looks something like this
```json
{
  "@type": "Mediachain",
  "statements": [
    {
      "ts": "2007-03-01T13:00:00Z",
      "@mediachain_type": "NYPL-0.1",
      "link": "Qm..."
    }
  ]
}
```

### Encapsulated Object
The inner scope can represent either a standard Mediachain native schema object (see below) or an appropriately labeled 3rd party object, which the client will understand semantically based on the label. The format of this object can vary, with the primary restriction of being encodable as JSON-LD, with no circular references.

### Object Types
The standard, native object format is based on [schema.org Creative Work](http://schema.org/CreativeWork) and respective subtypes (MusicRecording, Photograph, etc). The objects should translate cleanly to the corresponding JSON-LD schema.org types.

### Resolver Table
TBD

### Object Examples

See [example.yml](example.yml)

### See also
- [IIIF](http://iiif.io/api/presentation/2.0/) -- potential standard to interop with
