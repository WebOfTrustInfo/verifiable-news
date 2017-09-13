# Sketchpad

## Verifiable Text-based Claims
Here is a sketch of a verifiable text-based claim:
```json
{
  "claim": {
    "text": "Lorem ipsum dolor sit amet."
   }
}
```
in the context of a wider example:
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21",
  "type": "TextClaim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": {
    "text": "Lorem ipsum dolor sit amet."
   },
  "revocation": {
    "id": "https://www.journalistblog.com/users/1/revocations/",
    "type": "SimpleRevocationList2017"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCRVpjOb
    oDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+gGsutPTLzvu
    eMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
Here is another sketch of a verifiable text-based claim:
```json
{
  "claim": "Lorem ipsum dolor sit amet."
}
```
in the context of a wider example:
```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21",
  "type": "TextClaim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": "Lorem ipsum dolor sit amet.",
  "revocation": {
    "id": "https://www.journalistblog.com/users/1/revocations/",
    "type": "SimpleRevocationList2017"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCRVpjOb
    oDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+gGsutPTLzvu
    eMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```

## HTTP-based Revocation Scheme
The idea here is that a URL can be provided which returns HTTP status code `404` or `410` if the claim is revoked and HTTP status code `200` if the claim is not revoked.

[https://w3c.github.io/vc-data-model/#revocation](https://w3c.github.io/vc-data-model/#revocation)

```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21",
  "type": "TextClaim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": "Lorem ipsum dolor sit amet.",
  "revocation": {
    "id": "https://www.journalistblog.com/users/1/revocations/?id=ebfeb1f712ebc6f1c276e12ec21",
    "type": "HTTPBasedRevocation"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCRVpjOb
    oDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+gGsutPTLzvu
    eMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```

```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21",
  "type": "TextClaim",
  "issuer": "https://www.journalistblog.com/users/1/issuer/",
  "issued": "2017-06-18T21:19:10Z",
  "claim": "Lorem ipsum dolor sit amet.",
  "revocation": {
    "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21",
    "type": "HTTPBasedRevocation"
  },
  "signature": {
    "type": "LinkedDataSignature2017",
    "created": "2017-06-18T21:19:10Z",
    "creator": "https://www.journalistblog.com/users/1/keys/",
    "nonce": "c0ae1c8e-c7e7-469f-b252-86e6a0e7387e",
    "signatureValue": "BavEll0/I1zpYw8XNi1bgVg/sCneO4Jugez8RwDg/+MCRVpjOb
    oDoe4SxxKjkCOvKiCHGDvc4krqi6Z1n0UfqzxGfmatCuFibcC1wpsPRdW+gGsutPTLzvu
    eMWmFhwYmfIFpbBu95t501+rSLHIEuujM/+PXr9Cky6Ed+W3JT24="
  }
}
```
