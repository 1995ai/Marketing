# Verseflow Content Pipeline Design — AI-Assisted Social Media
> Last Updated: 2026-03-24
> Purpose: 4-level content pipeline (A/B/C/D) for Verseflow social media
> Status: ACTIVE — Matt/Jeff alignment complete 2026-03-24
> Owner: Jeff (execution), Matt (final approval, brand direction)

---

## Guiding Constraints

- **Content CREATION is the bottleneck.** Posting/scheduling is solved. The pipeline must minimize hours spent creating.
- **Every post reviewed before going live** — no exceptions, even Level A. The difference is *how much* review.
- **Brand voice:** Warm, confident, youth-adjacent, never saccharine, never corporate. See `marketing/verseflow/brand/voice-guide.md`.
- **Scripture accuracy is non-negotiable.** AI misquotes Scripture 15-60% of the time. Every verse reference gets human verification before posting.
- **AI disclosure: TikTok only.** All AI-generated visual content on TikTok must be self-labeled or face 73%+ reach suppression. Instagram and Facebook: no disclosure required.
- **Start manual, automate later.** At 24 posts/week, Matt and Jeff post manually while learning the cadence. Buffer automation activates as volume grows (multiple projects, >30 posts/week, or second account).
- **AI voiceover is an option for Reels.** Level C can use AI voiceover (ElevenLabs or similar) as an alternative to recording Matt/Jeff. Decision: per-piece, based on content type.
- **Team:** Matt (final approval, brand direction, scripture curation), Jeff (execution, posting, influencer management), Cowork (AI drafting daytime), Sentinel (overnight batch generation).

---

## Matt/Jeff Alignment Questions — Discuss Today

These need answers before the pipeline can run. Matt and Jeff to align on this call.

| # | Question | Decision |
|---|----------|---------|
| 1 | **Who posts?** | ✅ Jeff posts manually. Buffer activates when new revenue or new project launches. |
| 2 | **Who owns content calendar?** | ✅ Jeff leads calendar structure. Matt async on scripture. Sentinel generates monthly theme suggestions in AI-friendly format. |
| 3 | **Voiceover for Reels** | ✅ Jeff leads, Matt async. AI voiceover (ElevenLabs female voice) is an option — per-piece decision. Matt: evaluate ElevenLabs. |
| 4 | **Who reviews Level B drafts?** | ✅ Cowork designs, Jeff reviews, Matt async. |
| 5 | **Canva templates + watermark** | ✅ Two versions of every static post: one watermarked, one clean. Cowork creates both. |
| 6 | **TikTok timing** | ✅ TikTok when new project launches or significant growth. IG + FB primary now. |
| 7 | **Buffer trigger** | ✅ Same as #1: new revenue or new project. Not volume-based. |
| 8 | **Calendar sync** | ✅ Aligned. Sentinel generates monthly themes. Format TBD by Jeff. |

---

## First Action: Run the Pipeline Once (A/B/C/D Trial)

Before full automation, run one week manually to validate each level works end-to-end.

### Action Items — Week 1 Trial

**Level A Trial (Matt)**
- [ ] Curate 7 days of scripture (can use existing verse list or Sentinel-drafted list for review)
- [ ] Approve one Canva scripture card template (Jeff or Cowork designs)
- [ ] Sentinel generates 7 Level A captions overnight
- [ ] Matt or Jeff manually posts 3 days to IG — check quality, timing, tone
- [ ] Note: what felt off? What worked?

**Level B Trial (Jeff)**
- [ ] Pick one content type: themed carousel or breathing reel
- [ ] Sentinel generates draft overnight (Jeff drops a 1-sentence brief in Telegram)
- [ ] Cowork produces visual (Canva carousel or Kling clip)
- [ ] Jeff reviews in ~10 min, approves or edits
- [ ] Posts manually to IG
- [ ] Note: how long did review actually take?

**Level C Trial (Matt or Jeff)**
- [ ] Pick one Reel concept (e.g., "replace 3 minutes of doom-scrolling with scripture")
- [ ] Send brief to Sentinel via Telegram
- [ ] Sentinel drafts script overnight
- [ ] Matt/Jeff edits + records voiceover (or use AI voiceover — test both)
- [ ] Assemble in CapCut, post manually
- [ ] Note: what needed the most rework?

**Level D Trial (Matt)**
- [ ] Record one 30-sec "why I built this" clip on phone — no script, just talk
- [ ] Cowork adds captions/subtitles
- [ ] Matt posts directly to IG Story or Feed
- [ ] Note: how did it perform vs. AI content?

**After Trial Week:**
- [ ] Matt/Jeff debrief: what's the real time per level?
- [ ] Adjust pipeline based on actual (not estimated) time
- [ ] Decide: keep manual or flip to Buffer?

---

## Level A — Near-Automated (AI creates, one-time template approval)

**What it is:** Templated content where the *format* is pre-approved and only the *variable* (scripture, date, theme) changes. Matt approves the template once. After that, AI fills the template and schedules it.

### Content Types

| Content Type | Cadence |
|---|---|
| Daily Scripture Quote Card | 7x/week |
| "Verse of the Day" Instagram Story | 7x/week |
| Weekly Sabbath Reminder | 1x/week (Saturday) |
| App Feature Tips | 2x/week |

### How It Works

1. **Template Approval (one-time, ~2 hours):** Matt and Jeff approve 4-5 Canva templates. Lock fonts, colors, layout. Save as Canva Brand Templates.
2. **Overnight Generation (Sentinel, 11pm):** Pulls next day's verse from scripture calendar, generates caption, writes to `vault/staging/social-queue/`
3. **Morning Review (Jeff, ~5 min/day):** Scans for anything off. Posts manually or approves for Buffer.

### Time
- One-time setup: 2-3 hours
- Weekly ongoing: ~15-20 minutes

---

## Level B — AI Creates, Human Approves (1-3 min review per piece)

### Content Types

| Content Type | Cadence |
|---|---|
| Themed Scripture Carousel (3-5 slides) | 2x/week |
| Breathing Exercise Reel (AI B-roll) | 2x/week |
| Weekly Recap Story | 1x/week (Sunday) |
| Motivational Quote Cards | 2x/week |
| Facebook Group Discussion Prompts | 2x/week |

### How It Works

1. Sentinel generates batch Sunday night → writes to `vault/staging/social-queue/`
2. Monday morning review (Jeff/Matt, ~30 min): scripture accuracy check + brand voice spot-check
3. Cowork produces visuals (Canva static, CapCut for video), loads into Buffer or delivers to Jeff for manual posting

### AI Disclosure
- **TikTok only** — label AI video content. Instagram/Facebook: no disclosure required.

### Time
- Weekly review: 30-45 minutes Monday morning

---

## Level C — AI Drafts, Human Significantly Edits

### Content Types

| Content Type | Cadence |
|---|---|
| Instagram Reels (scripted) | 1-2x/week |
| Blog/Long Caption Posts | 1x/week |
| Email Newsletter Content | 1x/week |
| Church Outreach Social Content | As needed |

### Voiceover Options (Per Piece Decision)

| Option | When to Use |
|---|---|
| Matt records | Personal testimony, founder content, anything that needs his specific voice |
| Jeff records | Day-to-day Reels, behind-the-scenes, execution content |
| AI voiceover (ElevenLabs or similar) | When neither Matt nor Jeff has time, or for content that doesn't need a specific human identity (breathing exercise narration, inspirational overlays) |
| Text overlay only (no voiceover) | Short Reels where text does the job |

**Rule:** If the content is about a personal story or building the product → human voice. If it's instructional or ambient → AI voiceover acceptable.

### How It Works

1. Matt/Jeff writes 1-2 sentence brief → Telegram to Sentinel
2. Sentinel drafts overnight (or Cowork drafts live during day)
3. Human edits (15-30 min per piece): rewrite generic sections, add personal details, confirm voiceover approach
4. Assemble in CapCut, post manually or queue in Buffer

### Time
- Per piece: 15-45 minutes
- Weekly total: 1-2 hours for 2-3 pieces

---

## Level D — Fully Human (AI assists logistics only)

### Content Types

| Content Type | Cadence |
|---|---|
| Personal Testimony / "Why I Built This" | 1-2x/month |
| Live Q&A | 1x/month |
| User-Generated Content Reposts | As available |
| Behind-the-Scenes / Build Updates | 1-2x/month |
| Influencer Collaboration Content | Per influencer cadence |

### AI Role (Logistics Only)
- Sentinel: flags UGC to repost, identifies trending topics for timing
- Cowork: adds captions/subtitles to recorded video, formats for platform

### Time
- Per piece: 30 min to 2 hours
- Monthly total: 4-6 hours for all Level D content

---

## Weekly Volume and Time Summary

| Level | Posts/Week | AI Hours | Human Hours |
|---|---|---|---|
| A | 14-16 | ~2 (Sentinel overnight) | ~0.5 (Jeff spot-check) |
| B | 7-9 | ~3 (Sentinel + Cowork) | ~1 (review) |
| C | 2-3 | ~1.5 (drafting) | ~1.5 (editing + voiceover decision) |
| D | 1-2 | ~0.5 (logistics only) | ~1.5 (creation) |
| **Total** | **24-30** | **~7** | **~5** |

**At 24 posts/week: post manually.** Learn the cadence. Buffer activates when volume grows or a second project/account is added.

---

## Weekly Content Calendar

| Day | Level A | Level B | Level C | Level D |
|---|---|---|---|---|
| Monday | Scripture Card + Story | Motivational Quote | — | — |
| Tuesday | Scripture Card + Story | Themed Carousel | Scripted Reel (if scheduled) | — |
| Wednesday | Scripture Card + Story + App Tip | FB Discussion Prompt | — | — |
| Thursday | Scripture Card + Story | Breathing Exercise Reel | Long Caption Post | — |
| Friday | Scripture Card + Story + App Tip | Motivational Quote | — | — |
| Saturday | Scripture Card + Sabbath Reminder | — | — | Personal/BTS (if scheduled) |
| Sunday | Scripture Card + Story | Weekly Recap | Email Newsletter | Live Q&A (monthly) |

---

## Approval Workflow

```
Sentinel (overnight) → vault/staging/social-queue/
                               ↓
         Morning Brief (6:45am) — count + flagged items
                               ↓
       Matt/Jeff review (Telegram or vault, ~30 min Monday)
                               ↓
   Approved → Cowork produces visual → Jeff posts manually (or Buffer)
   Edit needed → Cowork revises → re-review
   Rejected → Sentinel logs to learnings.md
```

---

## Buffer — Activate When

Buffer Essentials ($6/channel/month) stays on standby until:
- Volume exceeds 30 posts/week consistently, OR
- Second project or account added (Henryedu, HammerGolf), OR
- Matt/Jeff manual posting is taking >3 hours/week

When activated: $24/month for 4 channels (IG, FB, TikTok, YouTube).

---

## Implementation Sequence

### Phase 1 — This Week (Setup)
- [ ] Matt/Jeff alignment conversation (questions above)
- [ ] Matt curates first 7-day scripture list
- [ ] Jeff + Cowork design 4-5 Canva templates
- [ ] Run Level A/B/C/D trial (one of each, manually)
- [ ] Debrief: adjust time estimates + cadence

### Phase 2 — Week 2 (Level A Running)
- [ ] Sentinel generates Level A content nightly
- [ ] Jeff reviews and posts manually each morning (~5 min)

### Phase 3 — Week 3 (Add Level B)
- [ ] Sentinel generates weekly Level B batch Sunday night
- [ ] First Kling 3.0 B-roll clip
- [ ] Monday review cadence established

### Phase 4 — Week 4 (Full Pipeline)
- [ ] Level C Reel with voiceover (test AI voice vs. human)
- [ ] Full cadence running
- [ ] First analytics capture

### Phase 5 — Month 2+ (Steady State)
- [ ] Buffer decision based on actual volume
- [ ] Analytics → prompt refinement loop active
- [ ] Content examples library seeded with top performers

---

## File Structure

```
Marketing/verseflow/content/
  content-pipeline.md          ← this file
  content-calendar.md          ← monthly content plan (create when ready)
  scripture-calendar.md        ← 30-day curated verse list (Matt maintains)
  prompt-library.md            ← AI generation prompts per type
  analytics/                   ← weekly + monthly performance summaries
  published/YYYY-MM/           ← archive of published drafts
  examples/                    ← top-performing content for AI reference

vault/staging/social-queue/    ← Sentinel overnight output (cleared after Cowork processes)
```
