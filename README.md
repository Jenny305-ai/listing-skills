# Listing Skills

Reusable Codex skills for Shopify listing workflows:

- `babelio-premium-listing`: evidence-based premium Babelio listings using matching Amazon and first-party sources.
- `bulk-product-listing`: batch Babelio draft listing generation without per-SKU competitor research.
- `petitwishes-apparel-listing`: Petitwishes apparel listings using the designated keyword sheet and IP/sensitive-word checks.

## Install with Codex

Ask Codex to install all three skills from this repository:

```text
Use $skill-installer to install these skills from Jenny305-ai/listing-skills:

skills/babelio-premium-listing
skills/bulk-product-listing
skills/petitwishes-apparel-listing
```

For a private repository, the recipient must have repository access and working GitHub credentials on their computer.

The skills become available on the next Codex turn after installation.

## Manual installation

Copy each skill directory into `$CODEX_HOME/skills/`. If `CODEX_HOME` is unset, use:

- Windows: `%USERPROFILE%\.codex\skills\`
- macOS/Linux: `~/.codex/skills/`

Keep each skill directory intact, including `SKILL.md`, `agents/`, and `references/`.

## Required access

These skills do not include account credentials. Each user must connect or authenticate their own Shopify, browser, Google Drive/Sheets, and other required sources.

Shopify is read-only by default. A write-back run is permitted only when the user's current request explicitly includes `允许写入 Shopify`.

The Petitwishes workflow references a designated Google Sheet. Recipients need at least read access to that sheet, or the reference must be replaced with an authorized sheet for their environment.
