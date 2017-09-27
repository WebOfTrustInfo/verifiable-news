# Journalistic Metadata

Here is an idea for how the HTML metadata system and models can be extended to facilitate the use of [decentralized identifiers](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2017/blob/master/topics-and-advance-readings/did-primer.md) (DID's) to indicate authors, editors, contributors and organizations pertinent to HTML journalistic content:

In the following example, the `model` namespace indicates the new ideas alongside Open Graph metadata:
```html
<html>
  <head prefix="og: http://ogp.me/ns# article: http://ogp.me/ns/article# model: http://example.com#">
    <meta name="model:type" content="journalism" />
    <meta name="og:type" content="article" />
    <meta name="model:author" content="did:example:ebfeb1f712ebc6f1c276e12ec21" />
    <meta name="article:author" content="John Smith" />
    <meta name="og:title" content="News Article" />
    <meta name="og:description" content="..." />
    <meta name="og:url" content="https://www.news.com/article.html" />
    <meta name="og:image" content="https://www.news.com/img.png" />
  </head>
  <body>
    ...journalistic content...
  </body>
</html>
```

Metadata models envisioned include types: `journalism` and `opinion`, the latter encompassing newspaper columns, editorials, op-eds, editorial cartoons and punditry.

## See Also
[HTML5 Metadata](https://www.w3.org/TR/html5/document-metadata.html)

[The Open Graph Protocol](http://ogp.me/)

[Facebook Metadata: Article](https://developers.facebook.com/docs/reference/opengraph/object-type/article/)
