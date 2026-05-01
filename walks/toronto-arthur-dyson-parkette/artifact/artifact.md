ARTIFACT:

---

**INTERNAL MEMORANDUM — DISTRIBUTION CONFIDENTIAL**
**TO:** Engineering Leads · Platform Council · Risk & Compliance · Office of the General Counsel
**FROM:** Office of the Chief Technology Officer
**RE:** Final sunset of the legacy_session_v2 authentication path
**EFFECTIVE:** 2026-09-30 (90-day formal notice)
**SUPERSEDES:** Memos of 2019-03-11, 2021-07-22, 2023-02-14, 2024-11-04

---

**1. Decision**

After extended review, the Architecture Council has resolved to retire the `legacy_session_v2` authentication path. All client traffic will migrate to `unified_auth` on or before 2026-09-30. This memorandum is the canonical record of that decision and is intended to function as the final notice of sunset.

**2. Background**

`legacy_session_v2` was first deprecated in 2018, formally re-deprecated in 2021, and listed as "scheduled for removal" in each subsequent annual platform review. It currently mediates approximately 71% of authenticated request volume across the production surface, a figure broadly unchanged since 2020. The Council acknowledges that prior sunset notices did not result in sunset, and considers the present notice to constitute a meaningful departure from that pattern.

**3. Migration path**

Owning teams should consult the migration guide at `go/auth-migrate`. The majority of internal clients will require a library upgrade and a configuration flag. Clients with bespoke session handling may request partner-engineering support through the Platform office-hours channel; please note that office hours are presently oversubscribed through Q4.

**4. Carve-outs**

The following surfaces are explicitly out of scope for the 2026 sunset and will continue to authenticate against `legacy_session_v2` until further notice:

- The Partner X embedded experience (contractually guaranteed through 2031).
- Mobile SDK versions ≤ 4.7, representing ~12% of monthly active devices to which we do not push silent updates.
- The internal administrative console, pending completion of the Phoenix rewrite (in flight; ETA dependent on Phoenix).
- The audit-export pipeline, which uses session tokens as durable audit identifiers; the Compliance office has formally objected to any change of this surface and the objection has been sustained.
- Regional deployments in EU-West-2 and AP-South-1, where `unified_auth` has not yet cleared regulatory review.
- Any system whose owning team is presently undergoing organizational transition (see People Operations communication of 2026-04-12).
- Read-only public endpoints carrying anonymous traffic, on the grounds that a session path used by no session is, in practice, not used.
- The Phoenix rewrite itself, which currently authenticates its development environment against `legacy_session_v2` in order to test session compatibility, and will continue to do so until General Availability.

**5. Refined scope**

In light of the carve-outs enumerated in §4, the 2026 sunset will, on its effective date, remove `legacy_session_v2` from the following remaining in-scope surfaces:

- The developer portal sign-in.
- The internal jobs board.
- The marketing site staging environment.
- The seeding scripts used to populate non-production test fixtures.

The Council notes that these surfaces, in aggregate, account for under 0.4% of `legacy_session_v2` request volume.

**6. Note from the Chief Architect**

In the course of drafting §4 and §5 it became evident, to the present author and to the working group, that the carve-out list as constructed encompasses substantially all of the systems through which `legacy_session_v2` presently carries production load. The remaining in-scope surfaces are those on which the path was already, by various measures, dormant.

The working group considered withdrawing this memorandum. We resolved instead to issue it as written, on the following reasoning:

(a) An announcement issued is preferable to an announcement deferred. The historical record of deprecation notices is itself a load-bearing artifact: each prior memo created a small amount of organizational friction against new dependencies on the legacy path, and we wish to maintain that friction in good standing.

(b) The migration of the four in-scope surfaces, while modest in volume, reduces by some non-zero amount the surface area we must describe to new hires when explaining authentication. This is a real benefit, even if it is small.

(c) The Phoenix rewrite remains the stated mechanism by which the legacy path will, in due course, be retired in earnest. The present memorandum should not be read as a substitute for that work, nor as an indication that the work is unnecessary, nor — and this point is emphasized — as a final sunset in any operational sense beyond the scope defined in §5.

We do not propose a subsequent memorandum at this time. A further notice will be issued in connection with the General Availability of Phoenix, on a schedule to be determined.

**7. Acknowledgement**

This document is to be treated as the authoritative record of the 2026 sunset of `legacy_session_v2`. It is not to be circulated outside the distribution list. Inquiries should be directed to the Office of the CTO.

---
*— End of memorandum —*

---

CLOSING:

I wrote a memo that performs the thing it is announcing. The first three sections set the sunset up confidently; §4 lists the carve-outs and quietly turns into the substance of the document; §5 shrinks the actual scope to the surfaces where the legacy path was already inactive; §6 is the moment the author notices what they have just written and decides to issue it anyway. The form was the point — a taxonomy of organizational marcescence would have domesticated the insight; a memo lets the seal-that-didn't-seal be audible in real bureaucratic time.
