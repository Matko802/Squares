# Sharp Corners — Zen Browser mod

Removes rounded corners from Zen's UI: tabs, sidebar, urlbar, panels, popups,
buttons, findbar.

## Why this needs one extra step

Zen's "Import Mods" button doesn't accept a JSON with the CSS embedded
inline — the manifest just carries metadata, and its `style` field has to
point to a URL where `chrome.css` is actually hosted. That's how every mod
on the official Zen Mods store works too (the store itself is just a
themes.json registry of URLs). So to make this a real, importable mod
(rather than a file you manually drop in your profile folder), the CSS
needs a public URL.

## Setup (one-time, ~2 minutes)

1. Create a public GitHub repo (or just a Gist) and add `chrome.css` from
   this folder to it.
2. Get the **raw** URL for the file:
   - Repo file: click the file on GitHub → "Raw" button → copy that URL.
   - Gist: same — open the gist → click "Raw" on the file → copy the URL.
3. Open `themes.json` and replace `REPLACE_WITH_RAW_CHROME_CSS_URL` with
   that raw URL.

## Installing it in Zen

1. Zen → Settings → Mods (`about:preferences#zenMarketplace`).
2. Click **Import Mods**, select your edited `themes.json`.
3. Enable "Sharp Corners" in the list if it isn't already on.
4. Restart Zen fully.

## Known Zen quirk

Local/self-hosted mod imports have had a bug in some Zen versions where
it tries to re-fetch a manifest from the official theme store by id
instead of trusting the local file, which can make the import silently do
nothing. If that happens: enable "Custom CSS" under the same Mods page and
paste `chrome.css` in there directly as a fallback — it applies immediately
without needing the JSON/URL step at all, you just lose the "shows up as
an installed mod with a toggle" packaging.
