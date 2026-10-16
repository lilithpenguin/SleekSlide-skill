# Requested hosting and protected sharing

Read only when the user requests remote delivery, shared persistence, or access control. Discussing sharing options does not authorize publishing. Honor the chosen host/audience and follow its workflow; do not create remote projects, repositories, deployments, tunnels, or links for a local deck.

## Persistence and permissions

Hosted editing needs authenticated persistence or the host's publishing workflow. Handle validation, failed saves, revisions/concurrency, and durable assets according to the requested collaboration scope. Browser-local storage is not publication.

Enforce canonical write permissions on the server with separate owner access. Hiding an editor button is not authorization; recipients can still modify their downloaded copies.

## Protected viewing

Authenticate through host/server/edge over HTTPS before sending private HTML, JSON, images, video, and assets. Embedded JavaScript password checks do not protect downloadable content. Keep passwords/credentials out of source; use the host's secret mechanism.

Protect the intended path/subdomain and assets. Check alternate origins/deployments and caches for bypasses where relevant. Verify denied access to content and assets. Use current provider documentation; shared passwords, HTTP authentication, and identity gateways differ. Do not silently substitute email-code login for a requested shared password.

If host details block implementation, finish independent source work and ask for them. Claim a protected URL only after deployment and verification. Handoff should state who can view/edit, how updates publish, and concrete limitations.
