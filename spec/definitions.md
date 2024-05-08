## Definitions

[[def: self-certifying identifier, SCID]]

~ An object identifier derived from initial data such that an attacker could not
create a new object with the same identifier. The input for a `did:tdw` SCID is
the initial DIDDoc with the placeholder `{SCID}` wherever the SCID is to be
placed.

[[def: base32_lower]]

~ Applies [[spec:rfc4648]] to convert
data to a `base32` encoding, and then lower cases the result. Data encoded as
base32 consists of a string of characters containing only the letters A-Z and
digits 2-7.

[[def: JSON Canonicalization Scheme]]

~ The [[spec:rfc8785]] canonicalizes a JSON
structure such that is suitable for verifiable hashing or signing.
