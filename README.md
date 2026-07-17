# bug-bounty-google-dorks

Google dorks for finding bug bounty / responsible disclosure programs. Cleaned up, deduplicated, and organized so it's actually usable — no broken `site:*.xx` wildcard stuff that Google stopped supporting.

Written so it works whether you're just starting or you've been doing this a while.

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

**Note on wildcards:** Google no longer supports `site:*.xx` style wildcard TLD searches (e.g. `site:*.shop`, `site:*.gov`) — they just return zero results now. These show up on basically every old dork list floating around online, but they don't work anymore, so they're left out here. Where a region/industry dork existed only in that broken format, it's rewritten below using `inurl:` or plain keyword matching instead, which still works.

How to use: pick a dork, swap in a real domain where relevant, paste into Google, sift through results. Some return junk — that's normal, dorking is trial and error. Always check the actual program page for scope/rules before reporting anything.

---

## 1. general discovery

```
inurl:/.well-known/security.txt
inurl:/.well-known/security.txt intext:bounty -hackerone -bugcrowd -synack
inurl:security.txt intext:"mailto" -github.com -wikipedia.org -portswigger.net -magento
inurl:/security "bug bounty"
inurl:/bug-bounty "security"
inurl:/security ext:txt "contact"
inurl:security-policy.txt ext:txt
inurl:reporting-security-issues
inurl:responsible-disclosure-policy
inurl:vulnerability-disclosure-policy
inurl:/security/index.html intext:bounty
inurl:/legal/security intext:monetary
inurl:/trust/report-a-vulnerability
intitle:"Bug Bounty" OR intitle:"Vulnerability Disclosure" OR intitle:"Security Rewards"
intext:"security vulnerability" "report"
intext:"we take security very seriously"
"submit vulnerability report" -site:hackerone.com -site:bugcrowd.com -site:synack.com -site:openbugbounty.org
"If you believe you've found a security vulnerability"
"vulnerability reporting policy"
"vulnerability disclosure program" AND (bounty OR reward OR swag OR "hall of fame")
site:responsibledisclosure.com
```

## 2. rewards / swag / money signals

these usually mean the program actually pays or gives something back, not just a thank-you page

```
intext:"responsible disclosure" "bounty" "reward"
intext:"we offer a bounty"
intext:"security vulnerability" "eligible for reward"
intext:"you may be eligible for monetary compensation"
intext:"CVSS score" AND "eligible for a reward" -hackerone -bugcrowd
"responsible disclosure" AND (monetary OR cash OR "gift card" OR crypto OR BTC)
"If you discover a vulnerability" AND (swag OR "hall of fame" OR monetary)
responsible disclosure hall of fame
inurl:"bug bounty" intext:"₹" OR intext:"rupees" OR intext:"INR"
inurl:"bug bounty" intext:"$" inurl:/security
inurl:"bug bounty" intext:"€" inurl:/security
```

## 3. self-hosted programs (own page, platform running behind the scenes)

```
"powered by bugcrowd" -site:bugcrowd.com
"powered by hackerone" -site:hackerone.com
"powered by synack" -site:synack.com
"powered by yeswehack" -site:yeswehack.com
"powered by federacy" -site:federacy.com
"powered by intigriti" -site:intigriti.com
intext:"Powered by Bug Bounty HQ" OR "Powered by disclose.io"
intext:"managed by huntr.dev"
inurl:/hackerone.yml -site:hackerone.com
inurl:/bug-bounty.json
inurl:/vdp.json
```

## 4. targeting one specific company

Swap `example.com` for the real domain once you have a target in mind — this is where `site:` actually works well, since it's a full domain and not a wildcard.

```
site:example.com inurl:security
site:example.com "responsible disclosure"
site:example.com filetype:pdf OR filetype:doc OR filetype:docx OR filetype:xlsx OR filetype:csv OR filetype:pptx
site:example.com ext:txt "contact"
```

## 5. gov / edu / finance

usually stricter scope, read the actual policy carefully before testing

```
site:gov.uk "responsible disclosure"
site:gov.in "vulnerability disclosure"
inurl:.gov "responsible disclosure" OR "vulnerability disclosure program" OR "bug bounty"
inurl:.gov intext:contact intext:reward inurl:security
inurl:.mil "security vulnerability report"
inurl:.edu "responsible disclosure" reward
inurl:.edu "vulnerability disclosure policy"
inurl:.edu intext:"report a vulnerability"
inurl:.edu intext:"we run a bug bounty program"
intext:"bug bounty" (bank OR finance OR fintech)
```

## 6. crypto / fintech

```
"bug bounty" intext:"BTC" OR "ETH" OR "USDT" OR crypto OR reward
intext:"cryptocurrency" "bug bounty"
intext:"security vulnerability report" (exchange OR crypto OR blockchain OR token)
```

## 7. cms / open source

```
"cms" bug bounty
"open-source security bounty"
inurl:/wp-content/plugins/ intext:vulnerability report
inurl:/modules/security-report/
inurl:/.git intext:security vulnerability
```

## 8. e-commerce / payments

these industries specifically, using keyword matching instead of broken wildcard TLDs

```
intext:"bug bounty" (shop OR store OR ecommerce)
intext:"responsible disclosure" (payment OR checkout OR "online store")
intext:"if you find a vulnerability" (bank OR payment)
```

## 9. bonus recon dork

not a bounty-finder, but useful once you're actually working a target — finds publicly exposed docs

```
site:example.com ext:doc OR ext:docx OR ext:pdf OR ext:odt OR ext:rtf OR ext:ppt OR ext:pptx OR ext:csv
```

---

## a note on scope and ethics

- These only surface pages that are already public and indexed by Google — nothing here touches or exploits a target.
- Always read the actual scope of a program before testing anything.
- Never test a company without a public disclosure policy or bounty program, without written permission.
- This is a time-saver for finding programs, not a shortcut around the rules.

## contributing

Got a dork that's actually working and isn't a duplicate? Open a PR and it'll get added to the right section.

## license

MIT
