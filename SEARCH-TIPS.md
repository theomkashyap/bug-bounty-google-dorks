# advanced combos

Single operators are fine for browsing, but chaining them cuts out 90% of the noise. Below are combos that actually narrow results, plus *why* each one works — so you can build your own instead of just copy-pasting.

Swap `target.com` for the real domain you're working on.

---

### 1. Find raw API paths, skip the sanitized docs

```
site:target.com inurl:api -inurl:docs filetype:json
```

**Why it works:** Documentation pages usually show cleaned-up, fake example payloads. Raw `.json` responses sitting outside `/docs/` are more likely to be actual endpoint dumps, config exports, or leftover test fixtures — someone's real data, not a tutorial.

---

### 2. Internal tools accidentally left public

```
site:target.com (inurl:admin OR inurl:internal OR inurl:staging) -inurl:login
```

**Why it works:** `-inurl:login` filters out the thousands of "here's my login page" results and leaves pages that got indexed *past* auth — meaning they were public at some point, even briefly. That's the interesting subset.

---

### 3. Exposed config / env files

```
site:target.com (ext:env OR ext:yml OR ext:ini) (inurl:config OR inurl:settings)
```

**Why it works:** Combining the file extension with a path keyword filters out the millions of unrelated `.yml`/`.ini` files (like CI configs in public repos) and keeps ones that live under an app's actual config directory — much higher signal for real secrets or connection strings.

---

### 4. Old disclosure pages that changed URL structure

```
site:target.com intitle:"security" OR intitle:"responsible disclosure" -inurl:careers
```

**Why it works:** Companies rename their security pages often (`/security` → `/.well-known/security.txt` → `/trust`). Searching the page *title* instead of the URL catches renamed pages the URL-based dorks miss. `-inurl:careers` kills the "security engineer job posting" noise that floods this search.

---

### 5. Third-party exposure through subdomains

```
site:*.target.com -site:www.target.com inurl:api
```

**Why it works:** Main domains are usually locked down and monitored closely. Subdomains — especially old marketing microsites or acquired-company domains — get forgotten. Excluding `www` forces Google to surface the neglected corners first.

---

## reading the results

- A combo returning 0 results isn't broken — it means that exact intersection doesn't exist for that target. Loosen one operator at a time, don't abandon the whole query.
- If a combo returns thousands of generic results, it's *too* loose — add another `-exclude` term instead of scrolling past pages of junk.
- The goal of chaining operators is always the same: kill the common case, keep the exception.

---

*Part of [bug-bounty-google-dorks](https://github.com/theomkashyap/bug-bounty-google-dorks). See the main README for the full categorized dork list.* 
