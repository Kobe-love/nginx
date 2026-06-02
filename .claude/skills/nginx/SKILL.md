```markdown
# nginx Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns, coding conventions, and common workflows used in the `nginx` repository. The codebase is primarily written in TypeScript (with C source files for core functionality) and focuses on high-performance networking, SSL/TLS integration, upstream server management, and modular extensibility. You will learn how to contribute features, bugfixes, and enhancements following established conventions and workflows.

---

## Coding Conventions

### File Naming

- **Style:** Snake case  
  **Example:**  
  ```
  ngx_http_upstream_round_robin.c
  ngx_event_openssl_cache.c
  ```

### Imports

- **Style:** Relative imports  
  **Example (TypeScript):**
  ```typescript
  import { someFunction } from './utils/some_util';
  ```

### Exports

- **Style:** Named exports  
  **Example (TypeScript):**
  ```typescript
  export function processRequest() { ... }
  export const DEFAULT_TIMEOUT = 5000;
  ```

### Commit Messages

- **Prefixes:** Commonly start with subsystem (e.g., `ssl`, `quic`, `upstream`, `configure`, `core`, `mp4`)
- **Style:** Freeform, average length ~44 characters  
  **Example:**  
  ```
  ssl: improve session ticket key rotation
  upstream: fix DNS SRV record parsing
  mp4: handle stsc atom edge case
  ```

---

## Workflows

### SSL Feature or Refactor

**Trigger:** When adding, refactoring, or fixing SSL-related features (protocol support, certificate caching, error handling)  
**Command:** `/ssl-feature`

1. Edit or add implementation in `src/event/ngx_event_openssl.c`
2. Edit or add headers in `src/event/ngx_event_openssl.h`
3. If related to caching, edit or add `src/event/ngx_event_openssl_cache.c`
4. Edit SSL-related modules as needed:
   - `src/http/modules/ngx_http_ssl_module.c`
   - `src/mail/ngx_mail_ssl_module.c`
   - `src/stream/ngx_stream_ssl_module.c`

**Example:**
```c
// src/event/ngx_event_openssl.c
int ngx_ssl_new_feature(...) {
    // Implementation of new SSL feature
}
```

---

### Release Version Bump

**Trigger:** When releasing a new version of nginx  
**Command:** `/release`

1. Update release notes in `docs/xml/nginx/changes.xml`
2. Bump version number in `src/core/nginx.h`

**Example:**
```xml
<!-- docs/xml/nginx/changes.xml -->
<change>
  <version>1.23.0</version>
  <description>Added QUIC support.</description>
</change>
```
```c
// src/core/nginx.h
#define NGINX_VERSION      "1.23.0"
```

---

### Upstream Module Enhancement

**Trigger:** When adding or improving upstream server handling (DNS, SRV records, config reload)  
**Command:** `/upstream-enhancement`

1. Edit or add code in relevant upstream modules:
   - `src/http/modules/ngx_http_upstream_*.c`
   - `src/http/ngx_http_upstream*.c/h`
   - `src/stream/ngx_stream_upstream*.c/h`
2. Update zone modules if needed:
   - `ngx_http_upstream_zone_module.c`
   - `ngx_stream_upstream_zone_module.c`

**Example:**
```c
// src/http/ngx_http_upstream.c
void ngx_http_upstream_add_srv_support(...) {
    // Implementation for SRV record support
}
```

---

### MP4 Module Bugfix

**Trigger:** When fixing a bug in MP4 chunk/atom handling  
**Command:** `/mp4-fix`

1. Edit `src/http/modules/ngx_http_mp4_module.c` to address the bug or edge case

**Example:**
```c
// src/http/modules/ngx_http_mp4_module.c
if (stsc_atom->entry_count == 0) {
    // Handle edge case
}
```

---

### Add or Update GitHub Templates or Workflows

**Trigger:** When adding or updating GitHub issue templates, PR templates, or CI workflows  
**Command:** `/github-template`

1. Add or edit files in `.github/ISSUE_TEMPLATE/`
2. Add or edit `.github/pull_request_template.md`
3. Add or edit `.github/workflows/*.yml`

**Example:**
```yaml
# .github/workflows/buildbot.yml
name: Build and Test
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm install
      - run: npm test
```

---

### Security Policy Update

**Trigger:** When updating the project's security policy  
**Command:** `/security-policy`

1. Edit `SECURITY.md` with new or clarified policy details

**Example:**
```markdown
# SECURITY.md
Please report vulnerabilities to security@nginx.org.
```

---

## Testing Patterns

- **Framework:** Unknown (not detected)
- **File Pattern:** `*.test.*`
- **Style:** Test files are named with `.test.` in the filename, typically colocated with the code under test.

**Example:**
```
src/http/modules/ngx_http_mp4_module.test.ts
```

---

## Commands

| Command           | Purpose                                                        |
|-------------------|----------------------------------------------------------------|
| /ssl-feature      | Start an SSL-related feature, refactor, or bugfix workflow     |
| /release          | Bump version and update changelog for a new release            |
| /upstream-enhancement | Enhance or fix upstream server handling modules            |
| /mp4-fix          | Fix bugs in the MP4 module                                     |
| /github-template  | Add or update GitHub templates or CI workflows                 |
| /security-policy  | Update the project's security policy                           |
```
