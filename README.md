# bug-bounty-google-dorks

Google dorks for finding bug bounty / responsible disclosure programs. Cleaned up, deduplicated, and organized so it's actually usable — no broken `site:*.xx` wildcard stuff that Google stopped supporting.

Written so it works whether you're just starting or you've been doing this a while.

The full dork list lives in [`dorks/`](dorks/), split by category, plus one combined file with everything. This README is just the overview — grab the actual dorks from there.

---

## if you're new to this (read this first)

A "dork" is just a normal Google search using special operators. You're not hacking anything by searching — you're just finding pages companies already made public.

Operators used below:

- `site:example.com` — only search within one specific website
- `inurl:word` — the URL contains this word
- `intext:"exact phrase"` — the page text contains this exact phrase
- `intitle:word` — the page title contains this word
- `-word` — exclude results with this word
- `OR` — match either term
- `filetype:pdf` / `ext:txt` — only that file type

**Note on wildcards:** Google no longer supports `site:*.xx` style wildcard TLD searches (e.g. `site:*.shop`, `site:*.gov`) — they just return zero results now. These show up on basically every old dork list floating around online, but they don't work anymore, so they're left out here.

**How to use:** pick a dork, swap in a real domain where relevant, paste into Google, sift through results. Some return junk — that's normal, dorking is trial and error. Always check the actual program page for scope/rules before reporting anything.

---

## categories

| file | what it finds |
|---|---|
| [`01-general-discovery.txt`](dorks/01-general-discovery.txt) | broad search for any public security/disclosure/bounty page |
| [`02-rewards-signals.txt`](dorks/02-rewards-signals.txt) | signals that a program actually pays, not just a thank-you page |
| [`03-self-hosted-programs.txt`](dorks/03-self-hosted-programs.txt) | companies running their own disclosure page instead of a platform |
| [`04-target-specific.txt`](dorks/04-target-specific.txt) | template dorks for digging into one company once you have a target |
| [`05-gov-edu-finance.txt`](dorks/05-gov-edu-finance.txt) | .gov / .edu / .mil / finance — usually stricter scope |
| [`06-crypto-fintech.txt`](dorks/06-crypto-fintech.txt) | crypto exchanges and fintech-specific programs |
| [`07-cms-opensource.txt`](dorks/07-cms-opensource.txt) | CMS plugins and open-source project bounties |
| [`08-ecommerce-payments.txt`](dorks/08-ecommerce-payments.txt) | online stores and payment/checkout flows |
| [`09-recon-bonus.txt`](dorks/09-recon-bonus.txt) | not a bounty-finder — finds exposed docs on a target you're already working |
| [`all-dorks.txt`](dorks/all-dorks.txt) | everything above, combined, one dork per line |

---

## a note on scope and ethics

- These only surface pages that are already public and indexed by Google — nothing here touches or exploits a target.
- Always read the actual scope of a program before testing anything.
- Never test a company without a public disclosure policy or bounty program, without written permission.
- This is a time-saver for finding programs, not a shortcut around the rules.

## contributing

Got a dork that's actually working and isn't a duplicate? Open a PR against the relevant file in `dorks/` and it'll get added.

## license

MIT
