# Sketchpad

## Text-based Claims
Here is a sketch of a text-based claim:
```json
{
  "claim": {
    "value": "Lorem ipsum dolor sit amet."
   }
}
```
Here is another:
```json
{
  "claim": [{
    "value": "Lorem ipsum dolor sit amet.",
    "lang": "en"
   },
   {
    "value": "Consectetur adipiscing elit.",
    "lang": "fr"
   }]
}
```
Here is a third sketch:
```json
{
  "claim": {
    "value": "The area of a circle with radius <math><mi>r</mi></math> is <math><mi>&pi;</mi><mo>&InvisibleTimes;</mo><msup><mi>r</mi><mn>2</mn></msup></math>.",
    "lang": "en",
    "datatype": "http://www.w3.org/1999/02/22-rdf-syntax-ns#HTML"
  }
}
```

## HTTP-based Revocation
The idea here is that a URL can be provided which returns HTTP status code [`404`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) or [`410`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11) if the claim is revoked and HTTP status code [`200`](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) if the claim is not revoked.

[https://w3c.github.io/vc-data-model/#revocation](https://w3c.github.io/vc-data-model/#revocation)

Here is a sketch of HTTP-based revocation:
```json
{
  "revocation": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1",
    "type": "HTTPBasedRevocation"
  }
}
```
and in the context of an example:
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1",
  "type": "Claim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "value": "Lorem ipsum dolor sit amet."
  },
  "revocation": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1",
    "type": "HTTPBasedRevocation"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCR
    VpjOboDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+g
    GsutPTLzvueMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
## Discussion
### What about interrelating claims, e.g. argumentation?
[https://w3c.github.io/vc-data-model/#evidence](https://w3c.github.io/vc-data-model/#evidence)
