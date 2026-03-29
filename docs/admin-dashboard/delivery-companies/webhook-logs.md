# Webhook Logs

## What This Page Does

This page monitors inbound delivery webhooks per company and helps recover failed processing.

Each webhook log stores:

- endpoint, method, headers, payload
- processed flag and timestamp
- linked order (if resolved)
- processing error message (if any)

---

## Processing Flow

1. webhook request is logged (`processed=false`)
2. payload is parsed by company format (Ozone / GLOG / generic)
3. system tries to find delivery order by tracking/reference
4. external status is resolved
5. external status mapping is applied to internal status
6. delivery order + status history + parent order are updated
7. log is marked processed (or keeps error)

---

## Common Failure Reasons

- order not found by tracking/reference
- unknown external status (`STATUS_NOT_FOUND`)
- status exists but no mapping (`MAPPING_NOT_FOUND`)
- payload parsing issue

---

## Retry & Recovery

Admin actions:

- retry one failed webhook
- retry all failed webhooks (last 24h batch)
- cleanup processed old logs

Retry re-runs parsing + status synchronization on saved payload.

---

## Operational Recommendation

- Keep pending logs near zero.
- If errors repeat, check this order:
  1. API settings/credentials
  2. statuses imported
  3. status mappings complete
  4. tracking/reference consistency from provider
