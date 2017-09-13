# Sketchpad

## Factual Claims
In the [verifiable claims data model](https://w3c.github.io/vc-data-model/#claims), a _claim_ is a statement about a subject and claims may be merged together to express a graph of information about a particular subject. A _verifiable claim_ is a claim that is tamper-resistant and whose authorship can be cryptographically verified.

The verifiable claims data model describes a datatype, `Credential`. A _[credential](https://w3c.github.io/vc-data-model/#dfn-credential)_ is a set of one or more claims made by the same entity about a subject. A _verifiable credential_ is a credential that is tamper-resistant and whose authorship can be cryptographically verified.

Envisioning a new datatype, e.g. `Claim`, here are some sketches showing a variety of "claims", _factual claims_, which are one or more RDF literals (see also [https://www.w3.org/TR/rdf-json/](https://www.w3.org/TR/rdf-json/)). Adding verifiability to this data structure results in _verifiable factual claims_ which are tamper-resistant and whose authorship can be cryptographically verified.

```json
{
  "claim": {
    "value": "Lorem ipsum dolor sit amet."
   }
}
```

```json
{
  "claim": [{
    "value": "Lorem ipsum dolor sit amet.",
    "lang": "en"
   },
   {
    "value": "Consectetur adipiscing elit.",
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

Here is an example of a _verifiable factual claim_:
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
  "type": "Claim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Lorem ipsum dolor sit amet."
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
The idea here is that a URL can be provided which returns HTTP status code [`404`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) or [`410`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11) if the claim is revoked and HTTP status code [`200`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) if the claim is not revoked.

[https://w3c.github.io/vc-data-model/#revocation](https://w3c.github.io/vc-data-model/#revocation)

Here is a sketch of HTTP-based revocation:
```json
{
  "revocation": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTTPBasedRevocation"
  }
}
```
and in the context of an example:
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/",
  "type": "Claim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Lorem ipsum dolor sit amet."
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

## Evidence and Reasoning Supporting Claims
The idea here is that the evidence and reasoning supporting a claim can be located at a specified URL, the data embedded in a hypertext document as per [schema.org](http://schema.org) schemas or JSON-LD in a `<script>` element.

[https://w3c.github.io/vc-data-model/#evidence](https://w3c.github.io/vc-data-model/#evidence)

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
  "type": "Claim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Lorem ipsum dolor sit amet."
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
