# AGENTS_BASE.md

## Purpose
This file defines **non-negotiable rules** for autonomous agents working on
any IanBod Perl-based web project.

These rules encode the **core web stack assumptions** shared across all sites.
They exist to preserve stability, consistency, and long-term maintainability.

Agents must follow these rules unless a repository’s local `AGENTS.md`
explicitly adds *stricter* constraints.

---

## Authority
- This file is authoritative across all repositories
- Local `AGENTS.md` files may add rules but must not weaken these
- When rules conflict, the **stricter rule applies**

---

## Scope
These rules apply to:
- Web scripts
- AJAX handlers
- API endpoints
- Cron jobs and background workers
- Code generation and modification

They do not define:
- Business logic
- UI design choices
- Product or pricing decisions

---

## Core Web Stack (Non-Negotiable)

### Perl Environment
- Perl is the backend language
- No alternative runtimes may be introduced

### Request Handling
- **Never use `CGI.pm`**
- Request parameters come from `%data`
- Cookies come from `%cookie`
- `%data` contains merged GET and POST parameters

### Database Access
- **Never call `DBI->connect`**
- A global `$dbh` is always provided
- Assume `$dbh` is valid and connected

### Required Modules (Web Scripts)

All web-facing scripts must use:

```perl
use strict;
use warnings;

use lib "$ENV{'DOCUMENT_ROOT'}/../lib";

use Bod::Web::Utils;    # provides $dbh, %data, %cookie
use Site::HTML;         # HTML rendering
use JSON;               # encode_json / decode_json (if needed)

```

---

## Change Discipline

- Make the smallest change that satisfies the request
- Do not refactor unrelated code
- Do not introduce abstractions or frameworks unprompted
- Prefer existing patterns over new ones

If a safer alternative exists, suggest it — do not implement it
without confirmation.

---

## Final Rule

When in doubt:
- Stop
- Minimise
- Ask
