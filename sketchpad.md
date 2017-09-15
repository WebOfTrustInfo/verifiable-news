# Sketchpad

## Verifiable Statements
In the [verifiable claims data model](https://w3c.github.io/vc-data-model/), a _[claim](https://w3c.github.io/vc-data-model/#dfn-claim)_ is a statement about a subject and claims may be merged together to express a graph of information about a particular subject. A _verifiable claim_ is a claim that is tamper-resistant and whose authorship can be cryptographically verified.

The verifiable claims data model describes a datatype, `Credential`. A _[credential](https://w3c.github.io/vc-data-model/#dfn-credential)_ is a set of one or more claims made by the same entity about a subject. A _verifiable credential_ is a credential that is tamper-resistant and whose authorship can be cryptographically verified.

We can envision a new datatype, `Statement`. A _statement_ is an assertion by an entity. A _verifiable statement_ is a statement that is tamper-resistant and whose authorship can be cryptographically verified.

```json
{
  "statement": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
   }
}
```

```json
{
  "statement": [{
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
   },
   {
    "value": "La Terre est la troisième planète du Soleil.",
    "lang": "fr",
    "contentType": "text/plain"
   }]
}
```

```json
{
  "statement": {
    "value": "The area of a circle with radius <math><mi>r</mi></math>
    is <math><mi>&pi;</mi><mo>&InvisibleTimes;</mo>
    <msup><mi>r</mi><mn>2</mn></msup></math>.",
    "lang": "en",
    "contentType": "text/html"
  }
}
```

```json
{
  "statement": [{
    "value": "cos(x) + 5",
    "contentType": "application/x-maple"
  },
  {
    "value": "Cos[x] + 5",
    "contentType": "application/vnd.wolfram.mathematica"
  },
  {
    "value": "\\cos x + 5",
    "contentType": "application/x-tex"
  },
  {
    "value": "<OMA xmlns='http://www.openmath.org/OpenMath'>
    <OMA><OMS cd='arith1' name='plus'/>
    <OMA><OMS cd='transc1' name='cos'/><OMV name='x'/></OMA>
    <OMI>5</OMI></OMA></OMA>",
    "contentType": "application/openmath+xml"
  }]
}
```

Here is a sketch of a _verifiable statement_:
```json
{
  "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "statement": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```

## Revocation of Statements
[https://w3c.github.io/vc-data-model/#revocation](https://w3c.github.io/vc-data-model/#revocation)

Here is a sketch of HTML-embedded revocation:
```json
{
  "revocation": {
    "id": "https://example.com/users/1/revocations/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedRevocationObject"
  }
}
```
A revocation object is a digitally-signed indication that a statement is revoked, embedded in a hypertext document as per [schema.org](http://schema.org) schemas or JSON-LD in a `<script>` element. If a statement is not revoked, then the server should return HTTP status code `404` for the revocation object URL.
```json
{
  "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "statement": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
  },
  "revocation": {
    "id": "https://example.com/users/1/revocations/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedRevocationObject"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
A revocation object might resemble:
```json
{
  "id": "https://example.com/users/1/revocations/ebfeb1f712ebc6f1/",
  "type": "Revocation",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-19T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```

## Supersession of Statements
Supersession objects can facilitate the modification and forwarding/redirection of statements. Supersession can allow users the capability to edit statements and also to forward/redirect statements between domains.

A supersession object might resemble:
```json
{
  "id": "https://example.com/users/1/revocations/ebfeb1f712ebc6f1/",
  "type": ["Revocation", "Supersession"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "supersededBy": "https://example.com/facts/a3cc92841ac9c3f2/",
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-19T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
A `reason` field can specify the reason for the supersession.

```json
{
  "id": "https://example.com/users/1/revocations/ebfeb1f712ebc6f1/",
  "type": ["Revocation", "Supersession"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "supersededBy": "https://example.com/facts/a3cc92841ac9c3f2/",
  "reason": "typographical",
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-19T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
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
    "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedEvidence"
  }
}
```
and in the context of an example:
```json
{
  "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "statement": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
  },
  "revocation": {
    "id": "https://example.com/users/1/revocations/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedRevocationObject"
  },
  "evidence": {
    "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedEvidence"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
