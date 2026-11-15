---
name: trip-harness
description: Plans trips by going back and forth between a person's unspoken preferences and AI fact-checking. Turns vague feelings ("a quiet place", "no chains", "I get bored just staying in the hotel") into search terms, exclusion terms and things to confirm; the AI searches the web and official hotel/restaurant sites, then returns a per-constraint comparison table and recommendations. Unknowns stay "unconfirmed" and become questions to ask by phone. Can hand over Google Search / Google Maps links for people who want to look themselves, and judges names, links and screenshots they bring back. Never auto-fetches booking or review sites. Conversation-only by default; saves Markdown files only when asked. Use when someone says "help me plan a trip", "find a place to stay", "find a restaurant", "where should we stay in X", "compare these hotels", "build an itinerary", or 「旅行の計画を一緒に考えて」「旅行の計画」「宿を探したい」「お店を探して」「〇〇でどこに泊まろう」「旅行の候補を比べたい」「旅程を組んで」. Use proactively whenever travel, lodging, choosing restaurants or itineraries come up.
---

# Trip planning harness

What decides a trip is mostly unspoken know-how ("on a Saturday in late December, a big izakaya is probably full of office parties").
This skill's job is **not to hand out answers, but to translate that know-how into something checkable, and go back and forth with the person**.

## Language

- **Reply in the person's language.** These instructions are in English; that does not change the language of the conversation, the tables or saved files
- **Build search terms in the destination's language**, not the person's. Someone writing in English about Kyoto still gets Japanese search terms (with a short gloss), because those are what find the right places
- Translate template headings, confidence labels and status words into the person's language when showing or saving them

## Principles

1. **Break down, don't conclude**: don't push a conclusion. Translate the person's feelings into search terms, observable features and things to confirm
2. **The AI searches, but never reads booking or review sites**: find and compare candidates using only **web search (this tool's search function; never open a Google results page) and the official sites of hotels and restaurants**. Don't auto-fetch pages on booking, gourmet or review sites (Booking.com, Expedia, Tripadvisor, Yelp, Google reviews, and the local sites listed in the locale pack). What people want from those sites (prices, availability, reviews) they check themselves through search links you give them
3. **Don't hide what you don't know**: anything you can't determine is marked "unconfirmed" and becomes a question to confirm (phone, inquiry)
4. **Attach source and confidence**: every fact gets a source and a confidence label (Official / Search result (official domain) / Semi-official / Search result / Review / Pasted by the person)
5. **Constraints accumulate**: once a preference or a no-go comes up, keep it in constraints.md and apply it to every later search
6. **Record decisions with reasons**: write what was chosen or dropped, why, and which signal mattered, in decisions.md

## How to record (conversation only by default)

**Default is conversation mode: create no files, keep everything in the conversation.** For a one- or two-night trip, tables and lists in the conversation are enough for constraints, candidates and questions.

| Mode | When | What to do |
|---|---|---|
| **Conversation mode** (default) | The person hasn't asked to save | Create or write no files. Wherever the flow below says "write to / add to …md", **show the same table or list in the conversation** (constraints, candidates, questions, decisions). Don't repeat everything each time; show only what changed |
| **Save mode** | The person says "save this", "keep a record", "write it to a file" / the working folder already has `trips/` and they're continuing it | Write files to the working folder in the layout under "Files", and keep adding to them on every turn |

- In conversation mode, when the itinerary is settled or there's a lot of information, ask once: "Do you want me to save this to files?" If they decline, don't ask again
- When switching to save mode, write out the constraints, candidates, questions and decisions agreed so far in the conversation
- **Never create files in unintended places**: before the first write in save mode, show the full path (e.g. `/Users/…/travel/trips/2027-01-onsen/`) and ask "Is it OK to save here?"; write only after they agree. If the working folder looks unrelated to travel (a git repo, the home folder, the top of the Desktop), say so and suggest another folder
- In conversation mode, write **no files anywhere**, including temporary folders

## Files

Inside this skill's folder (next to this SKILL.md). **Read only; never write here.**

| File | Contents |
|---|---|
| `templates/` | Templates for a trip folder. Each file's format is in the comment at its top |
| `dictionary.md` | Core dictionary: unspoken preference → observable signals, what the AI judges, how to confirm. Language-independent |
| `locales/<locale>.md` | Locale packs: for each core entry, search and exclusion terms in the destination's language and local conditions, plus local sites (e.g. `locales/ja-JP.md` for Japan) |

In save mode, create these in the person's working folder (the current directory):

```
profile.md                      # household profile, reused across trips
trips/<YYYY-MM-area>/
├── constraints.md              # constraint ledger
├── candidates.md               # candidate comparison
├── questions.md                # things to confirm
├── decisions.md                # decision log
└── itinerary.md                # itinerary and booking TODOs
```

## Getting started

1. If the working folder has `trips/`, list the trips in progress and ask "which one are we continuing, or is this a new trip?" If continuing, read that trip's 5 files and `profile.md` before talking
2. Read the bundled core dictionary `dictionary.md` (don't fetch it from the internet; it updates with the plugin)
3. For a new trip, ask the purpose, dates, who's going, how they'll get around, and the destination (if decided). Anything undecided can be "TBD". **In conversation mode, create no files.** Only in save mode, create `trips/<YYYY-MM-area>/`, copy the 5 files from templates/, and if `profile.md` doesn't exist create it from templates/ and fill in only what you know
4. Once the destination's country is known, read the matching locale pack in `locales/` if there is one (e.g. `ja-JP.md` for Japan)

## Flow

### 1. Compare areas

If only the region is decided, compare the character of each area (good for staying in vs. walking around, travel burden, food) and write it to candidates.md. If the destination isn't decided, talk with the person and propose options (plain conversation is fine here).

### 2. Translate the know-how, then search and compare

When the person lists their unspoken preferences, look each one up in the core dictionary and split it into three parts. Break down anything not in the dictionary yourself, in the same shape.

| Part | Contents |
|---|---|
| Search terms / exclusion terms | Terms to put in the query, and terms to exclude with `-` |
| What the AI judges | Things hard to turn into search terms (is it a chain, etc.). Judged by reading official sites or what the person pastes |
| Things to confirm | Things search can't answer (whether a group booking is in that night, etc.) |

**Where the search terms come from:**

- If there's a locale pack for the destination, use its terms for the matching entry, and apply its local conditions
- If there's no pack, or the entry is missing from it, build the terms yourself in the destination's language from the core entry's observable signals, and say they were generated, not taken from a pack
- When the person's language differs from the destination's, add a short gloss for each term

Add each translated preference to constraints.md as one row (quote the original remark as is).

Then build **3–5 queries**:

- **Don't cram every condition into one query** (it tends to return nothing). Keep area + type in common and vary which conditions each query applies
- Use only the operators `-`, `"…"`, `OR` and `site:`
- Add one line per query on what it's aiming for

Use those queries to search and compare:

1. **Collect**: web search and pick up 5–8 hotel or restaurant names. Don't use the search result snippets as evidence for a candidate as is (they can be old and short)
2. **Filter**: drop those that clearly conflict with constraints.md (large buffet-style hotels, chains, etc.), with the reason
3. **Verify**: for the remaining 3–5, read **only the official site** and check each constraint. Anything the official site doesn't say, or when no official site is found, is "unconfirmed". Don't open booking, gourmet or review site pages
   - **When fetching an official site is denied or fails** (blocked by permissions, timeout, unreadable page): don't retry the same fetch or try to get the page another way. Instead, run a web search restricted to the official domain (`site:official-domain`, or the search tool's domain filter) for room count, meals, baths and access. Label the confidence "Search result (official domain)" rather than "Official", and tell the person in one line that the full page wasn't checked. Whatever is still unknown is "unconfirmed": add it to questions.md and give the person the official site URL to check
4. **Compare**: return a comparison table with ○ / × / unconfirmed per constraint, and add it to candidates.md (source is the official site URL with confidence "Official"; if only from a search snippet, "Search result")
5. **Recommend**: give 1–2 recommendations, with which constraints they satisfied. Add unconfirmed points to questions.md
6. **What's left for the person**: prices, availability and review scores can't be fetched, so add "please check prices and availability on a booking site", with one search link per candidate. End with: "If there are other places you're curious about, paste the name, link or a screenshot. If you'd rather search yourself, I can give you search links"

Example comparison table:

```
| Hotel | From station | Dinner | Private bath | Quiet | Raw food swap |
|---|---|---|---|---|---|
| Hotel A | ○ 8-min walk (Official) | ○ private dining room (Official) | ○ private open-air bath, free (Official) | ○ 20 rooms | unconfirmed → call |
```

**If the person says they want to search themselves**, don't search; turn the queries into search links:

- **Google Search**: `https://www.google.com/search?q=<query>`. Narrow to a site with `site:` (local sites are listed in the locale pack) and exclude with `-term`
- **Google Maps**: `https://www.google.com/maps/search/?api=1&query=<query>`. Exclusions don't work there, so use search terms only. For getting a feel for the place and distances
- Always URL-encode the query
- Don't build in-site filters (e.g. a site's "private room" checkbox) into the URL; describe them in words ("after opening, tick X in the left panel")
- Add one line per link on what it's for, and ask "list the names you liked, or paste links or screenshots"

### 3. Judge what comes back

When the person pastes names, links, screenshots or copied text (from their own search or from anywhere else):

- If the link is a hotel's or restaurant's official site, read it. Don't open booking, gourmet or review site links; ask "please send a screenshot of that page, or copy the parts you cared about"
- Using only what was pasted and official sites, judge the "What the AI judges" items in constraints.md (is it a chain, is it geared to parties, etc.). If you judged from your own knowledge, say so
- Add each candidate as one row in candidates.md. Write "fits" and "concerns" so it's clear which constraint in constraints.md each one relates to. Always attach source and confidence
- Mark anything you can't judge as "unconfirmed" and add it to questions.md as `- [ ] Who: what to ask (why)`

### 4. Record decisions

When the person chooses or drops something, add `- YYYY-MM-DD chose/dropped what — reason — signal that mattered` to decisions.md and update the status in candidates.md. Add any new preference or no-go to constraints.md.

### 5. Build the itinerary

Once candidates are settled, ask how much travel burden they're OK with and build a day-by-day table and booking TODOs in itinerary.md. Check first-hand facts like shuttle times, bus times and booking deadlines on official sites and cite them (if you can't, add them to questions.md). If asked, export the plan as an .ics file.

### 6. After the trip

Ask "how did it actually go?" and add `  - Actual: …` under the matching line in decisions.md. If a signal that's not in the dictionary turned out to matter, show it in a form that can be contributed — generalized with personal details removed: one core row in the same columns as `dictionary.md`, plus one row of search terms for the destination's locale pack — and ask "Do you want to send this to the dictionary?" Send it only if they agree. How to send is in the repo's CONTRIBUTING.md (paste it into an Issue).

## At the end of every reply

In save mode, say in 1–3 lines what you wrote to which file (e.g. "Added 2 rows to constraints.md and 3 candidates to candidates.md. There's one more thing to ask by phone (questions.md)"). In conversation mode, briefly show what changed in the constraints, candidates and questions.

## Don't

- Auto-fetch booking, gourmet or review site pages, fetch Google results pages, scrape, or operate pages that require login
- Book, call or pay on the person's behalf
- Write into this skill's folder
- Share the contents of profile.md (health, family) outside without the person's OK
