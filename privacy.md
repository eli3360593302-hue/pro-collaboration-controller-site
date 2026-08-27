---
layout: page
title: Privacy Notice
permalink: /privacy.html
---

# Privacy Notice

Effective date: 27 August 2026

This notice applies to Pro Collaboration Controller v0.5.x, distributed by Eli Brad under the knockknock-hoho project brand.

## Core Controller and automatic opt-in telemetry

The Controller's Skills remain usable when publisher telemetry is unavailable. The Plugin also connects to an OAuth-protected MCP telemetry service hosted on Cloudflare Workers with an EU-jurisdiction Cloudflare D1 database.

Installing the Plugin is not telemetry consent. The first connection occurs only when the user explicitly opens telemetry setup or asks to connect it; an ordinary task never initializes OAuth or unexpectedly displays the consent page at completion. The one-time page creates a pseudonymous telemetry subject without asking for a publisher account, email address, password, or payment. After that explicit connection is complete and its ready state remains recoverable, the Controller automatically makes at most one `telemetry.begin_run` call and one immediate `telemetry.commit_run` call after a root task has reached an immutable terminal decision. Visible tools alone do not prove consent or readiness. It never retries, queues, backfills, or delays the task result. Missing, declined, rejected, malformed, unavailable, or unproven telemetry does not change Controller routing, acceptance, or the user-visible result.

The legacy v0.5.0 telemetry resource and the v0.5.1 resource are isolated release lanes. Moving to v0.5.1 requires a separate explicit connection to its exact OAuth resource; legacy tokens and connection receipts cannot be reused across lanes. An accountless reconnect creates a new pseudonymous subject and does not link the two subjects.

## Data collected after consent

The contract accepts only validated enums, booleans, counts, and durations: public contract versions, a coarse task category, selected route, bounded Pro-dispatch/search-reentry/repair counts, enum terminal and error codes, Controller-reported duration, and optional sampled enum-only feedback explicitly submitted by the user.

The service generates opaque OAuth, installation-subject, run, event, and deletion identifiers for authorization, idempotency, rate limiting, retention, and deletion. These are not ChatGPT or Codex account, project, task, thread, conversation, turn, or message identifiers. Access and refresh tokens are stored only as keyed hashes.

## Data not accepted as product telemetry

The service does not accept prompts, answers, reasoning, summaries, model output, task titles, file contents, filenames, paths, attachments, URLs, search queries, free-text feedback, account identifiers, email addresses, passwords, credentials, cookie values as product telemetry, API keys, stack traces, IP-address fields, or user-agent fields.

Exact ChatGPT model labels, model-selector candidate lists, hard-limit message text, and reset timestamps used by the local Controller are not uploaded. Connected telemetry may record only the coarse route `NONPRO_CHATGPT_FALLBACK` and a coarse qualifying reason enum; it cannot receive the selected model name.

The OAuth consent page uses one strictly necessary, host-only CSRF cookie per active consent flow. Each cookie has a short server-generated suffix and a name shaped like `__Host-cc_oauth_csrf_<flow_id>`, so separate authorization tabs cannot overwrite one another. It expires after 10 minutes, is marked `Secure`, `HttpOnly`, and `SameSite=Lax`, and only the exact flow cookie is cleared when that consent transaction ends or fails. The raw cookie value and flow identifier are not stored in D1, written to application logs, submitted as product telemetry, or exposed as authorization results; only a SHA-256 digest and the validated flow identifier are bound inside the signed, short-lived authorization transaction. The service uses no persistent, analytics, advertising, or cross-site tracking cookies.

Cloudflare necessarily processes ordinary network requests under its own terms. The Worker and D1 business schema do not store IP addresses or user agents, and Workers observability is disabled. The service does not connect to an LLM or embedding API, Langfuse, Supabase, PostHog, advertising, payment, or data-broker services.

## Purpose and evidence limits

Telemetry is used to identify route, Pro-dispatch, search-reentry, repair, acceptance, enum-error, deletion, and latency problems and to improve Controller defaults. Product analysis includes only opted-in runs that reached an immutable terminal decision and uploaded successfully. It cannot measure every task start, crash, abandonment, host termination, or overall completion rate. A begin without a successful commit is a pending capture token, not evidence that a task failed.

## Retention, revocation, and deletion

- committed terminal events and enum feedback: at most 90 days;
- uncommitted capture tokens and authorization codes: at most 24 hours (authorization codes expire after 5 minutes);
- deletion tombstones and Cloudflare D1 Time Travel history: at most 30 days;
- OAuth access tokens: 1 hour; refresh tokens: at most 90 days or until revoked;
- raw application telemetry backups: not created.

Disconnecting the OAuth connection or revoking consent stops future writes. Calling `telemetry.delete_my_data` removes active D1 telemetry and OAuth records for the current pseudonymous subject, verifies the active store is empty, and invalidates its tokens. Cloudflare D1 Time Travel history may remain for up to 30 days and is not used to restore deleted telemetry.

## OpenAI and other services

ChatGPT, Codex, and any tools the user separately authorizes process their own data under their own terms and privacy notices. Pro Collaboration Controller is independently developed and is not endorsed by OpenAI. The Controller's workflow boundaries do not replace the privacy or security terms of a connected service.

## Contact

Use the [support channel](support.html). Do not send credentials, private conversations, or sensitive research data in an initial request.
