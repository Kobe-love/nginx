---
name: upstream-module-enhancement
description: Workflow command scaffold for upstream-module-enhancement in nginx.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /upstream-module-enhancement

Use this workflow when working on **upstream-module-enhancement** in `nginx`.

## Goal

Implements new features, bugfixes, or enhancements to upstream modules, often related to DNS resolution, peer management, or configuration reloads.

## Common Files

- `src/http/modules/ngx_http_upstream_hash_module.c`
- `src/http/modules/ngx_http_upstream_ip_hash_module.c`
- `src/http/modules/ngx_http_upstream_least_conn_module.c`
- `src/http/modules/ngx_http_upstream_random_module.c`
- `src/http/modules/ngx_http_upstream_zone_module.c`
- `src/http/ngx_http_upstream.c`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add code in src/http/modules/ngx_http_upstream_*.c and src/http/ngx_http_upstream*.c/h
- Edit or add code in src/stream/ngx_stream_upstream*.c/h and related modules
- Update zone modules if needed (e.g., ngx_http_upstream_zone_module.c, ngx_stream_upstream_zone_module.c)

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.