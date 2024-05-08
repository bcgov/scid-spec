# Self-Certifying Identifiers - SCIDs

The spec repository for generating and verifying SCIDs - Self Certifying Identifiers.

Read the spec: [https://bcgov.github.io/scid-spec/](https://bcgov.github.io/scid-spec/)

Implementations are available in the "Trust DID Web (did:tdw) DID Method implementations:

- Typescript: [https://github.com/bcgov/trustdidweb-ts](https://github.com/bcgov/trustdidweb-ts)
- Python: [https://github.com/bcgov/trustdidweb-py](https://github.com/bcgov/trustdidweb-py)

## Abstract

A self-certifying identifier (SCID) as defined in this specification is an identifier for, and embedded in.
a JSON object that is created on initial use of that object. The SCID remains consistent as
the object evolves, and is verifiable from the initial JSON object.

SCIDs are using the [Trust DID Web (did:tdw) DID Method].

[Trust DID Web (did:tdw) DID Method]: https://bcgov.github.io/trustdidweb/


## Contributing to the Specification

Pull requests (PRs) to this repository may be accepted. Each commit of a PR must
have a DCO (Developer Certificate of Origin -
[https://github.com/apps/dco](https://github.com/apps/dco)) sign-off. This can
be done from the command line by adding the `-s` (lower case) option on the `git
commit` command (e.g., `git commit -s -m "Comment about the commit"`).

Rendering and reviewing the spec locally for testing requires `npm` and `node`
installed. Follow these steps:

- Fork and locally clone the repository.
- Install `node` and `npm`.
- Run `npm install` from the root of your local repository.
- Edit the spec documents (in the `/spec` folder).
- Run `npm run render`'
  - Use `npm run edit` to interactively edit, render and review the spec.
- Review the resulting `index.html` file in a browser.

The specification is currently in
[Spec-Up](https://github.com/decentralized-identity/spec-up) format. See the
[Spec-Up Documentation](https://identity.foundation/spec-up/) for a list of
Spec-Up features and functionality.
