---
name: ssl-feature-or-refactor
description: Workflow command scaffold for ssl-feature-or-refactor in nginx.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /ssl-feature-or-refactor

Use this workflow when working on **ssl-feature-or-refactor** in `nginx`.

## Goal

Implements new SSL features, refactors, or fixes in the SSL/OpenSSL integration layer, often involving changes to object caching, certificate handling, or protocol support.

## Common Files

- `src/event/ngx_event_openssl.c`
- `src/event/ngx_event_openssl.h`
- `src/event/ngx_event_openssl_cache.c`
- `src/http/modules/ngx_http_ssl_module.c`
- `src/mail/ngx_mail_ssl_module.c`
- `src/stream/ngx_stream_ssl_module.c`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add implementation in src/event/ngx_event_openssl.c
- Edit or add headers in src/event/ngx_event_openssl.h
- Edit or add implementation in src/event/ngx_event_openssl_cache.c (if related to caching)
- Edit SSL-related modules in src/http/modules/ngx_http_ssl_module.c, src/mail/ngx_mail_ssl_module.c, or src/stream/ngx_stream_ssl_module.c as needed

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.