# Common Security Requirements

**NOTE**: The key words **“MUST”**, **“MUST NOT”**, **“REQUIRED”**, **“SHALL”**, **“SHALL NOT”**, **“SHOULD”**,
**“SHOULD NOT”**, **“RECOMMENDED”**, **“MAY”**, and **“OPTIONAL”** in this document are to be interpreted
as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

The Icebreaker One (IB1) Trust Framework defines a security and trust model for shared data [APIs](../glossary.md#term-Application-programming-interface). Three
parties are involved in each shared data request:


1. The [Data Consumer](../glossary.md#term-Data-Consumer) wishing to access the [shared data](../glossary.md#term-Shared-data) [API](../glossary.md#term-Application-programming-interface)


2. The [authorization](../glossary.md#term-Authorization) server, as part of the governance service ([TFGS](../glossary.md#term-Trust-Framework-Governance-Service)), with knowledge about the
[Data Consumer](../glossary.md#term-Data-Consumer) as represented by an organisation account within the [TFGS](../glossary.md#term-Trust-Governance-Service)


3. The [Data Provider](../glossary.md#term-Data-Provider) responsible for supplying shared data through its shared data [API](../glossary.md#term-Application-programming-interface)

The interactions are shown graphically below in the form of a sequence diagram.

## Applicable standards

We use a strict sub-set of the [FAPI](../glossary.md#term-Financial-Grade-API) specification for interactions between [Data Providers](../glossary.md#term-Data-Provider) and [Data Consumers](../glossary.md#term-Data-Consumer). The
applicable standards are linked here for reference, we reference the precise elements of these standards in later
sections.


* [RFC6749 The OAuth 2.0 Authorization Framework](https://datatracker.ietf.org/doc/html/rfc6749)


* [RFC6750 The OAuth 2.0 Authorization Framework: Bearer Token Usage](https://datatracker.ietf.org/doc/html/rfc6750)


* [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html)


* [RFC8705 OAuth 2.0 Mutual-TLS Client Authentication and Certificate-Bound Access Tokens](https://www.rfc-editor.org/rfc/rfc8705.html)

### Discovery of endpoint URLs

While not strictly necessary, the authorization server deployed as part of the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) implements the OpenID Connect
Discovery provider configuration information endpoint as described
[here](https://openid.net/specs/openid-connect-discovery-1_0.html#ProviderConfig), references in this document to
e.g. `token_endpoint` refer to properties discoverable in this fashion.

## Token acquisition

In order to access a shared data [API](../glossary.md#term-Application-programming-interface), a [Data Consumer](../glossary.md#term-Data-Consumer) must first acquire an access token. This is done by sending an
[HTTP](../glossary.md#term-HypterText-Transfer-Protocol) request to the authorization server (part of the [OEGS](../glossary.md#term-Open-Energy-Governance-Service)). The [Data Consumer](../glossary.md#term-Data-Consumer) **MUST**:


* Use Mutual [TLS](../glossary.md#term-Transport-Layer-Security), presenting a client certificate when requested. This is the `tls_client_auth` authentication method
described in section 2 of [RFC8705](../glossary.md#term-OAuth-2.0-Mutual-TLS-Client-Authentication-and-Certificate-Bound-Access-Tokens).

> 
>     * In our implementation, this certificate is acquired by creating a `transport certificate` in a
> `software statement` within the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) directory


* Use the `client_credentials` grant type


* Send a `POST` request to the `token_endpoint` of the authorization server containing the following properties
as `application/x-www-form-urlencoded` key / value pairs:

```default
client_id : <CLIENT_ID>
scope: <REQUESTED_SCOPES>
grant_type: client_credentials
```

Scope may be omitted, for most uses within Open Energy there is no requirement to specify a scope. `CLIENT_ID` can
be obtained from the `software statement` within the directory corresponding to this client

A successful call to the `token_endpoint` is indicated by a `200` response code, in which case the body of the
response will contain a [JSON](../glossary.md#term-Javascript-Object-Notation) object with at least two properties:


1. `access_token` is an opaque string to be used as a bearer token for requests to resource servers
(a [Data Consumer](../glossary.md#term-Data-Consumer) [shared data](../glossary.md#term-Shared-data) [API](../glossary.md#term-Application-programming-interface) in our context)


2. `expires_in` is an integer number of seconds from the current time, after which the token will no longer be valid
- after this point the [Data Consumer](../glossary.md#term-Data-Consumer) **MUST** request a new token in order to continue to access shared data resources

## Token usage - calling a shared data API

To call a shared data [API](../glossary.md#term-Application-programming-interface) within a [Data Provider](../glossary.md#term-Data-Provider), the [Data Consumer](../glossary.md#term-Data-Consumer) MUST:


* Use Mutual [TLS](../glossary.md#term-Transport-Layer-Security) as previously described


* Pass the previously acquired bearer token in an [HTTP](../glossary.md#term-HypterText-Transfer-Protocol) header:

```default
Authorization: Bearer <TOKEN>
```

In addition, the [Data Consumer](../glossary.md#term-Data-Consumer) **SHOULD**:


* Specify an interaction [ID](../glossary.md#term-Identification) for this call in an [HTTP](../glossary.md#term-HypterText-Transfer-Protocol) header:

```default
x-fapi-interaction-id: <UUID>
```

This allows for tracking of transactions between clients and resource servers, aiding troubleshooting. We use a [UUID4](../glossary.md#term-Universally-unique-identififer-v4)
in our reference implementation

## Request validation

To participate in the Open Energy ecosystem, a [Data Provider](../glossary.md#term-Data-Provider) **MUST**:


* Expose an [HTTPS](../glossary.md#term-Secure-HTTP) [API](../glossary.md#term-Application-programming-interface)


* Perform validation on any requests to this [API](../glossary.md#term-Application-programming-interface)


    * Reject any requests which do not present a valid client certificate. Client certificates are validated in the
context of the root CAs provided by the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) directory.


    * Reject any requests which do not provide an `Authorization` header containing a `Bearer` token as described
above

If any of the above checks fail, the [Data Provider](../glossary.md#term-Data-Provider) **MUST NOT** continue processing the request, and **SHOULD** respond with
an error response as defined in [this section](https://datatracker.ietf.org/doc/html/rfc6750#section-6.2) of [RFC6750](../glossary.md#term-The-OAuth-2.0-Authorization-Framework-Bearer-Token-Usage)

### Token introspection

If all the above checks pass, the [Data Provider](../glossary.md#term-Data-Provider) **MUST** then validate the presented token. Tokens in our case are opaque
identifiers (as opposed to JWTs) and must be passed to the `introspection_endpoint` of the authorization server to
obtain additional information. To obtain this introspection response, the [Data Provider](../glossary.md#term-Data-Provider) **MUST**:


* Make a `POST` request to the `introspection_endpoint` of the authorization server


* Use Mutual [TLS](../glossary.md#term-Transport-Layer-Security), this means [Data Providers](../glossary.md#term-Data-Provider) must also have a provisioned client within the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) directory in the form
of a `software statement` and corresponding transport certificate


* Send the bearer token and client [ID](../glossary.md#term-Identification) of the [Data Provider](../glossary.md#term-Data-Provider) as an `application/x-www-form-urlencoded` body with the
following values:

```default
token: <BEARER_TOKEN>
client_id: <CLIENT_ID>
```

### Introspection response validation

The response body of this introspection call contains a [JSON](../glossary.md#term-Javascript-Object-Notation) object with information about the entity which requested
the supplied token from the authorization server, as well as properties of the token itself. An example introspection
response is shown below:

```json
{
  "active": true,
  "organisation_id": "8",
  "organisation_name": "A Demo Provider",
  "organisation_number": "8",
  "software_roles": [
    "EDSP_L1"
  ],
  "software_description": "Description: https://www.demo.org.uk/ is the location of our demo server",
  "additional_software_metadata": {
    "metadata": {
      "something": "something else"
    }
  },
  "client_id": "kZuAsn7UyZ98Wwh29hDpf",
  "exp": 1626279245,
  "iat": 1626278645,
  "iss": "https://auth.directory.energydata.org.uk",
  "scope": "directory:software",
  "cnf": {
    "x5t#S256": "rP_-9u3ZyVo4ryQxg-bn4rr6gJGNu1dTowEeppOuIt8"
  },
  "token_type": "Bearer"
}
```

The following elements of the introspection response **MUST** be validated further before any Open Energy specific
processing is performed:

#### active

If the introspection response does not contain the key `active`, or the value of this key is anything other than the
boolean `true` value, the [Data Provider](../glossary.md#term-Data-Provider) **MUST** reject the request and cease further processing.

If the `active` key was not present, it **SHOULD** respond with `400 invalid_request`

If the `active` key was present but not `true` it **SHOULD** respond with `401 invalid_token`

#### time ranges

If the introspection response contains `iat` this is interpreted as a number of seconds since the epoch at which the
token was issued. If this is in the future the [Data Provider](../glossary.md#term-Data-Provider) **MUST** reject the request and cease further processing. It
SHOULD respond with a `401 invalid_token`.

**NOTE**: The [Data Provider](../glossary.md#term-Data-Provider) **SHOULD** allow for a reasonable degree of clock skew when interpreting the `iat` timestamp, an
allowance of no more than 10 seconds should cover all reasonable cases.

If the introspection response contains `exp` this is interpreted as a number of seconds since the epoch after which
the token should be considered invalid. If this is in the past, the [Data Provider](../glossary.md#term-Data-Provider) **MUST** reject the request and cease
further processing. It **SHOULD** respond with a `401 invalid_token`

#### certificate thumbprint

Open Energy uses certificate pinning combined with MTLS on all requests between [Data Consumers](../glossary.md#term-Data-Consumer) and [Data Providers](../glossary.md#term-Data-Provider). This
ensures that a token issued to one client cannot be re-used by another client. [Data Providers](../glossary.md#term-Data-Provider) **MUST** check that the
thumbprint of the presented client certificate matches that provided within the introspection response.

The introspection response contains the SHA256 thumbprint of the certificate used to acquire the token as a nested
property `['cnf']['x5t#S256']`. This **MUST** be equal to the SHA256 thumbprint of the client certificate, if this is
not the case the [Data Provider](../glossary.md#term-Data-Provider) **MUST** reject the request and cease any further processing, responding with a
`401 invalid_token`

### Interaction header

If the `x-fapi-interaction-id` header is set in the request, it **MUST** be set to the same value in the response
header of the same name. If not set, a new ID **MUST** be generated and set in the response header.

### Other validation

If all the above checks have passed, the [Data Provider](../glossary.md#term-Data-Provider) can service the request and return whatever data were requested.
It **MAY**, however, apply additional checks based on information in the introspection response about the client. This
is where any Open Energy specific access control and licensing policies are applied.

To inform any additional processing, the [Data Provider](../glossary.md#term-Data-Provider) **MAY** make use of the
`['additional_client_metadata']['metadata']` key within the introspection response. This contains a [JSON](../glossary.md#term-Javascript-Object-Notation) object with
properties asserted about the [Data Consumer](../glossary.md#term-Data-Consumer). The exact set of properties is not defined here, please see the access
control language specification for more information about what could be specified.

[Data Providers](../glossary.md#term-Data-Provider) **MAY** make use of the `organisation_id` field in the token introspection response to uniquely and consistently
identify the organisation of the [Data Consumer](../glossary.md#term-Data-Consumer) where required, for example to reference a customer record within the [Data Provider](../glossary.md#term-Data-Provider).

More information on the Open Energy specific access control language can be found in
[Access Control and Capability Grant Language](../access_control_specification.md#access-control-and-capability-grant-language), and its expression in the metadata file at [Data Set Metadata](../metadata.md#data-set-metadata) in the
[Access Block](../metadata.md#access-block) section.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ0NTUwNjMxMl19
-->