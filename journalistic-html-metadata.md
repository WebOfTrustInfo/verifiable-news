# Journalistic Metadata

Types envisioned for `news:type` include: `analysis`, `background`, `opinion`, `reportage` and `review`, as per [journalistic schemas](journalistic-schemas.md).

```html
<!DOCTYPE html>
<html>
  <head prefix="og: http://ogp.me/ns# article: http://ogp.me/ns/article# news: http://example.com#">
    <meta name="og:type" content="article" />
    <meta name="news:type" content="reportage" />
    <meta name="article:author" content="John Smith" />
    <meta name="og:title" content="Example News Article" />
    <meta name="og:description" content="An example news article." />
    <meta name="og:url" content="https://www.news.com/article.html" />
    <meta name="og:image" content="https://www.news.com/img.png" />
  </head>
  <body>
    <!-- journalistic content -->
  </body>
</html>  
```

# Verifiable Claims, Schema.org and Embedded JSON-LD
Available at: [Verifiable Claims, Schema.org and Embedded JSON-LD](verifiable-claims-schema-org-and-embedded-json-ld.md)

## See Also
[HTML5 Metadata](https://www.w3.org/TR/html5/document-metadata.html)

[The Open Graph Protocol](http://ogp.me/)

[Facebook Metadata: Article](https://developers.facebook.com/docs/reference/opengraph/object-type/article/)

[Journalistic Schemas](journalistic-schemas.md)

[Markup for News](https://schema.org/docs/news.html)
