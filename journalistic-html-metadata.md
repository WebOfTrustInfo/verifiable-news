# Journalistic Metadata

In the following example, the `model` namespace indicates some ideas alongside Open Graph metadata:
```html
<html>
  <head prefix="og: http://ogp.me/ns# article: http://ogp.me/ns/article# model: http://example.com#">
    <meta name="og:type" content="article" />
    <meta name="model:type" content="reportage" />
    <meta name="article:author" content="John Smith" />
    <meta name="model:author" content="did:example:ebfeb1f712ebc6f1c276e12ec21" />
    <meta name="og:title" content="Example News Article" />
    <meta name="og:description" content="An example news article." />
    <meta name="og:url" content="https://www.news.com/article.html" />
    <meta name="og:image" content="https://www.news.com/img.png" />
    <meta name="model:signature" content="..." />
  </head>
  <body>
    ...journalistic content...
  </body>
</html>
```

Types envisioned for `model:type` include: `analysis`, `background`, `opinion`, `reportage` and `review`, as per [journalistic schemas](journalistic-schemas.md).

Due to the extensible nature of HTML metadata and due to the modular manner in which multiple CMS plugins generate `<meta>` and `<link>` metadata elements, digitally signing across multiple `<meta>` and `<link>` metadata elements is complex.

A plugin could, however, easily output digitally-signed, embedded JSON-LD content. For example:

**Hypothesis 1: Add `profile` Field to `Person`**
```html
<html>
  <head prefix="og: http://ogp.me/ns# article: http://ogp.me/ns/article# model: http://example.com#">
    <meta name="og:type" content="article" />
    <meta name="model:type" content="reportage" />
    <meta name="article:author" content="John Smith" />
    <meta name="model:author" content="did:example:ebfeb1f712ebc6f1c276e12ec21" />
    <meta name="og:title" content="Example News Article" />
    <meta name="og:description" content="An example news article." />
    <meta name="og:url" content="https://www.news.com/article.html" />
    <meta name="og:image" content="https://www.news.com/img.png" />
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
      "author": {
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
              "familyName": "Smith",
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
      }
    }
    </script>
  </head>
  <body>
    ...journalistic content...
  </body>
</html>
```

## See Also
[HTML5 Metadata](https://www.w3.org/TR/html5/document-metadata.html)

[The Open Graph Protocol](http://ogp.me/)

[Facebook Metadata: Article](https://developers.facebook.com/docs/reference/opengraph/object-type/article/)

[Journalistic Schemas](journalistic-schemas.md)

[Markup for News](https://schema.org/docs/news.html)

[Embedding JSON-LD in HTML Documents](https://json-ld.org/spec/latest/json-ld/#embedding-json-ld-in-html-documents)

[Linked Data Signatures](https://w3c-dvcg.github.io/ld-signatures/)
