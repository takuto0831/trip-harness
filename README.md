# trip-harness

English | [日本語](README.ja.md)

A Claude Code skill that plans trips by **going back and forth between your unspoken preferences and AI fact-checking**.

It turns vague feelings like "a quiet place", "no chains" or "I get bored just staying in the hotel" into search terms and exclusion terms. The AI then searches the web and the official sites of hotels and restaurants, and returns a comparison table per constraint plus a recommendation. Anything search can't answer is marked "unconfirmed" and goes on a list of things to ask by phone.

- If you'd rather search yourself, say so and you get search links (Google Search, Google Maps). Paste the names, links or screenshots you found and they're judged against the same criteria
- The AI never auto-fetches booking, gourmet or review sites. You check prices, availability and reviews yourself through the links it gives you
- No API keys or external services to set up
- Search terms are built in **the destination's language**, not yours. For Japan, a bundled Japanese term pack is used (with short glosses if you don't read Japanese). For other countries, terms are built on the spot in the local language
- Conversation only by default. Say "save this" and it creates Markdown ledgers (constraints, candidates, things to confirm, decisions, itinerary) in your working folder, so you can pick up where you left off

## Install (Claude Code)

```
/plugin marketplace add takuto0831/trip-harness
/plugin install trip-harness@trip-harness
```

Where `/plugin` isn't available (e.g. the VS Code extension), do the same from a terminal:

```
claude plugin marketplace add takuto0831/trip-harness
claude plugin install trip-harness@trip-harness
```

Restart Claude Code after installing.

### Update to a new version

```
claude plugin marketplace update trip-harness
claude plugin update trip-harness@trip-harness
```

## Usage

Open Claude Code and say "help me plan a trip". If you plan to save, open it in a folder for your trips rather than in this repo (the records go into that folder).

## What's inside

- `skills/trip-harness/SKILL.md` … the skill
- `skills/trip-harness/dictionary.md` … core dictionary: unspoken preference → observable signals, what the AI judges, how to confirm (language-independent)
- `skills/trip-harness/locales/` … search term packs per destination. Japan is `ja-JP.md` (search and exclusion terms, local conditions, local booking and gourmet sites)
- `skills/trip-harness/templates/` … templates for a trip folder

Contributions to the dictionary and new locale packs are welcome: see [CONTRIBUTING.md](CONTRIBUTING.md).
