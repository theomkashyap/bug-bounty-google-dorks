# bug-bounty-google-dorks

Random google dorks I've collected over time for finding bug bounty / responsible disclosure pages. Mostly for recon before I actually start testing anything — helps figure out if a company even has a program before wasting time on it.

There's a lot of these lists floating around already but most of them are just copy-pasted from each other with duplicates everywhere, so I cleaned mine up and grouped them by what they're actually useful for.

Nothing here is an exploit dork. It just helps you find pages companies have already made public — security.txt files, disclosure pages, bounty programs etc.

## how to use it

Copy any line below into Google. Change the `site:*.xx` part to whatever TLD or region you're looking at. Some of these will return nothing, some will return a lot of noise — that's just how dorking is, you have to sift through it.

Also don't just report the first thing you find. Check the actual scope/rules on the program page before touching anything.

## general

```
inurl:/bug-bounty "security"
inurl:/security "bug bounty"
inurl:/security.txt "bug bounty"
inurl:/.well-known/security.txt
inurl:/.well-known/security.txt intext:bounty -hackerone -bugcrowd -synack
inurl:security.txt intext:"mailto" -github.com -wikipedia.org -portswigger.net -magento
inurl:/security ext:txt "contact"
inurl:security-policy.txt ext:txt
inurl:reporting-security-issues
inurl:responsible-disclosure-policy
inurl:vulnerability-disclosure-policy reward
inurl:/trust/report-a-vulnerability
intext:"security vulnerability" "report"
intitle:"Bug Bounty" OR intitle:"Vulnerability Disclosure" OR intitle:"Security Rewards"
"submit vulnerability report" -site:hackerone.com -site:bugcrowd.com -site:synack.com -site:openbugbounty.org
"If you believe you've found a security vulnerability"
"vulnerability reporting policy"
"vulnerability disclosure program" AND (bounty OR reward OR swag OR "hall of fame")
```

## rewards / swag / money signals

these usually mean the program actually pays or gives something back, not just a thank-you page

```
intext:"responsible disclosure" "bounty" "reward"
intext:"we offer a bounty"
intext:"security vulnerability" "eligible for reward"
intext:"you may be eligible for monetary compensation"
"responsible disclosure" AND (monetary OR cash OR "gift card" OR crypto OR BTC)
"If you discover a vulnerability" AND (swag OR "hall of fame" OR monetary)
responsible disclosure hall of fame
inurl:bug bounty intext:"₹" OR intext:"rupees" OR intext:"INR"
inurl:"bug bounty" intext:"$" inurl:/security
inurl:"bug bounty" intext:"€" inurl:/security
```

## programs hosted on a platform but self-hosted page

companies that use hackerone/bugcrowd/etc but still have their own disclosure page

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

## region specific

swap the tld for whatever country you're focusing on

```
site:*.nl intext:responsible disclosure reward
site:*.uk intext:security report reward
site:*.de inurl:bug inurl:bounty
site:*.br responsible disclosure bounty
site:*.au responsible disclosure bounty
site:*.cn intext:security report reward
site:*.ca intext:"responsible disclosure" intext:reward
site:*.jp intext:"vulnerability report" intext:swag
site:*.it intext:"bug bounty" OR intext:"security reward"
site:*.se intext:"responsible disclosure" intext:hall_of_fame
site:*.fr intext:"bug bounty" OR "prime de sécurité"
site:*.es inurl:/seguridad intext:recompensa
site:*.pl inurl:/bezpieczenstwo intext:nagroda
site:*.dk inurl:/sikkerhed intext:dusør
site:*.no inurl:/sikkerhet intext:belønning
```

## gov / edu / finance

these are usually stricter about scope so read the policy carefully before testing

```
site:*.gov "responsible disclosure" OR "vulnerability disclosure program" OR "bug bounty"
site:*.gov inurl:/security intext:contact intext:reward
site:*.gov filetype:pdf "vulnerability disclosure policy"
site:*.mil "security vulnerability report"
site:*.edu "responsible disclosure" AND (reward OR swag OR bounty)
site:*.edu inurl:/security intext:"report a vulnerability"
site:*.edu intext:"vulnerability disclosure policy" intext:hall_of_fame
site:*.bank "security vulnerability report"
site:*.finance "bug bounty"
```

## crypto / fintech

```
"bug bounty" intext:"BTC" OR "ETH" OR "USDT" OR crypto OR reward
intext:"cryptocurrency" "bug bounty"
site:*.exchange intext:security vulnerability report
inurl:security-report intext:crypto OR blockchain OR token
```

## cms / open source

```
"cms" bug bounty
"open-source security bounty"
inurl:/wp-content/plugins/ intext:vulnerability report
inurl:/modules/security-report/
```

## random extra one

finds publicly exposed docs on a specific target, not really a bounty dork but I use it a lot during recon

```
site:target.com ext:doc OR ext:docx OR ext:pdf OR ext:odt OR ext:rtf OR ext:ppt OR ext:pptx OR ext:csv
```

## a quick note

Everything above only surfaces stuff that's already public and indexed by Google, it's not doing anything to the target itself. Still — always check the program's actual scope before you report anything, and don't touch anything that doesn't have a public disclosure policy without permission. Use this responsibly.

## contributing

If you've got a dork that isn't already in here and actually works, open a PR, I'll add it to whichever section fits.

## license

MIT
