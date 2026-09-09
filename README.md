# In Your Base

A personal, local-only browser for your own exported data. Drop in any
`.json` file and it detects the file type automatically — then search,
filter, tag, and read back through it, entirely on your own device.

## Try it

**[laustenfaund.github.io/In_Your_Base](https://laustenfaund.github.io/In_Your_Base/)** (bring your own Anthropic API key for the assistant) · **[hosted version](https://laustenfaund.github.io/In_Your_Base/hosted/)** (passcode) · [Source](https://github.com/laustenfaund/In_Your_Base)

The hosted version's page is live, but its assistant proxy isn't deployed
yet — `ASSISTANT_PROXY_URL` in `hosted/index.html` is still the placeholder
from `worker/README.md`. Everything else (import, search, filter, tag,
browse) works the same on both; deploy the Worker to turn the hosted
assistant on.

## What it does

- **Detects the file type automatically.** Recognized export formats are
  read with full fidelity. Anything else is read from whatever fields
  and structure it actually has — nothing invented or guessed at — and
  shown the way that fits it. The only items left out are a completely
  empty one, or one that's already in your archive.
- **Searches and filters** by keyword, platform, date range, and your own
  tags, across everything you've loaded. The platform filter isn't fixed
  to a couple of values — it's built from whatever's actually present.
- **Timeline** view of activity by month.
- **A search brief** — a written procedure meant to be handed to an AI
  assistant, describing how to work through a large personal data set
  deliberately (scope, catalog, flag, read, record) rather than skimming it.
- **An optional AI assistant** that runs that brief live, using an Anthropic
  API key you supply. Off by default; nothing is sent anywhere unless you
  turn it on. As it reads, it logs short quote-plus-note findings instead of
  holding full text in context — keeps token spend from climbing every
  round of a long search.

## Privacy

In Your Base is a single self-contained HTML file with no server behind it.
Everything it parses — your records, tags, saved brief — is written to
your browser's local storage on your device, and nothing is sent out over
the network, with one exception: if you set up the AI assistant, your
messages and API key go directly from your browser to `api.anthropic.com`.
No part of this app has a backend of its own, and nothing routes through
any server of ours.

What you load is tied to one browser, on one device — it doesn't sync.
There's no built-in export, so keep your original `.json` files;
re-importing them is how you'd rebuild it elsewhere.

## Usage

Use the live link above, or download `index.html` and open it in a browser
directly — double-click works, no install or build step needed either way.
The in-app **manual** button covers every feature in detail once it's open.

## The hosted variant

[`hosted/`](hosted) is a clone of this same app with one change: instead of
each person pasting in their own Anthropic API key, the AI assistant is
gated by a passcode and routed through a small proxy (in [`worker/`](worker))
that holds a single shared key server-side, with hard per-person and
total spending caps enforced before any request goes out. Use this if you
want to give a few people access to the assistant without also giving them
your API key. See [`worker/README.md`](worker/README.md) to deploy the
proxy; the UI is otherwise identical to the plain version above.

## Installing on your phone

Both links above are installable as a PWA (Progressive Web App) —
`manifest.json`, `sw.js`, and `icons/` (each variant has its own) give it a
name, an app icon, and a minimal offline shell cache so it behaves like a
real app on your home screen instead of just a bookmark.

Open the live link on your phone — not the repo's `github.com` page — and
use your browser's "Add to Home Screen" / "Install app" option.

## License

All rights reserved — see [`LICENSE`](LICENSE). This repository is shared
for personal reference; reuse requires asking first.
