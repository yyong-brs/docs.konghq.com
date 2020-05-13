---
title: kong.client.tls
pdk: true
toc: true
---

## kong.client.tls

The client.tls module provides functions for interacting with TLS
 connections from client.



### kong.client.tls.request_client_certificate()

Requests client to present its client-side certificate to initiate mutual
 TLS authentication between server and client.

 This function only *requests*, but does not *require* the client to start
 the mTLS process. Even if the client did not present a client certificate
 the TLS handshake will still complete (obviously not being mTLS in that
 case). Whether the client honored the request can be determined using
 get_full_client_certificate_chain in later phases.


**Phases**

* certificate

**Returns**

1.  `true|nil` true if request was received, nil if request failed

1.  `nil|err` nil if success, or error message if failure


**Usage**

``` lua
local res, err = kong.client.tls.request_client_certificate()
if not res then
  -- do something with err
end
```

[Back to TOC](#table-of-contents)


### kong.client.tls.disable_session_reuse()

Prevents the TLS session for the current connection from being reused
 by disabling session ticket and session ID for the current TLS connection.

**Phases**

* certificate

**Returns**

1.  `true|nil` true if success, nil if failed

1.  `nil|err` nil if success, or error message if failure


**Usage**

``` lua
local res, err = kong.client.tls.disable_session_reuse()
if not res then
  -- do something with err
end
```

[Back to TOC](#table-of-contents)


### kong.client.tls.get_full_client_certificate_chain()

Returns the PEM encoded downstream client certificate chain with the
 client certificate at the top and intermediate certificates
 (if any) at the bottom.

**Phases**

* rewrite, access, balancer, header_filter, body_filter, log

**Returns**

1.  `string|nil`  PEM-encoded client certificate if mTLS handshake
 was completed, nil if an error occurred or client did not present
 its certificate

1.  `nil|err` nil if success, or error message if failure


**Usage**

``` lua
local cert, err = kong.client.get_full_client_certificate_chain()
if err then
  -- do something with err
end

if not cert then
  -- client did not complete mTLS
end

-- do something with cert
```

[Back to TOC](#table-of-contents)

