> Source: 02-narrative-en.md | 5 cards

## Card 1: Root cause of the double charge

- **Key point**: A retry loop re-sent the invoice request after a network timeout, and with no idempotency key the second request created a second invoice.
- **Explanation**: The bug was found in an hour and fixed in ten minutes; the technical cause was duplicated invoice creation triggered by retries.
- **Self-check**: Why did a network timeout lead to a customer being charged twice?

---

## Card 2: A hand-fixed bug is not really fixed

- **Key point**: Fixing a bug by hand leaves no way to know it will not happen again.
- **Explanation**: After fixing only the specific case, a similar timeout bug later appeared in the refund flow and cost the team a customer.
- **Self-check**: Why was the second timeout bug in the refund flow possible despite the first fix?

---

## Card 3: Write a test for every bug you fix

- **Key point**: For every bug fixed, write an automated test that captures the exact scenario.
- **Explanation**: This prevented the retry-and-duplicate problem from silently returning and became the team's new practice.
- **Example**: Turn the "retry loops create a second invoice" scenario into an automated test so it can never regress unnoticed.

---

## Card 4: Tests removed the fear of deploying

- **Key point**: Within a quarter, production incidents fell by half and the team's fear of deploying disappeared.
- **Explanation**: The measurable win was fewer incidents; the cultural win was that releasing no longer felt risky.
- **Self-check**: Which outcome mattered more to the team than the drop in incidents, and why?

---

## Card 5: The lesson

- **Key point**: A bug fixed by hand is a bug waiting to be re-learned; a bug fixed with a test is a bug you finally own.
- **Explanation**: The durable unit of fixing is not the change itself but the test that locks the behavior in.
- **Self-check**: Restate the team's lesson in your own words.
