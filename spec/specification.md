## Selef-Certifying Identifier (SCID) Specification

The [[ref: SCID]], a globally unique identifier, is generated as part of the
creation of an object and used as or placed into an identifier for the object.

### Create (Register) SCID

Creating a [[ref: SCID]] is done by carrying out the following steps.

1. Define the identifier string, including where the [[ref: SCID]] will be
   placed. Identify (using the placeholder `{SCID}`) where the required [[ref:
   SCID]] will be placed in the identifier string (ie. `did:tdw:example.com:{SCID}`).
2. Create the initial JSON object (e.g., `did.json`) object to which the SCID applies, with whatever
   content is required. Wherever there is self-reference to the SCID in the
   content, use the `{SCID}`
   placeholder for the [[ref: SCID]] (ie. `did:tdw:example.com:{SCID}#key-1`).
3. Calculate the [[ref: SCID]] for the identified object as defined in the [SCID Generation
      and Validation](#scid-generation-and-validation) section of this
      specification.
4. Replace in the content the placeholder for the [[ref: SCID]] `{SCID}` with
      the calculated `SCID`.

### Read (Resolve)

For the initial version of the content, verify that the [[ref: SCID]] that is or
is embedded in the identifier verifies according to the [SCID Generation and
Verification](#scid-generation-and-validation) section of this specification.

### SCID Generation and Validation

The [[ref: Self-certifying identifier]] or `scid` is derived from the
initial content of the identified object, and forms some or all of the
object identifier.

#### Generate SCID

To generate the required [[ref: SCID]] for an identifier a Controller
**MUST** execute the following function:

 `left(base32_lower(hash(JCS(initial object content with placeholders))), <length>)`

Where:

1. The `initial object content with placeholders` is the initial content defined by the
   [[ref: Controller]] for the object, with the placeholder `{SCID}` put everywhere the
   [[ref: SCID]] will be used in the resolved version 1 of the content. At minimum, the
   `{SCID}` **MUST** appear in the top level `id` item of the content. It **MAY**
   occur elsewhere in the content.
2. `JCS` is an implementation of the [[ref: JSON Canonicalization Scheme]]
   [[spec:rfc8785]]. It outputs a canonicalized representation of its input.
3. `hash` is either `sha256` or an alternative hash algorithm defined in the
   `hash` item in the [[ref: parameters]]. Its output is the hash of its input.
4. `base32_lower` as defined by the [[ref: base32_lower]] function. Its output
   is the lower case of the Base32 encoded string of its input.
5. `left` extracts the `<length>` number of characters from the string input.
   1. `<length>` **MUST** be at least 28 characters.

#### Verify SCID

To verify the [[ref: SCID]] of a SCID-based identifier being resolved, the resolver
**MUST** execute the following process:

1. Extract the [[ref: SCID]] from the identifier.
2. Verify that the length of the `scid` is at least 28 characters.
   1. If less than 28 characters, terminate the resolution process with an
      error.
3. Extract or retrieve the first version of the object content.
4. Treat the content as a string and do a text replacement of the `scid` value
   from the first step with the string `{SCID}`. This should result in the `initial content object
   with placeholders` data needed for the next step.
5. Execute the hashing process defined in the generation defined above to
   generate the value `calculatedSCID`.
   1. For the `<length>` value, use the length of the `scid` extracted in step
      1.
6. Verify that the `scid` matches the `calculatedSCID`.
