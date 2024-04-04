# Spam Patriots: Control and Command Server Protocol
> ## PLEASE note that this shouldn't be used for any malicious purposes and that is not the intent of this protocol! Anything related to that is not related to this repo!

### GET `/getAttackSurface`
Takes in a single URL parameter, `numResults`, which should be a single integer greater then zero. Based on that, the server should return an array of objects which look like the following:
```json
{
  "surfaceId": "d11bcf59-a882-4b90-8d70-533646d0a578", "_comment0": "this should be a uuid v4 unique to each attack surface",
  "surfaceType": "website", "_comment1": "this should currently only be 'website'",
  "surfaceAttackMethod": "POST", "_comment2": "should currently be a HTTP method(in all caps)",
  "surfaceAttackDatatype": "json", "_comment3": "should currently be either 'json' or 'form'",
  "surfaceAttackFormat": { "_comment4": "shows the format of the request that should be sent",
    "card": "random(card)", "_comment5": "IS NOT CODE THAT SHOULD BE RAN! this should currently be either a static value or one of the random function documented in appendix 1, also all backslashes should be replace with two of them and all (literal backslash)( s should be replaced with a (",
  },
  "surfaceAttackLocation": "https://doesnt.exist.ha", "_comment6": "should be a valid URL under the 'website' surfaceType"
}
```

### POST `/newAttackSurface`
The POST data should closely mirror the data sent above under `/getAttackSurface`, except without the `surfaceId`. The response from the server should look like:
```json
{
  "ok": true,
  "data": [
    "(insert data objects sent but with surfaceIds)"
  ]
}
```

### PUT `/updateAttackSurface`
Identical to `/newAttackSurface` except with surfaceIds in the sent data.
