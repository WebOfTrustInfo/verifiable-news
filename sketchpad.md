# Verifiable Statements

## Introduction
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

## Supporting Statements: Templates, Rules, Sources, Citations, Evidence, Reasoning and Argumentation
[https://w3c.github.io/vc-data-model/#evidence](https://w3c.github.io/vc-data-model/#evidence)

This section discusses templates, rules, sources, the citing and referencing of materials, evidence, reasoning and argumentation.

### JSON Include

[https://tools.ietf.org/html/rfc6901](https://tools.ietf.org/html/rfc6901)

[https://tools.ietf.org/html/draft-pbryan-zyp-json-ref-03](https://tools.ietf.org/html/draft-pbryan-zyp-json-ref-03)

[http://json-schema.org/latest/json-schema-core.html#rfc.section.8](http://json-schema.org/latest/json-schema-core.html#rfc.section.8)

[https://tools.ietf.org/html/draft-luff-relative-json-pointer-00](https://tools.ietf.org/html/draft-luff-relative-json-pointer-00)

[https://www.w3.org/TR/xinclude-11/](https://www.w3.org/TR/xinclude-11/)

[https://wiki.whatwg.org/wiki/Link_Hashes](https://wiki.whatwg.org/wiki/Link_Hashes)

A general-purpose "JSON include" solution resembles:
```json
{ "$include": "https://web.com/content/resource.json" }
```
and a path to content can be specified:
```json
{ "$include": "https://web.com/content/resource.json#foo/baz" }
```

### Templates
A [template processor](https://en.wikipedia.org/wiki/Template_processor) (also known as a template engine or template parser) is software designed to combine templates with a data model to produce result documents.

In the following rough-draft sketch, the templates of types `text/template` and `text/x-handlebars-template` are strings which, for identical inputs, process into identical JSON outputs.
```json
{
  "id": "https://templates.org/astronomical-observation/",
  "type": "Template",
  "issuer": "https://example.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "expires": "2018-06-18T21:19:10Z",
  "content": [{
    "value": "...template string which processes to JSON...",
    "contentType": "text/template"
  },{
    "value": "...template string which processes to JSON...",
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
A template may also describe its data model, indicating a list of variables and the schema acceptable per variable.

Utilization of templates involves referencing a specific template and providing a data model:
```json
{
  "template": {
    "id": "https://templates.org/astronomical-observation/",
    "type": "Template"
  },
  "data": {
    "CONCLUSION": [{
      "value": "Earth is the third planet of the Sun.",
      "lang": "en",
      "contentType": "text/plain"
    },{
      "value": "La Terre est la troisième planète du Soleil.",
      "lang": "fr",
      "contentType": "text/plain"
    }],
    "OBSERVATIONS": ["https://en.wikipedia.org/wiki/Earth"]
  }
}
```
Templating could be built into JSON, JSON-LD, or a dialect. A syntax can indicate the JSON from a processed template for [transclusion](https://en.wikipedia.org/wiki/Transclusion):
```json
{
  "$template": "https://templates.org/astronomical-observation/",
  "$data": {
     "CONCLUSION": [{
      "value": "Earth is the third planet of the Sun.",
      "lang": "en",
      "contentType": "text/plain"
    },{
      "value": "La Terre est la troisième planète du Soleil.",
      "lang": "fr",
      "contentType": "text/plain"
    }],
    "OBSERVATIONS": ["https://en.wikipedia.org/wiki/Earth"]
  }
}
```
A path to content from the processed template for transclusion can be specified:
```json
{
  "$template": "https://templates.org/astronomical-observation/#foo/baz",
  "$data": {
     "CONCLUSION": [{
      "value": "Earth is the third planet of the Sun.",
      "lang": "en",
      "contentType": "text/plain"
    },{
      "value": "La Terre est la troisième planète du Soleil.",
      "lang": "fr",
      "contentType": "text/plain"
    }],
    "OBSERVATIONS": ["https://en.wikipedia.org/wiki/Earth"]
  }
}
```
Interesting topics include recursion, templates which process into resources which invoke templates.

## URI Schemes Other Than HTTP/HTTPS
URI schemes other than HTTP/HTTPS can be utilized, for example the [Magnet URI scheme](https://en.wikipedia.org/wiki/Magnet_URI_scheme) or [IPFS](https://en.wikipedia.org/wiki/InterPlanetary_File_System).
