# where-to-harness

English | [日本語](README.ja.md)

A skill that finds **where to go**, by going back and forth between your unspoken preferences and AI fact-checking. Installs in Claude Code and Codex (tested on Claude Code only).

Use it for either of these:

- **Trips**: where to stay, which area, what to do each day, all the way to an itinerary
- **Food**: just a place to eat, e.g. "a quiet izakaya in Tokyo for four on Friday, no chains". No trip needed

It turns vague feelings like "a quiet place", "no chains" or "I get bored just staying in the hotel" into search terms and exclusion terms. The AI then searches the web and the official sites of hotels and restaurants, and returns a comparison table per constraint plus a recommendation. Anything search can't answer is marked "unconfirmed" and goes on a list of things to ask by phone.

- If you'd rather search yourself, say so and you get search links (Google Search, Google Maps). Paste the names, links or screenshots you found and they're judged against the same criteria
- The AI never auto-fetches booking, gourmet or review sites. You check prices, availability and reviews yourself through the links it gives you
- No API keys or external services to set up
- Search terms are built in **the destination's language**, not yours. For Japan, a bundled Japanese term pack is used (with short glosses if you don't read Japanese). For other countries, terms are built on the spot in the local language
- Conversation only by default. Say "save this" and it creates Markdown ledgers (constraints, candidates, things to confirm, decisions, itinerary) in your working folder, so you can pick up where you left off

## Install (Claude Code)

Run in a terminal:

```
claude plugin marketplace add takuto0831/where-to-harness
claude plugin install where-to-harness@where-to-harness
```

Restart Claude Code after installing.

### Update to a new version

```
claude plugin marketplace update where-to-harness
claude plugin update where-to-harness@where-to-harness
```

## Install (Codex)

Codex can't use the Claude Code plugin, but it can install the skill folder straight from this repo with its built-in skill installer. Ask Codex:

```
$skill-installer https://github.com/takuto0831/where-to-harness/tree/main/skills/where-to-harness
```

It goes into `~/.codex/skills/where-to-harness`. Restart Codex after installing. Turn on web search in Codex, since the skill searches the web.

To update, delete `~/.codex/skills/where-to-harness` and run the same command again.

## Usage

Open Claude Code and say "help me plan a trip", or just "find me an izakaya in Shibuya for tonight". If you plan to save, open it in a folder for your outings rather than in this repo (records go into `outings/` in that folder).

> **Note: don't put `WebFetch(domain:*)` in deny.** If your Claude Code settings (`permissions.deny` in `settings.json`) contain `WebFetch(domain:*)`, every page fetch is refused, so the skill can't read the official sites of hotels and restaurants. It has to judge from search results alone, and nothing can get a ○ checked on an official site. To keep specific sites out, deny those domains one by one.

## What's inside

- `skills/where-to-harness/SKILL.md` … the skill
- `skills/where-to-harness/dictionary.md` … core dictionary: unspoken preference → observable signals, what the AI judges, how to confirm (language-independent)
- `skills/where-to-harness/locales/` … search term packs per destination. Japan is `ja-JP.md` (search and exclusion terms, local conditions, local booking and gourmet sites)
- `skills/where-to-harness/templates/` … templates for an outing folder (a trip or a meal out)

Contributions to the dictionary and new locale packs are welcome: see [CONTRIBUTING.md](CONTRIBUTING.md).
