# Verify

{% include "../../.gitbook/includes/eva-help-hint.md" %}

{% hint style="info" %}
Use a `routingIdentifier` that is no more than 6 hours old.

Use the returned `sessionId` within 2 hours for `order.do`.
{% endhint %}

{% openapi-operation spec="atlas-api" path="/verify.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/16d5f2d8196b3ef49a60acb409c448368fd1ff7b7e7d5d750ed7be17dd37bd3c.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260608%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260608T031649Z&X-Amz-Expires=172800&X-Amz-Signature=ef970ec0d2674d2a9cf9fcb0d3f4d3e5e8516edc1b3d54ee161c5618f70f7404&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
