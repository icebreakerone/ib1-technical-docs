# Registry Structure

The Registry is the machine-readable description of the Trust Framework and the Schemes within it as a linked set of RDF Resources describing the component parts. It describes the rules and the technical standards that are used to exchange data between participants.

These RDF resources are made available using three formats, RDF/XML, Turtle, and JSON-LD, along with a human readable interpretation. Each resource has a URL that is the unique identifier, and if visited in a web browser, will show the human readable interpretation of what the resource represents.

The resource URLs are embedded in the data, metadata, and audit records. To preserve the meaning of these records, once created, every resource is never changed. If a revised version is necessary, a separate resource is created, along with Registry metadata to describe the relationship between the versions and the reason why the change was made.
