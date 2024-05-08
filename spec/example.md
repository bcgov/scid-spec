## `did:tdw` Example

The following shows an example of a [[ref: SCID]] being created. This
example uses the creation of a Decentralized Identifier (DID) that
has an associated SCID. The SCID is generated from the DID's associated
DIDDoc.

### DIDDoc with SCID Placeholders

This is the version of the DIDDoc that is the input to the
[SCID Generation Process](#scid-generation-and-validation). Note the `{SCID}` placeholders
where the [[ref: SCID]] will later be placed in the next step of the process.

```json
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    "https://w3id.org/security/multikey/v1"
  ],
  "id": "did:tdw:example.com:{SCID}",
  "controller": "did:tdw:example.com:{SCID}",
  "authentication": [
    "did:tdw:example.com:{SCID}#y4SDXopT"
  ],
  "assertionMethod": [
    "did:tdw:example.com:{SCID}#5b48Zj6B"
  ],
  "verificationMethod": [
    {
      "id": "did:tdw:example.com:{SCID}#y4SDXopT",
      "controller": "did:tdw:example.com:{SCID}",
      "type": "Multikey",
      "publicKeyMultibase": "z6Mksta2t7db1WSx2JBorfYFcJnaJMBKUyupD2qPy4SDXopT"
    },
    {
      "id": "did:tdw:example.com:{SCID}#5b48Zj6B",
      "controller": "did:tdw:example.com:{SCID}",
      "type": "Multikey",
      "publicKeyMultibase": "z6Mkw1KSvGWNAwSwWbcpwPgFARX4vKPa1xvcDMsJ5b48Zj6B"
    }
  ]
}
```

### DIDDoc with SCID In Place

After the [[ref: SCID]] is generated, the `{SCID}` placeholders are replaced by the generated [[ref: SCID]] value.
In this case, the [[ref: SCID]] is `4c99uuenu8gk6n3bgf09fuf350gx`

```json
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    "https://w3id.org/security/multikey/v1"
  ],
  "id": "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx",
  "controller": "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx",
  "authentication": [
    "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx#y4SDXopT"
  ],
  "assertionMethod": [
    "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx#5b48Zj6B"
  ],
  "verificationMethod": [
    {
      "id": "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx#y4SDXopT",
      "controller": "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx",
      "type": "Multikey",
      "publicKeyMultibase": "z6Mksta2t7db1WSx2JBorfYFcJnaJMBKUyupD2qPy4SDXopT"
    },
    {
      "id": "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx#5b48Zj6B",
      "controller": "did:tdw:example.com:4c99uuenu8gk6n3bgf09fuf350gx",
      "type": "Multikey",
      "publicKeyMultibase": "z6Mkw1KSvGWNAwSwWbcpwPgFARX4vKPa1xvcDMsJ5b48Zj6B"
    }
  ]
}
```

The [[ref: SCID]] is a stable identifier that can be embedded (in this case) in
the DID string. As the DIDDoc evolves over time, the SCID can be used to
demonstrate that future versions of the DID/DIDDoc evolved from the initial version
of the DIDDoc.
