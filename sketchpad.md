# Sketchpad

## Verifiable Statements
In the [verifiable claims data model](https://w3c.github.io/vc-data-model/), a _[claim](https://w3c.github.io/vc-data-model/#dfn-claim)_ is a statement about a subject and claims may be merged together to express a graph of information about a particular subject. A _verifiable claim_ is a claim that is tamper-resistant and whose authorship can be cryptographically verified.

The verifiable claims data model describes a datatype, `Credential`. A _[credential](https://w3c.github.io/vc-data-model/#dfn-credential)_ is a set of one or more claims made by the same entity about a subject. A _verifiable credential_ is a credential that is tamper-resistant and whose authorship can be cryptographically verified.

We can envision a new datatype, `Statement` ("claim" is already used in the domain, "factual claim" may be confusing...). A _statement_ is a set of one or more RDF literals which each assert the same content by the same entity. A _verifiable statement_ is a statement that is tamper-resistant and whose authorship can be cryptographically verified.

```json
{
  "claim": {
    "value": "Earth is the third planet of the Sun."
   }
}
```

```json
{
  "claim": [{
    "value": "Earth is the third planet of the Sun.",
    "lang": "en"
   },
   {
    "value": "La Terre est la troisième planète du Soleil.",
    "lang": "fr"
   }]
}
```

```json
{
  "claim": {
    "value": "The area of a circle with radius <math><mi>r</mi></math>
    is <math><mi>&pi;</mi><mo>&InvisibleTimes;</mo>
    <msup><mi>r</mi><mn>2</mn></msup></math>.",
    "lang": "en",
    "datatype": "http://www.w3.org/1999/02/22-rdf-syntax-ns#HTML"
  }
}
```
Here is a sketch of a _verifiable statement_:
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Earth is the third planet of the Sun."
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```

## HTTP-based Revocation
[https://w3c.github.io/vc-data-model/#revocation](https://w3c.github.io/vc-data-model/#revocation)

Two possibilities exist for HTTP-based revocation. In one, HTTP status code [`200`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) means that the statement is there, thus not revoked. In the other, HTTP status code [`200`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) means that a revocation object is available at a URL. The two HTTP-based approaches have opposite uses for [`200`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) and [`404`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) / [`410`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11). It makes sense to have both available for different systems.

Here is a sketch of HTTP-based revocation:
```json
{
  "revocation": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTTPBasedRevocation"
  }
}
```
The scenario indicated here is where the revocation URL is the statement URL. A URL is provided which returns HTTP status code HTTP status code [`200`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) if the statement is not revoked and status codes [`404`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) or [`410`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11) if the statement is revoked.
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Earth is the third planet of the Sun."
  },
  "revocation": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTTPBasedRevocation"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
The scenario indicated here is where the revocation URL is for a revocation object. A URL is provided which returns HTTP status code HTTP status code [`200`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) if the statement is revoked and status codes [`404`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) or [`410`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11) if the statement is not revoked.
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Earth is the third planet of the Sun."
  },
  "revocation": {
    "id": "https://www.journalistblog.com/users/1/revocations/ebfeb1f712ebc6f1/",
    "type": "HTTPBasedRevocation2"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```

## Evidence and Reasoning Supporting Statements
[https://w3c.github.io/vc-data-model/#evidence](https://w3c.github.io/vc-data-model/#evidence)

The idea here is that the evidence and reasoning supporting a statement can be located at a specified URL, the data embedded in a hypertext document as per [schema.org](http://schema.org) schemas or JSON-LD in a `<script>` element.

Here is a sketch of HTML-embedded schema evidence:
```json
{
  "evidence": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedSchema"
  }
}
```
and in the context of an example:
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Earth is the third planet of the Sun."
  },
  "revocation": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTTPBasedRevocation"
  },
  "evidence": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedSchema"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
