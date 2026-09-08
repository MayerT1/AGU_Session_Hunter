# AGU_Session_Hunter
AGU_Session_Hunter


What the loop does:

For each of the 28 category pages, it:

Downloads the raw HTML.
Finds every <a href="SessionNNNNNN.html">Title</a> tag with regex — this is one session entry.
For each match, grabs the session number from the URL, cleans the title text, and builds the full URL.
Slices out the HTML between this link and the next session link — that's the "Primary Convener / Conveners" block — and strips it to plain text (detail_text).
Cuts off page-footer junk ("Browse Sessions...") if it leaked into the last session's block.
Appends a dict (category, session_number, title, url, detail_text) to rows.

It repeats this per category, collects everything into all_rows, then builds one big DataFrame (df) — one row per session, across all 28 categories. A 0.5s sleep between requests avoids hammering the server.

That's it — it's a scrape-and-flatten loop, not doing any filtering itself (that happens after, in step 3 of the full script).
Inclusive
KEYWORDS = [
    "Foundational",
    "AI",
    "Geo-AI",
    "Generative AI",
    "NASA",
    "Huntsville",
    "Large Earth Model",
]

Exclusive
KEYWORDS = [
    "Foundational",
    "Foundation",
    "Agentic",
    "Agent",
]

