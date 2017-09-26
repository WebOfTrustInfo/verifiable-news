Here is an idea for how the HTML metadata system and models can be extended to facilitate the use of [decentralized identifiers](https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2017/blob/master/topics-and-advance-readings/did-primer.md) (DID's) to indicate authors, editors, contributors and organizations pertinent to HTML journalistic content:

```html
<html>
  <head>
    <meta name="model:author" content="did:example:ebfeb1f712ebc6f1c276e12ec21" />
  </head>
  <body>
    …journalistic content…
  </body>
</html>
```
