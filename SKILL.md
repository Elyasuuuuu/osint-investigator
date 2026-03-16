---
name: username-email-investigator
description: Investigate a public online footprint from a username or email using open-source intelligence techniques. Use when a user wants to find public profiles across major platforms, correlate likely matches, assess whether accounts may belong to the same person, generate plausible username variants, validate profile candidates per platform, capture public profile image links when available, run defensive Have I Been Pwned email checks when configured, or export structured JSON results.
---

# Username / Email Investigator

Use this skill for public-footprint OSINT based on:
- username
- email address
- or both together

Read as needed:
- `references/workflow.md` for the investigation flow
- `references/platforms.md` for target platforms and search ideas
- `references/platform-validation.md` for platform-specific validation rules
- `references/profile-media.md` for profile image handling
- `references/scoring.md` for confidence logic
- `references/variants.md` for handle-variant generation
- `references/tooling.md` for the lightweight discovery helper
- `references/breach-checks.md` for optional defensive breach lookup behavior
- `references/configuration.md` for HIBP API key setup
- `references/safety.md` for acceptable-use boundaries
- `references/output.md` for response structure

Use scripts when helpful:
- `scripts/generate_variants.py` for plausible username variants
- `scripts/check_profiles.py` for first-pass platform checks with platform-aware validation
- `scripts/check_hibp.py` for optional Have I Been Pwned email checks
- `scripts/export_json.py` for structured JSON output

## Core behavior

- Focus on public data only.
- Prefer lightweight verification over aggressive scraping.
- A 200 HTTP status is not enough to confirm a profile.
- Separate facts from guesses.
- Report confidence, not certainty.
- Keep results structured and easy to audit.
- Prefer a smaller set of verified findings over a noisy wall of guesses.

## Workflow

1. Normalize the input.
2. Generate a small set of plausible username variants when useful.
3. Run a lightweight multi-platform presence check when useful.
4. Validate candidate results per platform.
5. Capture final links and public profile image URLs when available.
6. If an email is provided and HIBP is configured, run a defensive breach check.
7. Record exact matches, likely matches, weak matches, no-results, and not-verifiable results.
8. Compare public signals across candidates.
9. Assign a confidence level using `references/scoring.md`.
10. Return a concise human summary.
11. Export JSON if requested.

## Output rules

Always distinguish between:
- confirmed public match
- likely match
- weak/uncertain match
- not verifiable
- no evidence found

Include final profile links for matches.
Include profile image links only when they are publicly exposed and easy to extract.
If HIBP is used, report breach results as defensive exposure information, not identity proof.

Do not overclaim identity resolution.
If evidence is thin, say so clearly.
If evidence conflicts, say so clearly.
Lead with the strongest public evidence first.

## JSON export

If the user requests JSON:
- use `scripts/export_json.py`
- include the input, platforms checked, matches found, signals observed, final links, profile image links when available, optional breach-check results, and confidence summary

## Safety

Read `references/safety.md` when the request could drift into harassment, private-person targeting, or invasive tracking.

Do not help with:
- credential theft
- account takeover
- bypassing access controls
- doxxing
- stalking or targeted harassment
- collecting non-public personal data

## Style

- concise
- factual
- audit-friendly
- explicit about uncertainty
