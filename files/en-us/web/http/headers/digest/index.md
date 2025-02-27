---
title: Digest
slug: Web/HTTP/Headers/Digest
tags:
  - HTTP
  - HTTP Header
  - Digest
  - Authentication
browser-compat: http.headers.Digest
---
{{HTTPSidebar}}

The **`Digest`** response HTTP header provides a {{Glossary("digest")}} of the _selected representation_ of the requested resource.

Representations are different "versions" of a particular resource that might be returned from a request: for example, the same data resource might formatted in a particular media type such as XML or JSON, localised to a particular written language or geographical region, and/or compressed or otherwise encoded for transmission.
The representation can be determined from the response's {{Glossary("Representation header","Representation headers")}}.

The digest applies to the whole representation of a resource, not to a particular message.
It can be used to verify that the representation has not been modified during transmission.

> **Note:** While a representation may be fully contained in the message body of a single response, it can also be sent using multiple messages in response to a [range request](/en-US/docs/Web/HTTP/Range_requests), or omitted altogether in response to a {{HTTPMethod("HEAD")}} request.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Header type</th>
      <td>{{Glossary("Response header")}}</td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Forbidden header name")}}</th>
      <td>no</td>
    </tr>
  </tbody>
</table>


## Syntax

```
Digest: <digest-algorithm>=<digest-value>
Digest: <digest-algorithm>=<digest-value>,<digest-algorithm>=<digest-value>
```

## Directives

- `<digest-algorithm>`
  - : Digest algorithms are defined in [Digest Headers](https://datatracker.ietf.org/doc/draft-ietf-httpbis-digest-headers/). 
    - Permitted digest algorithms values include: `unixsum`, `unixcksum`, `crc32c`, `sha-256` and `sha-512`, `id-sha-256`, `id-sha-512`
    - Deprecated algorithms values include: `md5`, `sha`, `adler32`.
- `<digest-value>`
  - : The result of applying the digest algorithm to the resource representation and encoding the result.
    The choice of digest algorithm also determines the encoding to use: for example `SHA-256` uses base64 encoding.

## Examples

```http
Digest: sha-256=X48E9qOokqqrvdts8nOJRJN3OWDUoyWxBf7kbu9DBPE=
Digest: sha-256=X48E9qOokqqrvdts8nOJRJN3OWDUoyWxBf7kbu9DBPE=,unixsum=30637
```

## Specifications

{{Specifications("http.headers.Digest")}}

## Browser compatibility

{{Compat}}

## See also

- {{HTTPHeader("Want-Digest")}}

- [HTTP range requests](/en-US/docs/Web/HTTP/Range_requests)
- [`206 Partial Content`](/en-US/docs/Web/HTTP/Status/206 "The HTTP 206 Partial Content success status response code indicates that the request has succeeded and has the body contains the requested ranges of data, as described in the Range header of the request.")
