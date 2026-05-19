# QA — MVP Golden Path Acceptance Test

A new user should be able to complete this entire path end-to-end in under 10 minutes with no support. If any step requires reaching out to us, we have not shipped MVP yet.

## Setup

- Fresh browser session, no Lighthouse cookies
- Test bank account in Plaid sandbox
- Test card in Stripe test mode

## Path

1. **Land on marketing site.** Click "Get started" in the hero.
2. **Sign up.** Email + password OR Google. Reach the empty-workspace dashboard.
   - ✅ Time check: under 60 seconds from landing.
3. **Connect a bank account.** Click "Connect bank" → Plaid sandbox → complete the flow → return to dashboard.
   - ✅ Bank shows as connected on dashboard.
4. **Create a customer.** Click "+ Customer". Name, email, save.
5. **Create an invoice.** Click "+ Invoice". Select the customer. Add one line item ($100). Set Net 30. Click "Send".
   - ✅ Confirmation toast. Invoice appears in list with status `sent`.
6. **Receive the invoice as the customer.** Open the email in the test inbox. Click the "View and pay" link.
   - ✅ Hosted payment page loads. Branding visible. Amount correct.
7. **Pay the invoice.** Use the Stripe test card. Submit.
   - ✅ Success page shown. Invoice status flips to `paid` in the operator dashboard within 5 seconds.
8. **See reconciliation.** On the dashboard, the deposit shows up matched to the invoice (test mode simulates settlement).
   - ✅ Match is automatic. No operator action required.
9. **Check the hours-saved counter.** The dashboard counter should be visible and non-zero by now (reflecting the workflow we just automated).

## Pass criteria

- Every step completes without error.
- No step requires opening the help docs or contacting support.
- Total elapsed time: under 10 minutes.

## Fail handling

If any step fails or takes longer than expected, file a bug with the step number and a short description. Block MVP launch until all steps pass cleanly three runs in a row.
