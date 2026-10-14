# The Bug That Taught Us to Write Tests

When our startup shipped v1.0 of the billing system, we were proud. Three engineers, six weeks, one feature: automatic invoices. We tested it by hand before launch. It worked.

Two weeks later, a customer emailed: "You charged me twice." We found the bug in an hour. A retry loop re-sent the invoice request when the network timed out, and because our server had no idempotency key, the second request created a second invoice. The fix took ten minutes.

But the real problem was not the bug. It was that we had no way to know it would not happen again. We fixed that one case and shipped, hoping. A month later, a similar timeout bug appeared in the refund flow, and we lost a customer.

That week we stopped fixing bugs one by one and started writing an automated test for every bug we fixed. Each test captured the exact scenario, so the retry-and-duplicate problem could never silently return. Within a quarter, production incidents fell by half and, more importantly, our fear of deploying disappeared. We learned that a bug fixed by hand is a bug waiting to be re-learned; a bug fixed with a test is a bug we finally own.
