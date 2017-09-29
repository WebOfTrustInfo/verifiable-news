# Journalistic Metadata

Here is an idea for how the HTML metadata system and models can be extended to facilitate the use of [decentralized identifiers](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2017/blob/master/topics-and-advance-readings/did-primer.md) (DID's) to indicate authors, editors, contributors and organizations pertinent to HTML journalistic content:

In the following example, the `model` namespace indicates the new ideas alongside Open Graph metadata:
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

Types envisioned for `model:type` include: `analysis`, `background`, `opinion`, `reportage` and `review`.

Digitally signing HTML metadata across elements is difficult due to the modular and extensible manner in which CMS plugins generate `<meta>` and `<link>` metadata elements.

It could be that one plugin outputs an embedded JSON-LD section in a `<script>` element with a digitally-signed object.

```html
<html>
  <head>
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
