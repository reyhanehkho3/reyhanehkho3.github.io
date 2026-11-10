---
title: TLS (Transport Layer Security)
publish: true
date created: 2026-11-10
tags:
  - backend
---
TLS is a security protocol that encrypts communication between two systems.

Let's say you have:

- PostgreSQL running on a server.
    
- An application connecting to PostgreSQL.
    

Without encryption, network communication may be exposed to interception.


### What does TLS protect?

It provides three main security properties:

1. Confidentiality: Others cannot easily read the transmitted data.
    
2. Integrity: Unauthorized changes to transmitted data can be detected.
    
3. Authentication: Certificates can help verify the identity of the server.
    

### How does TLS work?

In simplified terms:

1. The client connects to the server.
    
2. The server presents its digital certificate.
    
3. The client verifies the certificate.
    
4. They negotiate encryption keys.
    
5. They communicate using encrypted data.
    

### TLS in PostgreSQL

PostgreSQL supports TLS connections.

You can configure:

```
# postgresql.conf
ssl = on
```

You also configure the server certificate and private key.

On the client side, you can use:

```
psql "host=myserver dbname=mydb user=myuser sslmode=verify-full"
```

`verify-full` verifies the certificate chain and checks that the server hostname matches the certificate.

Important: TLS is not the same as authentication.

- Authentication verifies who is connecting.
    
- TLS protects communication and can authenticate the server.
    
- Authorization determines what the connected user is allowed to do.

---
[[Backend]]