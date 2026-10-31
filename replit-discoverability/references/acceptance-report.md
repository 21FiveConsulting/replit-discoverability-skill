# Acceptance report format

Use concise prose or this table structure, sized to the task. A small read-only check may use a shortened report. Do not claim a PASS for anything not tested.

## Scope and mode
- Mode: Build It Right / Audit and Repair
- Site type: public / private / hybrid; framework and hosting (verified or unknown)
- Authorized action: read-only / development edit / publish (specific user approval)

## Findings and evidence
| Priority | Route/component | Observation | Evidence type | Recommendation |
|---|---|---|---|---|
| ... | ... | ... | live / built / source / browser / Search Console / inferred | ... |

## Changes, if approved
- Exact file(s)/route(s) changed and why.
- Explicitly preserved functionality, design, content, private routes and data rules.
- Any deviations from approved scope; obtain approval before expanding.

## Verification
| Test | Result | Environment and proof/limitations |
|---|---|---|
| Initial HTML / metadata / content | PASS / FAIL / UNTESTED | ... |
| Hydration and core interactions | PASS / FAIL / UNTESTED | ... |
| Desktop/mobile visual regression | PASS / FAIL / UNTESTED | ... |
| Accessibility / contrast | PASS / FAIL / UNTESTED | numeric measurements where relevant |
| Performance | PASS / FAIL / UNTESTED | before/after and conditions if measured |
| Build/typecheck | PASS / FAIL / UNTESTED | ... |
| Auth/privacy regressions (if applicable) | PASS / FAIL / UNTESTED | no real client data |
| Live production confirmation | PASS / FAIL / PENDING / NOT AUTHORIZED | ... |

## Decision and follow-up
- Outcome: ready for review / ready to publish (not yet published) / published and live-verified / blocked / deferred.
- Known unknowns and risks, including difference between indexability and actual indexation.
- Lowest-risk next action and whether user approval is required.

Never report a site as Google-indexed based only on a sitemap, an HTML canonical, a 200 response, or an SEO scanner health score.
