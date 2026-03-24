# Kling AI Video Tool — Plan Recommendation + Jeff Setup Guide
Last Updated: 2026-03-23

---

## Part 1: Plan Recommendation (For Matthew's Decision)

### Pricing Overview

Kling AI uses a credit-based subscription model. No unlimited generation on any plan.

| Plan | Monthly Cost | Credits/mo | ~Videos (standard 5s, 1080p) | Watermark |
|------|-------------|------------|------------------------------|-----------|
| Free | $0 | 66/day (no rollover) | ~6/day | Yes |
| Standard | $10 | 660 | ~33 | No |
| Pro | $37 | 3,000 | ~150 | No |
| Premier | $92 | 8,000 | ~400 | No |
| Ultra | $180 | 26,000 | ~1,300 | No |

Annual billing saves ~34% on Ultra, 6-7% on lower tiers.

**Hidden costs to know:**
- Higher quality modes (cinematic, longer clips) burn 1.5-2x credits per generation
- Failed generations still consume credits — no refund system
- Credit top-ups are expensive: ~$10-15 per 100 credits

### Team / Multi-Seat Access

**No native team plan exists.** Pro and below are single-user. Options for a 2-person setup:

1. **Shared single account** — One Pro or Premier login shared between Jeff and Cowork automation. Simplest, cheapest. Kling TOS does not explicitly prohibit account sharing, but it is a gray area.
2. **Two separate subscriptions** — Clean separation but doubles cost. Two Pro plans = $74/mo.
3. **Enterprise/custom** — Kling offers a questionnaire for custom pricing, but this is designed for larger orgs. Likely overkill for a 2-person team.

### API Access (For Cowork/Claude Integration)

**Yes, Kling has a developer API.** Key details:

- Access at `app.klingai.com/global/dev`
- Authentication: JWT (JSON Web Token) using access key + secret key
- Supports text-to-video and image-to-video
- Asynchronous workflow: submit prompt, get task_id, poll for result
- Rate limit: ~5 parallel jobs per API key
- API credits draw from the same subscription pool (no separate API pricing tier documented)

**Integration path for Cowork:** Generate API key, store in env vars (never in vault), Cowork submits prompts via API, polls for results, downloads completed videos for Jeff's review before posting.

### Recommendation for 2-Person Team

**One shared Pro account ($37/mo) to start.** Here is the reasoning:

- 3,000 credits/mo = ~150 standard videos. Enough for initial content pipeline ramp.
- Jeff uses the web UI for manual creation and experimentation.
- Cowork uses the API key for automated/batch generation.
- Both draw from the same credit pool, which is fine at this volume.
- Upgrade to Premier ($92/mo) only if you are consistently hitting credit limits.

If you want clean separation (Jeff's experiments vs. Cowork production), two Standard accounts ($20/mo total) is an alternative, but you lose the higher credit pool and 1080p is still available on Standard.

**My recommendation: Start with one Pro account at $37/mo. Reassess after 30 days of actual usage data.**

### Privacy / Data Terms — Faith Brand Considerations

This is the section that matters most. Be direct about the risks:

**Content rights:** You retain copyright on paid plans. However, you grant Kling (parent: Kuaishou, Beijing) a worldwide, royalty-free, sublicensable license to use, store, reproduce, modify, and display your content for "service improvement" — which includes AI model training.

**Data sharing:** Kling can share data with affiliates and third-party vendors. Content uploaded is treated as non-proprietary and non-confidential under their terms.

**Data residency:** Processing occurs on servers that may be located in China. Kuaishou is subject to Chinese data laws.

**Privacy tiers:** Free tier generations may appear in public community feed. Pro and above offer private generation mode.

**What this means for VerseFlow:**
- Generated spiritual/faith content will likely be used to train future Kling models. A verse visualization you create could influence outputs other users get.
- Do NOT upload proprietary brand assets, unreleased app screenshots, or anything confidential as reference images.
- For generic atmospheric/spiritual content (sunsets, nature, abstract visuals), the risk is low — these are not proprietary.
- For anything with VerseFlow branding or unique IP, generate locally or use a tool with stronger data isolation.

**Bottom line:** Acceptable for atmospheric B-roll and generic spiritual visuals. Not appropriate for proprietary brand content or anything you would not want a Chinese tech company to have access to.

### Kling 3.0 vs. Google Veo 3.1 — Brief Comparison

| Dimension | Kling 3.0 | Google Veo 3.1 |
|-----------|-----------|-----------------|
| **Price (comparable tier)** | $37/mo (Pro, ~150 videos) | $19.99/mo (AI Pro, ~90 videos) or $0.15-0.40/sec API |
| **Quality** | Strong realism, good motion physics | Superior cinematic polish, native audio generation |
| **Max duration** | 15 seconds per generation | 8 seconds per generation |
| **9:16 vertical** | Native support, no crop needed | Supported |
| **Privacy** | Broad license, Chinese data residency | Google's standard data policies, US/EU data residency |
| **Team access** | No native team plan | Ultra plan ($249.99/mo) has team Flow access |
| **API** | Yes, JWT-based, straightforward | Yes, per-second billing |
| **Best for** | Volume production, predictable billing | High-fidelity hero content |

**For VerseFlow's use case (volume short-form spiritual content on a budget), Kling wins on price-to-volume ratio.** Veo 3.1 produces better cinematic output but the 8-second limit and higher cost make it less practical for batch content creation. If you ever need a single stunning hero clip, Veo is worth the per-second cost.

**Privacy edge goes to Veo** — Google's data handling is governed by US/EU law, no Chinese data residency concern.

### Decision Needed

1. **Approve Kling Pro ($37/mo) as the primary video tool?** Y/N
2. **Acceptable to use Kling for generic atmospheric content, keeping proprietary brand assets off-platform?** Y/N
3. **Want Cowork API integration built?** Y/N (can be Phase 2)

---

## Part 2: Setup Guide + Cheatsheet (For Jeff)

### Account Setup (10 minutes)

1. Go to [klingai.com](https://klingai.com) and click Sign Up
2. Create account with Google, Apple, or email (use the team email if you have one)
3. Navigate to Membership and select the **Pro plan** ($37/mo)
4. After subscribing, go to `app.klingai.com/global/dev` to generate an API key (for Cowork automation later — Matthew or Sentinel will handle this part)

### Understanding Credits

- You get 3,000 credits/month on Pro
- A standard 5-second video at 1080p costs ~20 credits
- Higher quality ("cinematic" mode) costs 1.5-2x more
- **Tip:** Use "Standard" quality for drafts and experiments, "Professional" only for final exports
- Credits reset monthly — they do not roll over

### Recommended Settings for Instagram Reels / TikTok

| Setting | Value | Why |
|---------|-------|-----|
| Aspect Ratio | **9:16** | Native vertical — no cropping needed |
| Resolution | **1080p** | Full HD, optimized for mobile |
| Frame Rate | **30fps** | Standard for most content (use 60fps only for fast motion) |
| Duration | **5-6 seconds** | Social sweet spot — forces directness, creates natural loops |
| Mode | **Standard** for drafts, **Professional** for finals | Saves credits during iteration |

### Prompting Guide for Spiritual / Atmospheric Content

Kling responds best to structured prompts. Use this formula:

```
[Scene/Setting] + [Subject & Appearance] + [Action/Motion] + [Camera Movement] + [Atmosphere/Mood] + [Lighting]
```

**Example prompts that work well for faith content:**

**Meditative / Prayer:**
> Slow dolly-in on a person kneeling in a sunlit chapel. Morning light streams through stained glass windows, casting colored light across stone floor. Dust particles float in light beams. Sacred, reverent, peaceful atmosphere. Warm golden hour lighting.

**Nature / Creation:**
> Aerial tracking shot over a misty mountain valley at dawn. Clouds drift slowly between peaks. A river winds through the valley below, catching first light. Ethereal, transcendent, serene atmosphere. Soft diffused natural lighting.

**Abstract / Worship:**
> Close-up of hands releasing glowing particles that float upward against a dark background. Particles form constellation-like patterns. Gentle, ascending motion. Celestial, luminous, otherworldly atmosphere. Soft rim lighting with deep shadows.

**Scripture Visual:**
> A single candle flame in a dark room. Camera slowly orbits around it. The flame flickers gently, casting warm light on an open book. Intimate, sacred, meditative atmosphere. Dramatic chiaroscuro lighting.

**Looping Ambient (for background reels):**
> Gentle ocean waves washing over smooth stones at sunset. Camera locked in place. Golden light reflects off water surface. Seamless loop. Serene, calming, contemplative atmosphere. Warm backlit golden hour.

### Prompting Rules

**DO:**
- Be specific about camera movement (dolly-in, orbit, tracking, locked)
- Name the lighting explicitly (golden hour, rim light, diffused, chiaroscuro)
- Include 2-3 mood/atmosphere words (ethereal, sacred, transcendent, serene, luminous)
- Keep subjects simple — one main element, one setting
- Describe motion intentionally — what moves, what stays still

**DO NOT:**
- Write essay-length prompts — 2-4 sentences max
- Ask for text/words in the video — AI text rendering is unreliable
- Include multiple scene changes in one generation
- Use vague descriptors ("beautiful," "nice," "cool")
- Request human faces in close-up unless you have a reference image (faces can distort)

**Negative prompt (always include):**
> Smiling, cartoonish, oversaturated, low resolution, blurry, disfigured, extra limbs, text overlay, watermark

This prevents Kling's tendency toward overly cheerful defaults, which clashes with reverent/solemn spiritual content.

### Image-to-Video Workflow (Higher Quality)

For the best results, especially for consistent style:

1. Generate a still image first using Midjourney, Flux, or Kling's own image generator
2. Pick the image that nails the look you want
3. Use Kling's Image-to-Video feature to animate it
4. In the motion prompt, describe ONLY the movement — do not re-describe what is in the image
5. Example motion prompt: "Slow push-in. Gentle wind moves fabric. Light particles drift upward. Subtle camera sway."

This gives you much more control over the visual starting point.

### Batch Content Creation Workflow

**Weekly batch session (1-2 hours, produces 10-15 clips):**

1. **Theme first.** Pick the week's content theme (e.g., "Peace," "Trust," "Gratitude"). Align with any scripture or devotional plan.
2. **Write 10-15 prompts in a doc.** Use the formula above. Draft all prompts before generating anything.
3. **Generate in Standard quality first.** Run all prompts at Standard quality to see which concepts work. This uses fewer credits.
4. **Pick winners.** Select the 5-7 best outputs.
5. **Re-generate winners in Professional quality.** Only spend premium credits on proven concepts.
6. **Export and organize.** Download finals. Name files by theme and date (e.g., `peace-ocean-2026-03-23.mp4`).
7. **Queue for approval.** Drop finals into the shared approval folder/channel before posting.

**Credit budget per batch session:**
- 10-15 Standard drafts: ~200-300 credits
- 5-7 Professional finals: ~150-250 credits
- Total per session: ~350-550 credits
- At Pro tier (3,000 credits/mo), you can do ~5-8 batch sessions per month

### Approval Workflow Before Posting

1. Jeff generates content in batch sessions
2. Finals go into a shared Telegram thread or Google Drive folder tagged "PENDING REVIEW"
3. Matthew reviews and approves/rejects with a quick thumbs up or note
4. Only approved clips get posted
5. Jeff handles posting to Instagram Reels / TikTok with captions and hashtags

**Rule: Nothing posts without Matthew's approval.** This is a faith brand — tone, theology, and visual quality all matter. One bad AI artifact in a spiritual context can damage trust instantly.

### Quick Reference Card

```
SETTINGS:        9:16 | 1080p | 30fps | 5-6 sec
PROMPT FORMAT:   Scene + Subject + Motion + Camera + Mood + Lighting
MOOD WORDS:      ethereal, sacred, luminous, serene, transcendent, celestial
NEGATIVE PROMPT: smiling, cartoonish, oversaturated, low res, blurry, disfigured, text
BATCH FLOW:      Theme → Write prompts → Standard drafts → Pick winners → Pro finals → Approve → Post
CREDITS:         ~20/video standard, ~35/video professional. Budget ~500/batch.
```

---

## Sources

- [Kling AI Membership Plans](https://app.klingai.com/global/membership/membership-plan)
- [Kling AI Pricing Breakdown (AI Tool Analysis)](https://aitoolanalysis.com/kling-ai-pricing/)
- [Kling AI Developer API](https://app.klingai.com/global/dev/document-api/quickStart/userManual)
- [Kling AI Privacy Policy](https://klingai.com/global/docs/privacy-policy)
- [Kling 3.0 Tutorial (Cliprise)](https://www.cliprise.app/models/kling-3-0)
- [Kling 3.0 Prompt Guide (fal.ai)](https://blog.fal.ai/kling-3-0-prompting-guide/)
- [Kling AI Prompt Guide (Ambience AI)](https://www.ambienceai.com/tutorials/kling-prompting-guide)
- [Google Veo 3.1 Pricing (CostGoat)](https://costgoat.com/pricing/google-veo)
- [Veo 3.1 vs Sora 2 vs Kling (AIML API)](https://aimlapi.com/blog/google-veo-3-1)
- [Kling AI Complete Guide (AI Tool Analysis)](https://aitoolanalysis.com/kling-ai-complete-guide/)
