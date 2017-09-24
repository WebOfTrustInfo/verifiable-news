# Verifiable Statements

## Introduction
In the [verifiable claims data model](https://w3c.github.io/vc-data-model/), a _[claim](https://w3c.github.io/vc-data-model/#dfn-claim)_ is a statement about a subject and claims may be merged together to express a graph of information about a particular subject. A _verifiable claim_ is a claim that is tamper-resistant and whose authorship can be cryptographically verified.

The verifiable claims data model describes a datatype, `Credential`. A _[credential](https://w3c.github.io/vc-data-model/#dfn-credential)_ is a set of one or more claims made by the same entity about a subject. A _verifiable credential_ is a credential that is tamper-resistant and whose authorship can be cryptographically verified.

We can envision a new datatype, `Statement`. A _statement_ is an assertion by an entity. A _verifiable statement_ is a statement that is tamper-resistant and whose authorship can be cryptographically verified.

## Statements
```json
{
  "content": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
   }
}
```

```json
{
  "content": [{
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
   },{
    "value": "La Terre est la troisième planète du Soleil.",
    "lang": "fr",
    "contentType": "text/plain"
   }]
}
```

```json
{
  "content": {
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
  "content": [{
    "value": "cos(x) + 5",
    "contentType": "application/x-maple"
  },{
    "value": "Cos[x] + 5",
    "contentType": "application/vnd.wolfram.mathematica"
  },{
    "value": "\\cos x + 5",
    "contentType": "application/x-tex"
  },{
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
  "expires": "2018-06-18T21:19:10Z",
  "content": {
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

## Resource and Content Layers

[https://w3c.github.io/vc-data-model/#issuer](https://w3c.github.io/vc-data-model/#issuer)

[https://w3c.github.io/vc-data-model/#expiration](https://w3c.github.io/vc-data-model/#expiration)

It is important to distinguish _resource layer intervals_ from _content layer intervals_.

Resource layer intervals are the intervals of time that digitally-signed resources are valid or exist. It may be the case that resources are only available at URI's while valid, before they expire. Resource layer fields are `issued` and `expires`. In the [verifiable claims data model](https://w3c.github.io/vc-data-model/), these fields are defined as describing the duration of the validity of the claims of a credential and of the credential.

Content layer intervals are the intervals of time that content is to be asserted. The content layer exists atop the resource layer. Content layer fields are `contentIssued` and `contentExpires`. `contentIssued` indicates the start of an assertion of content and, if omitted, has a default value of the value of `issued`. `contentExpires` indicates the end of an assertion and, if omitted, the assertion is intended while the resource and any superseding resources which contain the content are valid.

If a verifiable statement indicates `expires` without indicating `contentExpires`, or if `contentExpires` has a value which occurs after that of `expires`, and if that statement indicates a value for `update`, then a system may check for an update, a supersession, when that resource expires.

## Updating Statements: Revocation and Supersession
Digitally-signed resources are immutable and transitory. The `update` field allows digitally-signed resources to be revoked or superseded. The `update` field points to lists or instances of _revocation objects_ or _supersession objects_.

```json
{
  "update": {
    "id": "https://example.com/updates/",
    "type": "UpdateList"
  }
}
```
```json
{
  "update": {
    "id": "https://example.com/updates/ebfeb1f712ebc6f1/",
    "type": "Update"
  }
}
```
```json
{
  "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "type": "Statement",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",  
  "content": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
  },
  "update": {
    "id": "https://example.com/updates/ebfeb1f712ebc6f1/",
    "type": "Update"
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

### Revocation
[https://w3c.github.io/vc-data-model/#revocation](https://w3c.github.io/vc-data-model/#revocation)

Revocation can facilitate the retraction, deletion, conclusion and cancellation of resources and statements.

A _revocation object_ might resemble:
```json
{
  "id": "https://example.com/updates/ebfeb1f712ebc6f1/",
  "type": ["Revocation", "Update"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",  
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

### Supersession
Supersession can facilitate the modification, editing, revision, forwarding, redirection and replacement of resources and statements.

A _supersession object_ might resemble:
```json
{
  "id": "https://example.com/updates/ebfeb1f712ebc6f1/",
  "type": ["Supersession", "Update"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",
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

### Temporary Revocations and Supersessions
A temporary revocation or supersession can be implemented by a revocation or supersession which expires before the revoked or superseded resource expires.

A temporary revocation can also be implemented by a supersession to a resource with a post-dated issuance.

### Rationale for Revocations or Supersessions
There may be a variety of types of revocation and supersession. An optional `reason` field can specify the reason for or the variety of the revocation. A `reason` field could be for text values, values from an enumerated set, and/or link to machine-utilizable rationale.
```json
{
  "id": "https://example.com/updates/ebfeb1f712ebc6f1/",
  "type": ["Revocation", "Update"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",  
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
This is what a supersession object might resemble which links to a machine-utilizable rationale explaining the supersession:
```json
{
  "id": "https://example.com/updates/ebfeb1f712ebc6f1/",
  "type": ["Supersession", "Update"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-19T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",
  "revoked": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "supersededBy": "https://example.com/facts/a3cc92841ac9c3f2/",
  "reason": {
    "id": "https://example.com/rationale/a3cc92841ac9c3f2/",
    "type": "Support"
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

## Supporting Statements: Evidence and Reasoning
[https://w3c.github.io/vc-data-model/#evidence](https://w3c.github.io/vc-data-model/#evidence)

This section discusses reasoning, rules, templates, evidence, sources and the citing and referencing of materials.

Here is a sketch of support:
```json
{
  "support": {
    "id": "https://example.com/support/ebfeb1f712ebc6f1/",
    "type": "Support"
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
  "expires": "2018-06-18T21:19:10Z",
  "content": {
    "value": "Earth is the third planet of the Sun.",
    "lang": "en",
    "contentType": "text/plain"
  },
  "support": [{
    "id": "https://example.com/support/fc0fc20823fcd702/",
    "type": "Support"
  },{
    "id": "https://example.com/support/0d10d319340de813/",
    "type": "Support"  
  }],
  "update": {
    "id": "https://example.com/updates/ebfeb1f712ebc6f1/",
    "type": "Update"
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
### Templates
A template is a digitally-signed, reusable resource with placeholder variables. Here is a rough-draft sketch:
```json
{
  "id": "https://templates.org/templates/astronomical-observation/",
  "type": "Template",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",
  "content": [{
    "value": "...lengthy JSON templates string...",
    "contentType": "text/template"
  },{
    "value": "...lengthy JSON templates string...",
    "contentType": "text/x-handlebars-template"
  }],
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://example.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }  
```
A template may also indicate its variables and acceptable schema per variable.

Utilization of templates involves referencing a specific template and providing values for its variables:
```json
{
  "template": {
    "id": "https://templates.org/templates/astronomical-observation/",
    "type": "Template"
  },
  "symbols": {
    "CONCLUSION": [{
      "value": "Earth is the third planet of the Sun.",
      "lang": "en",
      "contentType": "text/plain"
    },{
      "value": "La Terre est la troisième planète du Soleil.",
      "lang": "fr",
      "contentType": "text/plain"
    }],
    "OBSERVATION": "https://en.wikipedia.org/wiki/Earth"
  }
}
```
### Reasoning
Here is a sketch of an argument supporting a statement:
```json
{
  "id": "https://example.com/support/fc0fc20823fcd702/",
  "type": ["Support", "Argument", "Inference"],
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",
  "conclusion": "https://example.com/facts/ebfeb1f712ebc6f1/",
  "argument": {
    "id": "https://rules.org/rules/example-inference-rule/",
    "type": "Template"
  },
  "symbols": {
    "X": {
      "id": "https://example.com/facts/ebfeb1f712ebc6ef/",
      "type": "Statement"
    },
    "Y": {
      "id": "https://example.com/facts/ebfeb1f712ebc6f0/",
      "type": "Statement"
    },
    "Z": {
      "id": "https://example.com/facts/ebfeb1f712ebc6f1/",
      "type": "Statement"      
    }
  },
  "update": {
    "id": "https://example.com/updates/fc0fc20823fcd702/",
    "type": "Update"
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

## URI Schemes Other Than HTTP/HTTPS
URI schemes other than HTTP/HTTPS can be utilized, for example the [Magnet URI scheme](https://en.wikipedia.org/wiki/Magnet_URI_scheme) or [IPFS](https://en.wikipedia.org/wiki/InterPlanetary_File_System).
