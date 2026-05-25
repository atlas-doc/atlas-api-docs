# Create Order

{% include "../../.gitbook/includes/eva-help-hint.md" %}

### Baggage for connecting flights

Atlas may return baggage options per segment.

For connecting flights in the same direction, keep the baggage selection consistent across all connected segments.

If outbound connected segments use different baggage selections, or inbound connected segments use different baggage selections, order creation can fail with `307`.

Outbound and inbound can still use different baggage selections.

{% openapi-operation spec="atlas-api" path="/order.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/16d5f2d8196b3ef49a60acb409c448368fd1ff7b7e7d5d750ed7be17dd37bd3c.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260525%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260525T075245Z&X-Amz-Expires=172800&X-Amz-Signature=0797364758a650e15a41eda11966128cab0b1fcba270d4ffd3e76985356ed315&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
