# Playbook: Research, Positioning, SEO and Distribution

Internal document for maintaining and growing this repository. Snapshot: September 2026.

---

## 1. Research findings

### 1.1 The market is crowded on quantity

Large curated lists already exist, and competing with them on count is a losing strategy.

| Existing list | Approx. size / signal (Sep 2026) | Angle |
|---|---|---|
| anthropics/skills | ~179k stars | Official source, not a directory |
| VoltAgent/awesome-agent-skills | ~29.6k stars, 1,000+ skills | Official vendor skills plus community |
| BehiSecc/awesome-claude-skills | ~9.9k stars | Categorised community list |
| ComposioHQ/awesome-claude-skills | Large, app-integration focus | Composio integrations |
| travisvn/awesome-claude-skills | Claude Code focus | Early list |
| hesreallyhim/awesome-claude-code | Broad Claude Code resources | Not skills-only |
| clskills.in / agentskill.sh | 2,300 to 69,000+ skills | Scraped directories |

**Conclusion:** the gap is not "more skills". It is *trustworthy selection*.

### 1.2 The real pain (evidence)

1. **Most public skills do not help.** One tester installed all 47 skills from a popular collection and found 40 made output worse than vanilla Claude Code. Skills that restate what the model already does add tokens and narrow output.
2. **Skills fail silently.** Independent studies reported non-invocation around 56% (Vercel), a 50% success rate, and 77% activation over 650 samples. Directive-style descriptions reportedly raised activation sharply.
3. **Security risk is real.** Snyk's audit of 3,984 skills on public hubs (Feb 2026) found 13.4% with critical issues and 76 confirmed malicious payloads. A coordinated malware campaign ("ClawHavoc") targeted Claude Code and OpenClaw users.
4. **Budget overflow.** The combined skill description budget defaults to about 15,000 characters; beyond that, skills are silently dropped.
5. **Stale rankings.** Star counts in popular articles are months out of date; they reward popularity, not usefulness.
6. **What works:** Anthropic has said verification skills have had the most measurable impact internally. Durable "encoded process" skills (Superpowers, Karpathy guidelines, grill-me) outlast "capability uplift" skills that new models absorb.

### 1.3 Demand signals

- Superpowers: reported at roughly 265k stars (Aug 2026).
- forrestchang/andrej-karpathy-skills: 210k+ stars reported, still among top weekly gainers.
- mattpocock/skills: ~1.3k stars in a single week on star-history's leaderboard.
- Official vendor teams (Vercel, Cloudflare, Stripe, Sentry, Flutter, Firebase, Microsoft, HashiCorp, Trail of Bits) now ship skills, which confirms durable demand.
- Search demand: many 2026 listicles target "best Claude Code skills", "awesome Claude skills", "Claude skills GitHub", confirming search volume on these phrases.

### 1.4 ICP (ideal customer profile)

| Segment | Who | Pain | What they want from us |
|---|---|---|---|
| **Primary** | Developers using Claude Code, Codex or Cursor daily; indie founders; small-team tech leads | Burned by bad or silent skills; no time to test 50 repos | A short, trusted "install these" list with exact commands |
| **Secondary** | Engineering managers and security leads | Need an approved allowlist for their team | Scores, security gates, licence notes, re-review dates |
| **Supply side** | Skill authors and vendor DevRel teams | Want discovery | A clear, fair scoring path (drives PRs, backlinks, shares) |

### 1.5 About the "150 skills above 95" target

Scored honestly, very few skills clear 95. This list has **21 Tier S skills (≥95)** and **172 Tier A/B skills (75 to 94)**, 193 in total. Inflating scores to hit 150 would destroy the one thing that differentiates this repo: trust. Keep the bar and let the tiers carry breadth.

---

## 2. Positioning

**Name options** (include the high-volume phrase "claude skills"):
- `verified-claude-skills` (recommended)
- `claude-skills-scorecard`
- `awesome-claude-skills-verified`

**One-line description for the GitHub "About" box (keep under ~120 chars):**
> Scored, security-checked Claude Skills for Claude Code, Codex and Cursor. Install commands for 190+ free Agent Skills.

**Tagline:** "Install fewer skills. Install the right ones."

---

## 3. GitHub and search-engine setup

### 3.1 Repository settings
- **Topics** (up to 20): `claude-skills`, `claude-code`, `claude-code-skills`, `agent-skills`, `awesome-list`, `awesome`, `anthropic`, `claude`, `skill-md`, `ai-coding-agent`, `mcp`, `codex-skills`, `cursor`, `gemini-cli`, `developer-tools`, `ai-agents`, `prompt-engineering`, `llm`, `security`, `devtools`.
- **Social preview image** (Settings, 1280×640): title, "193 scored skills", a Tier S visual.
- **Website field:** link to the GitHub Pages site.
- Pin the repo on your GitHub profile.

### 3.2 README structure (already applied)
- H1 contains the main phrase: "Claude Skills", "Claude Code", "2026".
- First paragraph states what, who, and which agents, in plain language.
- Question-style FAQ headings match how people search.
- One H3 per Tier S skill creates linkable anchors (`#2-systematic-debugging-97`).
- Short keyword line at the end. Do not add more; keyword stuffing violates Google's spam policies.

### 3.3 GitHub Pages site (more search control)
- Enable Pages from `/docs` or a `gh-pages` branch with a simple static generator (Jekyll is native to Pages).
- One page per category and one per Tier S skill, each with a unique title and meta description.
- Add `sitemap.xml` and `robots.txt`; submit to **Google Search Console** and **Bing Webmaster Tools** (Bing also feeds several other engines).
- Add FAQPage structured data on the FAQ page only if it mirrors visible content.
- Set a canonical URL per page; keep the README as the canonical for the repo itself.

### 3.4 Freshness (a ranking and trust signal)
- The included `.github/workflows/link-check.yml` checks every link weekly and opens an issue when links break.
- Update the "last reviewed" badge on each quarterly re-score and write a short `CHANGELOG.md` entry (what moved tiers and why).
- Publish a quarterly "State of Claude Skills" post summarising changes; it gives people a reason to link back.

---

## 4. Distribution plan (policy-safe)

| Week | Action | Rules to respect |
|---|---|---|
| 0 | Publish repo; write a long-form article on your blog or Medium ("I scored 193 Claude skills; 21 passed") linking to the repo | If republishing on Medium, set the canonical link to your original post |
| 1 | Post on X and LinkedIn with the key finding (most skills hurt output; here's what works) | Share findings, not just a link |
| 1 | Reddit: r/ClaudeAI, r/ClaudeCode and relevant language subs, as a genuine write-up | Read each subreddit's self-promotion rules; disclose it's your project; engage in comments; don't cross-post the same text everywhere |
| 2 | Show HN, only once the repo is solid | Never ask for upvotes; HN penalises vote solicitation |
| 2 | Open PRs to add the repo to existing lists (e.g., the "Collections" sections of other awesome lists) | Follow each list's CONTRIBUTING rules exactly; one PR per list |
| 3+ | Notify vendor teams whose skills scored Tier S (a polite issue or social mention) | No spam, no mass tagging |
| Ongoing | Answer "which skill should I use" questions on forums with a specific answer, linking only when relevant | Helpfulness first |

**Submitting to sindresorhus/awesome:** only after the list meets that repo's current guidelines (it runs `awesome-lint` and has age and quality requirements). Read the guidelines at submission time.

---

## 5. What not to do (policy and reputation)

- **Never buy stars, trade stars, or use bots.** GitHub's Acceptable Use Policies prohibit inauthentic activity; fake stars get removed and can get accounts restricted.
- **No spam issues or PRs** on other repos to promote this one.
- **No affiliate links or paid placements** without clear disclosure. Recommended: none at all.
- **Don't imply Anthropic endorsement.** Keep the "not affiliated" line; don't use Anthropic logos.
- **Don't copy source-available skills** (docx, pdf, pptx, xlsx) into the repo. Link only.
- **Don't auto-generate hundreds of thin pages.** Scaled low-value content violates Google's spam policies and undermines trust.
- **Don't include skills you haven't checked** against the hard gates.

---

## 6. Scoring methodology (detail)

**P: Real pain solved (40)**
- 35 to 40: Fixes a frequent, costly agent failure (false completion, symptom-only fixes, insecure code, broken payment flows) and defines success criteria the model doesn't know.
- 28 to 34: Clear improvement on a common task.
- Under 28: Mostly restates model defaults or serves rare tasks.

**D: Demand signal (35)**
- Maintainer: official vendor team or proven author (up to 12).
- Adoption: stars, installs, forks, mentions in independent reviews (up to 13).
- Activity: commits and releases in the last 90 days (up to 10).

**I: ICP fit (25)**
- Clear weekly user (up to 10).
- Free to use or free with a standard account (up to 8; 🔑 skills lose 1 to 3).
- Specific, reliable trigger description (up to 7).

**Hard gates:** maintained within ~90 days; source repo identifiable; no obfuscated scripts or unexplained network calls; no instructions to hide actions from the user.

**Re-scoring:** quarterly, plus on any security report. Each change gets a CHANGELOG line.

---

## 7. Metrics to track

- Stars and forks per week (GitHub Insights → Traffic).
- Referrers and popular content (Insights → Traffic).
- Search Console impressions and clicks for the Pages site.
- Inbound PRs from skill authors (supply-side health).
- Broken-link issues opened by the workflow (maintenance health).

---

## 8. Sources

- ksred.com: "Best Claude Code Skills: Which Are Actually Worth It" (Aug 2026), summarising Shcheglov's testing, Snyk's ToxicSkills audit, activation studies and the description budget.
- anthropics/skills README and repository listing.
- obra/superpowers README and skills directory.
- VoltAgent/awesome-agent-skills README (official vendor skills).
- BehiSecc/awesome-claude-skills README (community skills).
- vercel-labs/agent-skills README.
- mattpocock/skills README.
- docs.flutter.dev/ai/agent-skills; firebase/agent-skills README.
- star-history.com weekly leaderboard; OSS Insight trending.
- firecrawl.dev: "Best Claude Code Skills for Developers in 2026".
