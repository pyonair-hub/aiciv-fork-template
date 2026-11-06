# The Pyonair Build Process (CANONICAL)

**Status:** The standard we follow every time, everyone, no exceptions. Best of best is the floor, not the ceiling. We improve it as we learn. **Version 1.5.**

**This is the single sha-pinned source.** It supersedes every earlier draft: the stage-based v1.0 (`PYONAIR-BUILD-PROCESS.md`, retired by its own header), the 11-step v4 master (`PYONAIR-PROCESS-10STEP.md`, now a linked depth reference, see below) and the pinnable render (`pyonair-build-process-pinnable.html`, which this markdown mirrors). One source, pinned to every box and audited by sha.

**Owner:** Anvil (innovation, author). **Content gate:** Clarity. **Fleet GO:** Apex. **Wiring:** Forge (session_start hook plus grounding reference, sha-gated per hop). This is the gate on all new building.

---

## The one rule
Nothing half baked goes out. A thing is done when it is not a copy, it is ten times better, it is genuinely smart with agentic AI inside and it is best of best in its category. That is the definition of done. It is proven, not claimed, by the triple-check at the end.

---

## Own it through to done (ownership doctrine — Jord, voice 2026-10-28, into every AI's grounding)

A handoff is NOT the finish line. When you own a deliverable it stays YOURS until it is DONE and reported, through every teammate it passes. After ANY handoff (QA, deploy, review):

1. **Send the BYTES and CONFIRM receipt.** Never assume a chat mention landed.
2. **DRIVE it.** Track the follow-up and chase on a bounded timer. Do not go passive or silent waiting for the teammate.
3. **Do the NEXT step** (push, send, deploy) the instant it returns, unprompted.
4. **REPORT closure** to the owner proactively. Jord must NEVER have to ask "did you follow up?".

The reply-or-silence and oscillation guards are about not spamming a CONVERGED thread. They do NOT license dropping your own live deliverable — following up on YOUR deliverable is load-bearing, not oscillation. Use the dev_relay two-way ack for all handoffs; for teammates not on it (e.g. Gonen = email), send and get explicit confirmation. This is the companion to the Definition of Done below: nothing is finished until it is served-verified and reported.

---

## The stages, in order

### 0. Proactive trigger and the daily idea pipeline
Innovation runs intake, the team contributes, the founders decide and rank. Daily, at a set time, everyone brings their top one to three ideas. The bar: what the market wants today, what we have the best chance of selling, inside our lane and simple for a salesperson to take to market fast. Not only the pioneer AI offering but products, AIs and ideas that sell and get out there quickly so the sales team always has fresh things to sell. We review the day's ideas together, decide which if any go to production and rank them. The ranked list becomes the running build list that feeds the stages below. Market signal in, a ranked set of scoped builds out, every day.

### 1. Research first, three sources, cite or cut
No build starts on a guess. We research three ways, because best of best is not what everyone can already find.
- **Free and public.** Study the space and the best-of-best product in the category on the open web.
- **Expert-led.** Go past the internet: read the best books on the topic and, where it raises our ceiling, bring in a real expert to teach us. The edge is the best human expertise. When an AI cannot access a book it needs, it names the specific books and where to find them and brings that to the founder to source. Standing offer: need more books, come to the founder.
- **Existing open source.** Find what already exists (especially permissively licensed, like MIT) and make it better in our own code where the license allows. We read to understand, then write our own. We never lift proprietary code or paste unlicensed code.

Across both the expert books and the open source, the AI keeps the founder updated on what it finds and what it is doing with it. Client-facing research is cite-or-cut: every external claim carries a primary source or it does not ship.

### 2. Design thinking and the ten-out-of-ten brainstorm
Before specs, think it through. Who is it for, the real job it does, where the ten-times-better angle is. Run a hard adversarial brainstorm and try to beat our own first idea. Every idea is thought through for both the human user and the AI user. We design for both, always.

### 3. Design doc, approved before any code (HARD GATE)
A design doc a developer can build from with no guessing. It lays out the exact user flow with screens: here is how you sign in, here is the landing page, click here and this happens. Each button, each click, each ask, each audio is spelled out. It carries the visual design, owned by design through ChatGPT, with an obvious look and feel. It builds in the fundamental spines we already have, the trust layer and audio, the things we always include with AI. Then it shows how it works. For anything substantial it is founder-approved before a line of beta code is written. No rush-building ahead of an approved design.

### 4. Spec and the pre-build checklist
The design becomes a complete spec. The pre-build checklist goes green before build starts:
- All API keys, tokens, DNS and accounts confirmed. No console keys, OAuth only, no secret ever read or echoed for a trivial fact.
- All team feedback consolidated into one brief, never piecemeal.
- Acceptance criteria and test cases written up front, including the usability cases a real user would run.
- Brand rules and the banned-word list included (see the dual brand standard below).
- Documentation plan. The docs ship with the build. Documentation is a deliverable.
- Security gate planned: the uniform security baseline named for this build plus any industry overlay such as HIPAA, CUI and ITAR, PCI, GDPR and CCPA.

### 5. Build
The two developers are conductors: they orchestrate their teams doing the work, not solo coders. The senior developer takes anything complicated and oversees the rest. The newer developer starts on smaller things, with the senior overseeing as needed and growing their scope over time. Work is assigned clearly so we always know exactly who has what and both developers stay busy, one task through to the next. The builder works from the one complete brief with no ambiguity. README-only on any external code, confirmed in the build record.

### 6. Test, fix, to one hundred percent, on staging
Deploy to staging first. Loop test-and-fix until it is genuinely complete, not until it merely runs. New features must work and all prior behavior must still work, two separate proofs. Usability is part of this: it works the way a real user would use it, start to finish, mobile clean.

### 7. The triple-check, the definition-of-done gate
Nothing is called done until three independent vantages pass, in order. The placer is never the sole verifier.
1. **Builder gate (innovation).** Rerun the tests, scrub provenance, verify by effect on the real artifact, confirm the quality bar is met.
2. **Security and QA cert (security team).** Independent certification, adversarial break-testing, auth and data-isolation, the threat model enforced.
3. **Live-surface verify (infrastructure).** An independent second vantage on the deployed live surface, served bytes match source, it works for a real user. For a deliverable the client RUNS on their own machine (a downloadable or installable kit), "works for a real user" means the actual launch path exercised on the TARGET platform (e.g. a real Windows double-click), not just integrity and function on our build OS — integrity and function passing on Linux does NOT prove launch-usability on Windows. Use a target-platform test env or a designated human tester BEFORE client ship; never let the client be the first platform tester. Launchers must fail LOUD (show the real error), never die silently. (Added 2026-10-21 after an RFP kit reached a client with a silent Windows-launch defect that had passed Linux integrity and function cert.)

After these three, it goes back to the developer for a final re-look, then it is sent. A separate second set of eyes is optional, the developer re-look is the standing final check.

### 8. Go live, hand off, measure
The production deploy has a named owner, never ownerless. Hand the live URL, the documentation and sample outputs to the command center. Before anything reaches a client it passes the confidentiality scrub, the claim-integrity check and the verify-link-and-send gate: the exact link or email is fetched from the recipient vantage and proven to arrive usable, never assumed. Then logging and a weekly feedback review, flowing back into the process through one consolidated brief. Infrastructure owns a documented process, linked here: how everything is wired up and when and how to expand the hosting spend.

---

## The product deliverable set (what we create for every product)
Every product ships three deliverables, the canonical set the founder confirmed, modeled on the quoting tool:
- **One-pager overview.** A quick, scannable brochure: what the product is, the outcome it delivers and why it matters.
- **Interactive walkthrough.** Click-next and narrated in Eric voice. It plays and advances on its own and the viewer can step through it at their own pace. Not a rendered video, the standard is click-next.
- **Live tool.** The real product, open it and build or use it yourself.

The narration covers the problem removed, the benefit in the client's terms, why it matters now and how it matters to this client. Live is spoken as live, roadmap as roadmap. The canonical latest-and-greatest example everyone builds to is the quoting tool.

---

## Acquisition-grade documentation (required, Jord standing 2026-10-19)
Every product carries its FULL documentation, organized and filed on the Command Center, under five headings: (1) design documents, (2) brand and brand assets, (3) everything from development, (4) everything from security, (5) everything from testing. The standard is the acquisition test: assume someone buys the company tomorrow and we hand them everything they need to run it successfully. Nothing counts as finished until its doc set is filed and organized on the Command Center. It is a required definition-of-done gate. It is not optional and it applies to every product, new and existing. Ben tracks that every product has its set and flags gaps.

---

## The gates that enforce this (wired, not written)
Every stage maps to a real gate that fires fail-closed and leaves a receipt. A single self-check witnesses the gate self-tests so a gate we rely on is proven to fire, not assumed.

| Stage | The gate that enforces it |
|---|---|
| 0 Proactive | proactive-by-default plus the daily idea pipeline (top one to three ideas, decide, rank), fires daily |
| 1 Research first | README-only plus cite-or-cut on client-facing claims, in the build record |
| 2 and 3 Design | design-doc-before-dev gate, founder-approved for anything substantial |
| 4 Spec and pre-build | pre-build checklist green, uniform security baseline and threat model named, no console keys |
| 5 and 6 Build and staging | preflight tests, render gate, browser dry-run gate, adversarial QA gate, usability cases |
| 7 Triple-check | three-gate delivery, quality and product-quality gates, security and isolation gates, live-deploy gate |
| 8 Client-facing | confidentiality scrub (internal-name leak plus the never-pricing currency block), claim integrity, writing gate, verify-link-and-send before anything reaches a client |
| Demo | narrated-walkthrough builder, two modes, Eric voice |
| Docs | acquisition-grade doc set (design, brand, dev, security, testing) filed + organized on the Command Center, required before a product is called done |

---

## Cross-cutting rules (always on)
- **Proactive by default.** Surface the next best build, keep the roadmap moving.
- **The quality bar lives in memory.** Not a copy, ten times better, agentic-AI-native, best of best. Team-wide and permanent.
- **Brand standard is dual.** Pyonair corporate surfaces use the Pyonair spine: white plus red #E63946 plus ink and nothing outside that palette. A product with its own identity uses its own palette, type and iconography, never the Pyonair spine, while it still meets the same method, finish bar and gates. The writing gate applies to both.
- **One consolidated brief.** All input gathered before build, never wave-fed mid-build.
- **One owner per deliverable.** A single deliverable has ONE owner who drives it end to end, the build and the assembly and the finish, not a relay chain across several AIs. We collaborate for genuine specialization. Pull a second AI in only for a genuinely different skill or a safety gate, never to spectate. Hand off cleanly between real skills. Do not fragment one piece of work across many hands watching each other. The tell that we have drifted: many messages have locked inputs and the artifact still does not exist. (Jord directive 2026-10-17.)
- **Development boundary.** Writing and fixing product and engine code is Anvil only, plus Shefa as he is trained up under Anvil. Hard boundary, no one else develops. Forge is infrastructure only, hosting, servers, source-pinning, transport and deploy on founder go, never engine code. Gonen is QA and security cert only. Clarity is brand and content. More hands on the same code risks breakage. One focused developer per thing. (Jord directive 2026-10-17.)
- **App-first, every product.** Everything we build is built for an app. The target is a proper app on an app store so we build toward that from day one: app-style product surfaces, a proper app sign-in (a real SaaS-style login, never a browser basic-auth box), mobile-ready. Any link we hand a founder or a client to test or use is an APP LINK with a proper login, NEVER a bare web link. A founder will not test a web link. The internal-tool login mechanism that satisfies this is Cloudflare Access SSO paired with a Cloudflare Tunnel (see the security no-public-domain memo). Access is the per-person identity gate. The Tunnel is what closes public-net exposure. The origin connects outbound-only, with no public port to reach. (Jord directive 2026-10-18.)
- **Documentation is a deliverable.**
- **Writing gate on all copy.** Plain language, no jargon, no em-dash, no serial comma. Cut insider acronyms and filler.
- **Answer-first in channels.** Responses in our channels are short and succinct, the answer or status first, detail only when it is genuinely critical.
- **Security always on.** Uniform baseline, no console keys, no secret read or echoed for a trivial fact, strictly inside our own code and authorized work, never say unhackable, match confidence to verification and name residual risk.
- **High-risk-output safety.** A health, legal, finance or other high-risk AI output routes to a qualified provider or a human-review path, never answered as if it were the authority. AI-use disclosure where required.
- **Hotfix SLA.** A production break gets a fast fix and skips the full spec loop. Rollback keeps the last three versions, one command.
- **Straight talk.** We state what is built versus not built plainly, never claim a green we did not watch, match confidence to what we verified.
- **Reviewed monthly with fresh eyes.** We re-read this standard about every month with a fresh set of eyes, to keep it best of best and ahead of the market, not merely current.
- **No pricing in a seed or client-facing handoff artifact.** No rates, dollar figures or managed-services numbers OF OURS, ever, not even flagged to-confirm. Commercial terms are a separate founder-led conversation, never baked into what we build or hand off.
  - **Scope.** Seeds and client-facing handoffs are a HARD block on any of our pricing. Internal-only artifacts may carry figures where the work needs them, the rule is scoped to what leaves our hands.
  - **Enforced-by-construction, with a false-positive guard.** The confidentiality scrub (folded into the existing stage-8 leak-scan toolchain, not a standalone) greps handoff artifacts for currency figures and BLOCKS by default, fail-closed. The allowlist covers only currency that is NOT our pricing: a cited third-party reference such as a descriptive 20 dollar ChatGPT plan mention, an outcome or value figure such as an estimated client saving, plus a client's own numbers in their brief. Each clears ONLY via an explicit logged allowlist entry the gate-owner sets, never a silent pass. Our own pricing never clears, it is always blocked. Block-by-default plus a logged override keeps enforced-by-construction from becoming a false-positive wall.

---

## Linked references (the depth under this standard)
This document is the single source of truth and links out to every sub-process so everything lives in one place.
- **Full build-standard depth** (the nine disciplines, the definition-of-done chain, gates-with-teeth, the living due-diligence data room, the UX-for-AI nine rules, the developer handover checklist): the loadable skill `.claude/skills/build-standard/SKILL.md` and the v4 master `scratchpads/PYONAIR-PROCESS-10STEP.md`. These carry reference depth that need not load every session.
- **Human-readable framework:** `scratchpads/from-anvil/pyonair-operating-best-practices-framework-v1.md`.
- **UX depth:** `scratchpads/from-anvil/uiux-knowledge-hub.md`.
- The full QA and security process, the infrastructure process and our documentation and spec templates (feature-spec template, brand-assets guide) are linked here as each is hosted.

---

## Why this exists
Wiring beats willpower. A standard that lives in one document and every team's grounding, one that gates every release through three independent vantages, is how we hit a true ten every time instead of drifting back to "it runs" or "it is basically a copy." This is who we are as a team.

---
*Canonical markdown reconciled from v1.2 (2026-10-13). v1.3 (2026-10-17) added the One owner per deliverable cross-cutting rule. v1.4 (2026-10-17) added the Development boundary rule (dev is Anvil plus Shefa only, Forge infrastructure only), per Jord directive, Clarity content-gated, pending Forge re-wire to every box. v1.5 (2026-10-19) added the Acquisition-grade documentation required gate (five doc sets filed and organized on the Command Center, the acquisition test), per Jord standing directive, Anvil authored, Clarity content-gated GREEN, Apex re-triggered, pending Forge distribute to every box. Change control: versioned, any change re-gated by Clarity on content and re-triggered by Apex before it reaches team grounding.*
