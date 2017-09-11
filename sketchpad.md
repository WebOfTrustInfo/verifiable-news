# Sketchpad

## Verifiable Text-based Claims
Here is a sketch of a verifiable text-based claim:

```json
{
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21",
  "type": "FactualTextClaim",
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
  "id": "https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21",
  "type": "FactualTextClaim",
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
