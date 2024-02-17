# riftiaxe

A MIO rusTLS termination proxy that uses aws-lc-rs (AWS Cryptography) as a rusTLS provider.

Features:
- logging with UTC timestamps
- UUIDv4 stateful logging
- aws-lc-rs cryptography
- configurable rusTLS settings

The usage of aws-lc-rs makes the compile targets limited! Musl libc targets do not succeed with aws-lc-rs.

