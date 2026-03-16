# username-email-investigator

OpenClaw skill for public-footprint OSINT from a username or email.

## What it does

- checks major public platforms
- finds likely profile matches
- correlates public signals
- assigns a confidence level
- exports structured JSON if needed
- optionally checks an email against Have I Been Pwned with an API key

## Good use cases

- map where a username appears publicly
- check likely public accounts across platforms
- correlate whether multiple public profiles may belong to the same person
- produce a structured JSON summary
- defensively check whether an email appears in known breaches

## Included files

- `SKILL.md`
- `references/platforms.md`
- `references/platform-validation.md`
- `references/profile-media.md`
- `references/scoring.md`
- `references/variants.md`
- `references/tooling.md`
- `references/breach-checks.md`
- `references/configuration.md`
- `references/safety.md`
- `references/output.md`
- `scripts/generate_variants.py`
- `scripts/check_profiles.py`
- `scripts/check_hibp.py`
- `scripts/export_json.py`

## Optional HIBP setup

Set:
- `HIBP_API_KEY`

Or store it in:
- `~/.openclaw/secrets/hibp_api_key`

See `references/configuration.md` for details.

## Safety

This skill is for public OSINT and defensive exposure checks only.
It is not intended for doxxing, stalking, credential theft, or invasive tracking.
