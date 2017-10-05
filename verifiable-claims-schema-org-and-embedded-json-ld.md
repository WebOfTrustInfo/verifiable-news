# Verifiable Claims, Schema.org and Embedded JSON-LD
### Approach 1: Add `profile` to `Person` and Digitally Sign JSON-LD Content using DID Document Keys
A [_profile_](https://w3c.github.io/vc-data-model/#dfn-profile) is a set of one or more credentials typically related to the same subject. An entity may have multiple profiles and each profile may contain verifiable credentials issued by multiple issuers. A _verifiable profile_ is a profile that is tamper-resistant and whose contents are typically counter-signed by the holder or subject.
```html
<!DOCTYPE html>
<html>
  <head>
    <script type="application/ld+json">
{
  "@context": [
    "http://schema.org",
    "https://w3id.org/identity/v1",
    "https://w3id.org/security/v1"
  ],
  "@type": "ReportageNewsArticle",
  "headline": "Example News Article",
  "description": "An example news article.",
  "url": "https://www.news.com/article.html",
  "image": {
    "@type": "ImageObject",
    "url": "https://www.news.com/img.png",
    "width": "1200",
    "height": "630"
  },
  "author": [{
    "@type": "Person",
    "name": "John Smith",
    "givenName": "John",
    "familyName": "Smith",
    "profile": {
      "id": "did:example:ebfeb1f712ebc6f1c276e12ec21",
      "credential": [{
        "id": "...",
        "type": "Credential",
        "issuer": "...",
        "issued": "2010-01-01T19:73:24Z",
        "claim": {
          "id": "did:example:ebfeb1f712ebc6f1c276e12ec21",
          "name": "John Smith",
          "givenName": "John",
          "familyName": "Smith"
        },
        "signature": {
          "type": "LinkedDataSignature2017",
          "created": "2017-06-17T10:03:48Z",
          "creator": "...",
          "nonce": "d61c4599-0cc2-4479-9efc-c63add3a43b2",
          "signatureValue": "pYw8XNi1bgVg/sCneO4BavEll0/I1zJugez8RwDg/+
          ibcC1wpsMCRVpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuF
          zvueMWmFPRdW+gGsutPTLhwYmfIFpbBu95t501+rSLHIEuujM/+PXr+W3JT24
          9Cky6Ed="
        }
      }],
      "signature": [{
        "type": "LinkedDataSignature2017",
        "created": "2017-06-18T21:19:10Z",
        "creator": "did:example:ebfeb1f712ebc6f1c276e12ec21/keys/2",
        "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
        "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+
        MCRVpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wps
        PRdW+gGsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed
        +W3JT24="
      }]
    }
  }],
  "signature": [{
    "type": "LinkedDataSignature2017",
    "created": "2017-09-29T22:55:50Z",
    "creator": "did:example:ebfeb1f712ebc6f1c276e12ec21/keys/2",
    "nonce": "d1bf2d9f-d8f8-57a0-c363-97f7b1f8498f",
    "signatureValue": "rSeVAO2CpMoI6AitKyAyZwwHdSh448iimcY5Rp4XWT
    TuJwkWXlBF2iAq/1g/kg82Tb+fZmXJOdqzJe+xOFUCpRLdf2Rwi2pj3hTpvSi
    fFJ0v3ze8YQeH0HeFrlu+Re78XT4Lluo6Hv88BoqGqi3gjD70di+wCwg4329H
    x8idxy8="
  }]
}
    </script>
  </head>
  <body>
    <!-- journalistic content -->
  </body>
</html>
```

### Approach 2: Add `credentials` to `Person` and Digitally Sign JSON-LD Content using DID Document Keys
A [_credential_](https://w3c.github.io/vc-data-model/#dfn-credential) is a set of one or more claims made by the same entity about a subject. A _verifiable credential_ is a credential that is tamper-resistant and whose authorship can be cryptographically verified.
```html
<!DOCTYPE html>
<html>
  <head>
    <script type="application/ld+json">
{
  "@context": [
    "http://schema.org",
    "https://w3id.org/identity/v1",
    "https://w3id.org/security/v1"
  ],
  "@type": "ReportageNewsArticle",
  "headline": "Example News Article",
  "description": "An example news article.",
  "url": "https://www.news.com/article.html",
  "image": {
    "@type": "ImageObject",
    "url": "https://www.news.com/img.png",
    "width": "1200",
    "height": "630"
  },
  "author": [{
    "@type": "Person",
    "name": "John Smith",
    "givenName": "John",
    "familyName": "Smith",
    "credentials": [{
        "id": "...",
        "type": "Credential",
        "issuer": "...",
        "issued": "2010-01-01T19:73:24Z",
        "claim": {
          "id": "did:example:ebfeb1f712ebc6f1c276e12ec21",
          "name": "John Smith",
          "givenName": "John",
          "familyName": "Smith"
        },
        "signature": {
          "type": "LinkedDataSignature2017",
          "created": "2017-06-17T10:03:48Z",
          "creator": "...",
          "nonce": "d61c4599-0cc2-4479-9efc-c63add3a43b2",
          "signatureValue": "pYw8XNi1bgVg/sCneO4BavEll0/I1zJugez8RwDg/+
          ibcC1wpsMCRVpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuF
          zvueMWmFPRdW+gGsutPTLhwYmfIFpbBu95t501+rSLHIEuujM/+PXr+W3JT24
          9Cky6Ed="
        }
     }]
  }],
  "signature": [{
    "type": "LinkedDataSignature2017",
    "created": "2017-09-29T22:55:50Z",
    "creator": "did:example:ebfeb1f712ebc6f1c276e12ec21/keys/2",
    "nonce": "d1bf2d9f-d8f8-57a0-c363-97f7b1f8498f",
    "signatureValue": "rSeVAO2CpMoI6AitKyAyZwwHdSh448iimcY5Rp4XWT
    TuJwkWXlBF2iAq/1g/kg82Tb+fZmXJOdqzJe+xOFUCpRLdf2Rwi2pj3hTpvSi
    fFJ0v3ze8YQeH0HeFrlu+Re78XT4Lluo6Hv88BoqGqi3gjD70di+wCwg4329H
    x8idxy8="
  }]
}
    </script>
  </head>
  <body>
    <!-- journalistic content -->
  </body>
</html>
```

### Approach 3: Add `did` to `Person` and Digitally Sign JSON-LD Content using DID Document Keys
```html
<!DOCTYPE html>
<html>
  <head>
    <script type="application/ld+json">
{
  "@context": [
    "http://schema.org",
    "https://w3id.org/identity/v1",
    "https://w3id.org/security/v1"
  ],
  "@type": "ReportageNewsArticle",
  "headline": "Example News Article",
  "description": "An example news article.",
  "url": "https://www.news.com/article.html",
  "image": {
    "@type": "ImageObject",
    "url": "https://www.news.com/img.png",
    "width": "1200",
    "height": "630"
  },
  "author": [{
    "@type": "Person",
    "name": "John Smith",
    "givenName": "John",
    "familyName": "Smith",
    "did": "did:example:ebfeb1f712ebc6f1c276e12ec21"
  }],
  "signature": [{
    "type": "LinkedDataSignature2017",
    "created": "2017-09-29T22:55:50Z",
    "creator": "did:example:ebfeb1f712ebc6f1c276e12ec21/keys/2",
    "nonce": "d1bf2d9f-d8f8-57a0-c363-97f7b1f8498f",
    "signatureValue": "rSeVAO2CpMoI6AitKyAyZwwHdSh448iimcY5Rp4XWT
    TuJwkWXlBF2iAq/1g/kg82Tb+fZmXJOdqzJe+xOFUCpRLdf2Rwi2pj3hTpvSi
    fFJ0v3ze8YQeH0HeFrlu+Re78XT4Lluo6Hv88BoqGqi3gjD70di+wCwg4329H
    x8idxy8="
  }]
}
    </script>
  </head>
  <body>
    <!-- journalistic content -->
  </body>
</html>
```

### Approach 4: Use DID for `@id` on `Person` and Digitally Sign JSON-LD Content using DID Document Keys
```html
<!DOCTYPE html>
<html>
  <head>
    <script type="application/ld+json">
{
  "@context": [
    "http://schema.org",
    "https://w3id.org/identity/v1",
    "https://w3id.org/security/v1"
  ],
  "@type": "ReportageNewsArticle",
  "headline": "Example News Article",
  "description": "An example news article.",
  "url": "https://www.news.com/article.html",
  "image": {
    "@type": "ImageObject",
    "url": "https://www.news.com/img.png",
    "width": "1200",
    "height": "630"
  },
  "author": [{
    "@type": "Person",
    "@id": "did:example:ebfeb1f712ebc6f1c276e12ec21",
    "name": "John Smith",
    "givenName": "John",
    "familyName": "Smith"
  }],
  "signature": [{
    "type": "LinkedDataSignature2017",
    "created": "2017-09-29T22:55:50Z",
    "creator": "did:example:ebfeb1f712ebc6f1c276e12ec21/keys/2",
    "nonce": "d1bf2d9f-d8f8-57a0-c363-97f7b1f8498f",
    "signatureValue": "rSeVAO2CpMoI6AitKyAyZwwHdSh448iimcY5Rp4XWT
    TuJwkWXlBF2iAq/1g/kg82Tb+fZmXJOdqzJe+xOFUCpRLdf2Rwi2pj3hTpvSi
    fFJ0v3ze8YQeH0HeFrlu+Re78XT4Lluo6Hv88BoqGqi3gjD70di+wCwg4329H
    x8idxy8="
  }]
}
    </script>
  </head>
  <body>
    <!-- journalistic content -->
  </body>
</html>
```

## See Also
[Embedding JSON-LD in HTML Documents](https://json-ld.org/spec/latest/json-ld/#embedding-json-ld-in-html-documents)

[Linked Data Signatures](https://w3c-dvcg.github.io/ld-signatures/)
