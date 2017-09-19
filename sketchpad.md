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

Here are sketches of HTML-embedded revocation:
```json
{
  "revocation": {
    "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedRevocationObject"
  }
}
```
```json
{
  "revocation": {
    "id": "https://example.com/revocations/",
    "type": "HTMLEmbeddedRevocationObjectList"
  }
}
```
An HTML-embedded revocation object is a digitally-signed indication that a statement is revoked, embedded in a hypertext document as per [schema.org](http://schema.org) schemas or JSON-LD in a `<script>` element.
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
    "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
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
  "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
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
There may be a variety of types of revocation and an optional `reason` field could specify the reason for or variety of the revocation. A `reason` field could be for text values, values from an enumerated set, and/or link to machine-utilizable rationale.
```json
{
  "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
  "type": "Revocation",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "reason": "typographical-error",
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
This is what a revocation object might resemble which links to a machine-utilizable rationale explaining the revocation:
```json
{
  "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
  "type": "Revocation",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "reason": {
    "id": "https://example.com/rationale/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedRationale"
  },
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
Supersession objects can facilitate the modification, editing, revision, forwarding, redirection and replacement of statements.

A supersession object might resemble:
```json
{
  "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
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
There are a variety of types of supersession and an optional `reason` field could specify the reason for or the variety of the supersession. A `reason` field could be for text values, values from an enumerated set, and/or link to machine-utilizable rationale.
```json
{
  "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
  "type": ["Revocation", "Supersession"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "supersededBy": "https://example.com/facts/a3cc92841ac9c3f2/",
  "reason": "typographical-error",
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
This is what a supersession object might resemble which links to a machine-utilizable rationale explaining the supersession:
```json
{
  "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
  "type": ["Revocation", "Supersession"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "supersededBy": "https://example.com/facts/a3cc92841ac9c3f2/",
  "reason": {
    "id": "https://example.com/rationale/a3cc92841ac9c3f2/",
    "type": "HTMLEmbeddedRationale"
  },
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
Scenarios for machine-utilizable rationale include where the superseding statement is the logical opposite of the superseded statement and the rationale is the refutation of the superseded statement or the argumentation which convinced the issuer of the statements to retract _S_ and to assert _¬S_ instead.

There are a number of relationships possible between superseded and superseding statements and there also could be a field which semantically relates the superseded statement to the superseding statement from an extensible ontology. A verifiable claim could also be used to express a semantic relationship between two verifiable statements.

## Issuance and Statement Assertion Intervals

[https://w3c.github.io/vc-data-model/#issuer](https://w3c.github.io/vc-data-model/#issuer)

[https://w3c.github.io/vc-data-model/#expiration](https://w3c.github.io/vc-data-model/#expiration)

It is important to distinguish _issuance layer intervals_ from _content layer intervals_. Issuance layer intervals are the intervals of time that digitally-signed digital objects are valid or exist, a cryptographic or systems security topic. An issuance may only be available at a URL while valid, until it expires. Content layer intervals are the intervals of time that represented assertions of statements are intended. Content layer intervals may span one or more issuance intervals; the duration of an intended assertion may span across the durations of one or more digitally-signed objects.

Issuance layer fields include: `issued` and `expires`. In the [verifiable claims model](https://w3c.github.io/vc-data-model/), these are described as for _both_ the validity of the issuance and of the claim. Explored herein is a separate content layer atop an issuance layer.

Content layer fields include: `contentIssued` and `contentExpires`.

A field, `contentIssued` can indicate the start of an assertion and, if omitted, has a default value of `issued`. A field, `contentExpires` can indicate the end of an assertion and, if omitted, the assertion is intended while the issuance and any superseding issuances which contain the statement are valid.

If a verifiable statement indicates `expires` without indicating `contentExpires`, or if `contentExpires` has a value which occurs after that of `expires`, and if that statement indicates a value for `revocation`, then a system may check for a supersession when that issuance expires.

In the following example, the issuances expire annually and the statement assertion is open-ended:
```json
{
  "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",
  "statement": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
  },
  "revocation": {
    "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
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

And the superseding statement:
```json
{
  "id": "https://example.com/facts/b4dca3952b4bd203/",
  "type": "Statement",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2018-06-18T21:19:10Z",
  "expires": "2019-06-18T21:19:10Z",
  "contentIssued": "2017-06-18T21:19:10Z",
  "statement": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
  },
  "revocation": {
    "id": "https://example.com/revocations/b4dca3952b4bd203/",
    "type": "HTMLEmbeddedRevocationObject"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2018-06-18T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
    "nonce": "a1be2d9f-c7e7-469f-b252-97f7b1f8499a",
    "signatureValue": "A9xksT3/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+X43TW9="
  }
}
```

## Pausing and Resuming Statements
The idea here is that revocations and supersessions are content in the content layer atop the issuance layer. By using an explicit `contentExpires` field on a revocation, the revocation or supersession is temporary.
```json
{
  "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
  "type": "Revocation",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "expires": "2017-06-20T21:19:10Z",
  "contentExpires": "2017-06-20T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "reason": {
    "id": "https://example.com/rationale/ebfeb1f712ebc6f1/",
    "type": "HTMLEmbeddedRationale"
  },
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
    "id": "https://example.com/revocations/ebfeb1f712ebc6f1/",
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
