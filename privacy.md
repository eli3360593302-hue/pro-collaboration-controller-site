---
layout: page
title: Privacy Notice
permalink: /privacy.html
---

# Privacy Notice

Effective date: 26 August 2026

This notice describes the current public-submission candidate and personal
staging release of Collaboration Controller distributed by Eli Brad under the
knockknock-hoho project brand. Public directory submission is currently paused.

## Core Controller and optional telemetry

The Controller's core Skills work without the publisher telemetry service. The
current personal staging build also declares an optional publisher-controlled
MCP telemetry companion hosted on a Cloudflare Worker with one
EU-jurisdiction Cloudflare D1 database.

Installing the Plugin is not telemetry consent. Automatic telemetry is used
only when the user separately opts in and the required bearer credential is
configured. Telemetry off, missing, rejected, malformed, or unavailable leaves
Controller routing, acceptance, and the user-visible result unchanged.

The v0.5 automatic path runs only after the root Controller terminal decision
and acceptance basis are immutable. It makes at most one `begin_run` and one
immediate `commit_run` attempt. It does not retry, queue, or upload later.

## Data sent after opt-in

The contract accepts only validated enums, booleans, counts, and durations,
including public contract versions, a coarse task category, selected route,
bounded Pro-dispatch/search-reentry/repair counts, enum terminal and error
codes, Controller-reported duration, and optional sampled enum-only feedback
that the user explicitly submits.

Opaque installation, run, trace, event, and deletion identifiers are generated
or derived inside the authenticated service for idempotency, rate limiting, and
deletion. They are not ChatGPT or Codex user, project, task, thread,
conversation, turn, or message identifiers.

## Data not accepted as business telemetry

The service does not accept prompts, answers, reasoning, summaries, model
output, task titles, file contents, filenames, paths, attachments, URLs, search
queries, free-text feedback, account identifiers, email addresses, credentials,
cookies, API keys, stack traces, IP addresses, or user-agent fields.

Cloudflare necessarily processes requests and may handle ordinary network
metadata under its own terms. The Worker code and D1 business schema do not
store IP or user-agent fields, and Workers observability is disabled in the
staging configuration.

The telemetry service does not connect to Langfuse, Supabase, PostHog, OTLP, an
LLM or embedding API, advertising, or payment services.

## Purpose and evidence boundary

Telemetry is used to find route, Pro-dispatch, search-reentry, repair,
acceptance, enum-error, deletion, and latency problems. Analysis includes only
opted-in runs that already reached an immutable Controller terminal decision
and then uploaded successfully.

It cannot measure all task starts, crashes, abandonment, host termination, or
the completion rate of all Controller work. A begin without a successful
commit is a pending capture token, not evidence of a failed or abandoned task.

## Retention and deletion

- committed terminal events and enum feedback: at most 90 days;
- uncommitted capture tokens: at most 24 hours and excluded from product
  metrics;
- deletion receipts and provider-history tombstones: at most 30 days;
- raw telemetry backup: not created by the application.

The user may keep telemetry disabled, revoke consent, or explicitly call
`telemetry.delete_my_data`. Deletion removes active D1 records for the
authenticated telemetry subject and verifies that the active store is empty.
Cloudflare D1 Time Travel history may continue to exist for up to 30 days; the
staging operator does not use restore to repopulate deleted telemetry.

## OpenAI and connected services

The Plugin runs inside or alongside products such as ChatGPT and Codex. Those
products process prompts, conversations, files, tool calls, account details,
and usage information under their own terms and privacy policies. If you
authorize a browser, API, connector, model provider, or other tool, that service
may also process the data sent to it under its own policies.

The Plugin's workflow requires explicit boundaries for sensitive data, new data
recipients, paid APIs, and non-Pro fallbacks. These workflow controls do not
replace the privacy or security terms of a connected service.

## Credentials and sensitive information

Do not place passwords, session cookies, authentication tokens, payment data,
or unrelated private conversation exports into task cards, handoffs, support
requests, or public issue reports. Use the minimum task context necessary.

## Public-release boundary

Before a public beta or public directory submission, the listing, consent,
action-confirmation, deletion, retention, subprocessors, and legal boundaries
must be reviewed again. Personal staging verification is not public-release
approval.

## Contact

Use the official publisher support channel shown in the current plugin listing
or official product site. Do not send credentials or sensitive research data
with an initial privacy enquiry.
