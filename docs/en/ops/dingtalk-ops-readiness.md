# DingTalk Ops Readiness

This guide defines channel-specific operations checks for DingTalk.

## Health Semantics

- Channel health is true only when both running and stream connection are active.
- Expired session webhook targets must be rejected or refreshed before sending.

## Auth and Delivery

1. Validate access token fetch and refresh lifecycle.
2. Verify fallback behavior between session webhook replies and AI interaction APIs.
3. Reject arbitrary webhook targets and unsupported media payloads.

## Incident Steps

1. Check DingTalk app credentials and token acquisition path.
2. Validate websocket stream mode endpoint availability.
3. Confirm reply target cache freshness and expiry handling.
4. Capture provider error payload before restarting workers.

## SLO Signals

- auth_fail_total
- stream_reconnect_total
- outbound_send_fail_total
- healthcheck_fail_total
