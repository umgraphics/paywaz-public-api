# Paywaz Webhooks — Best Practices

## Verify signatures using raw body
Do not parse JSON before verification. Verify against `${timestamp}.${raw_body}`.

Headers:
- `Paywaz-Timestamp: <unix_seconds>`
- `Paywaz-Signature: v1=<hex>`

## Replay protection
Reject events where `|now - timestamp| > 300 seconds` (or your configured tolerance).

## Acknowledge fast, process async
Return `200` immediately after verification and queue work (or process in background).

## Idempotency
Webhook deliveries may be retried. Store processed `event.id` for 24–72 hours and ignore duplicates.

Recommended: Redis `SET NX EX`.

## Secret rotation
Support multiple secrets (current + previous). Verify signature against each in order.

## Observability
Log:
- event id
- type
- version (eventVersion)
- verification outcome
- processing outcome
