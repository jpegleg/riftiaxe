# riftiaxe 

![riftia](https://upload.wikimedia.org/wikipedia/commons/f/f6/Riftia_tube_worm_colony_Galapagos_2011.jpg)

A MIO rusTLS termination proxy that uses aws-lc-rs (AWS Cryptography) as a rusTLS cryptography provider.

Features:
- logging with UTC timestamps
- UUIDv4 stateful logging
- aws-lc-rs cryptography
- configurable rusTLS settings

The usage of aws-lc-rs makes the compile targets limited! Musl libc targets do not succeed with aws-lc-rs.

Possible techniques (with code adjustements for special cases):
- unstable PQC via aws-lc-rs
- FIPS via aws-lc-rs

Note that the logging is intentionally verbose, with entries for every connection, detailing how many bytes are sent, when the connection was closed, how many connections have been observed, and more.

## TLS termination is bad...

TLS termination weakens TLS. If termination can be avoided in a given situation, avoid it. But there are times there are reasons to do TLS termination for meeting different requirements. 

I would much prefer the rusTLS TLS style in https://github.com/jpegleg/ichorsurf if possible, but the reality is we can't always be ichorsurfing. 
When we have to work on FIPS or special compliance requirements, riftiaxe is a tool for helping accomplish those cryptographic needs.

## The good and ugly

Riftiaxe does allow optionally enabling rusTLS mTLS with process args, however the rustTLS mTLS is still either too picky or too open and not really usable IMO.

There is hybrid PQC available in aws-lc-rs, however is pre-standardization and "unstable" software.

The aws-lc-rs library does help rustls improve performance, but limits the compilation targets.

#### Riftiaxe?

The name was inspired by deep ocean worms:

https://en.wikipedia.org/wiki/Riftia 
