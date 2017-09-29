# Journalistic Metadata

In the following example, the `model` namespace indicates some new ideas alongside Open Graph metadata:
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

Due to the modular and extensible manner in which CMS plugins generate `<meta>` and `<link>` metadata elements, digitally signing across multiple `<meta>` and `<link>` metadata elements is complex. It could be that a plugin outputs embedded, digitally-signed JSON-LD content.

For example:
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
      "@context": "http://schema.org",
      "@type": "ReportageNewsArticle",
      "headline": "Example News Article",
      "description": "An example news article.",
      "url": "https://www.news.com/article.html",
      "image": {
        "@type": "ImageObject",
        "url": "https://www.news.com/img.png",
        "height": "400",
        "width": "300"
      },
      "author": {
        "@type": "Person",
        "givenName": "John",
        "familyName": "Smith",
        "did": "did:example:ebfeb1f712ebc6f1c276e12ec21"
      },
      "signature": {
        "type": "LinkedDataSignature2017",
        "created": "2017-06-18T21:19:10Z",
        "creator": "...",
        "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
        "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
        VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
        GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
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

[Embedding JSON-LD in HTML Documents](https://json-ld.org/spec/latest/json-ld/#embedding-json-ld-in-html-documents)
