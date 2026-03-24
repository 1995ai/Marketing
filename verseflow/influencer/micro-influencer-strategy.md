# VerseFlow Micro-Influencer Strategy
> Last Updated: 2026-03-23
> Purpose: Scalable playbook for micro-influencer partnerships to drive VerseFlow installs and paid conversions
> Benchmark: Lolo partnership achieved $5.71 CPI vs $10.61 industry average (46% cost reduction)

---

## 1. Ideal Influencer Profile

### Demographics & Platform

| Attribute | Ideal | Acceptable |
|-----------|-------|------------|
| **Follower range** | 10K-50K | 50K-100K |
| **Engagement rate** | 4%+ (likes + comments / followers) | 3%+ minimum |
| **Platform priority** | Instagram (Reels + Stories) | TikTok secondary, YouTube Shorts tertiary |
| **Age of creator** | 24-35 | 20-40 |
| **Audience age** | 24-35 primary | 18-40 acceptable |
| **Gender split** | Either; mix of male and female creators | Avoid all-male or all-female roster |
| **Geography** | US-based | English-speaking (Canada, UK acceptable) |

### Content Type (Must-Haves)

- **Personal devotional content** -- shares their own quiet time, prayer life, or scripture study. Not just quoting verses, but showing what faith looks like in daily practice.
- **Anti-performance Christianity** -- authentic, imperfect, vulnerable. Not polished megachurch aesthetic. Not prosperity gospel. Not culture war content.
- **Short-form video native** -- already posting Reels or TikToks, not just static carousel quotes.
- **Wellness-adjacent** -- content that touches mental health, anxiety, rest, or intentional living alongside faith. This maps directly to VerseFlow's "3 minutes. Scripture. Breathe." positioning.

### Theological Alignment (Non-Negotiable)

- **Protestant/evangelical** -- mainline or nondenominational preferred. Must affirm Scripture as authoritative.
- **No culture war content** -- accounts that spend significant time on political or divisive social topics are disqualified. VerseFlow is about closeness to God, not tribal signaling.
- **No prosperity gospel** -- if the feed is dominated by "God wants you wealthy," hard pass.
- **Ecumenically warm** -- can partner across denominations without alienating segments of the audience.
- **Theologically literate** -- doesn't need to be a seminary grad, but should handle Scripture with care and accuracy.

### Red Flags (Disqualify)

- Sudden follower spikes without engagement growth (purchased followers)
- Engagement rate below 2% (dead audience or bot followers)
- Brand deal saturation (more than 30% of posts are sponsored)
- Controversial public statements on divisive theological or political issues
- Content that feels performative or manufactured rather than genuine

### Platform Priority Rationale

**Instagram first** because:
- Lolo benchmark was Instagram-based; replicate what's working
- Instagram Stories swipe-up/link stickers allow direct app store links (attribution)
- Reels algorithm favors niche content to engaged audiences
- Instagram audience skews 25-34 (VerseFlow's core demo)

**TikTok second** because:
- Higher organic reach potential for new accounts
- Gen Z skew is slightly younger than VerseFlow's sweet spot
- Attribution is harder (no swipe-up equivalent in organic content)
- AI content disclosure requirements add friction

**YouTube Shorts tertiary** because:
- Longer content relationship (subscribers watch more deliberately)
- Better for retargeting and funnel building
- Lower volume of faith micro-influencers compared to Instagram

---

## 2. Metrics Framework

### Core KPIs

| Metric | Definition | Target | Source |
|--------|-----------|--------|--------|
| **CPI (Cost Per Install)** | Total spend / attributed installs | <$6.00 (beat Lolo's $5.71 as floor) | MMP + promo code tracking |
| **Engagement rate** | (Likes + comments + saves + shares) / followers | 4%+ on sponsored posts | Instagram Insights or HypeAuditor |
| **Story view rate** | Story views / follower count | 5%+ | Instagram Insights (request from creator) |
| **Link click-through rate** | Link clicks / story views | 3%+ | UTM-tagged link analytics |
| **Promo code redemption** | In-app promo code entries / attributed installs | 30-50% (expected capture rate) | RevenueCat or in-app analytics |
| **Trial-to-paid conversion** | Paid subs / trial starts from influencer cohort | Track separately per influencer | RevenueCat (requires cohort tagging) |
| **30-day retention** | Users still active 30 days after install | 25%+ | App analytics |

### Secondary KPIs

| Metric | Definition | Why It Matters |
|--------|-----------|---------------|
| **Organic lift** | Increase in organic installs during campaign window vs baseline | Captures unattributed installs driven by influencer exposure |
| **Brand search lift** | "VerseFlow" Google/App Store searches during campaign | Shows awareness even when installs aren't directly tracked |
| **Content save rate** | Saves on sponsored Reels / total views | Saves signal high-intent interest; algorithm boost |
| **Comment sentiment** | Qualitative -- are comments asking about the app? | Leading indicator of conversion intent |
| **Follower growth** | VerseFlow IG follower increase during campaign | Secondary; awareness metric |

### Tracking Cadence

- **Per campaign**: CPI, engagement rate, link clicks, promo redemptions
- **Weekly**: Organic lift analysis, brand search volume
- **Monthly**: Trial-to-paid by influencer cohort, 30-day retention, budget reallocation
- **Quarterly**: Full ROI review, influencer roster cull/expand

---

## 3. Attribution Strategy

### The Problem

iOS App Store installs are anonymous. When a user taps "Get" on the App Store, Apple does not pass referral data back to the app. This means you cannot deterministically connect an influencer's link click to an app install. Android (Google Play) is better but still imperfect.

### Multi-Layer Attribution Approach

**Layer 1: UTM-Tagged Landing Pages (Pre-App-Store)**

Create a unique landing page per influencer: `verseflow.app/lolo`, `verseflow.app/megs`, etc.

- Each page has the influencer's name, a brief pitch, and a "Download" button that links to the App Store
- UTM parameters on the landing page URL: `?utm_source=instagram&utm_medium=influencer&utm_campaign=lolo_march26`
- Google Analytics tracks page visits, time on page, and button clicks
- This gives you: click volume, click-to-page-visit conversion, and page-visit-to-download-button-click conversion
- **Gap**: Once the user hits the App Store, tracking breaks. You know how many clicked the download button, but not how many actually installed.

**Layer 2: Unique Promo Codes (Post-Install)**

Each influencer gets a unique promo code (e.g., `LOLO`, `MEGS`, `FAITH30`).

- Users enter the code during onboarding or in settings for a benefit (extended trial, bonus content, etc.)
- This captures 30-50% of influencer-driven installs (users who remember and bother to enter the code)
- Promo codes are the single most reliable per-influencer attribution method for iOS
- **Implementation**: Add a "Got a promo code?" field to the onboarding flow. Low engineering effort, high attribution value.

**Layer 3: Organic Lift Analysis (Statistical)**

Compare daily organic install baseline to installs during and 48 hours after an influencer post.

- If baseline is 5 installs/day and you see 15 installs/day during the campaign, the lift is ~10 installs attributable to the influencer
- This is imprecise but captures the installs that promo codes miss
- Best done with a clean calendar -- one influencer posting at a time, or stagger by 48+ hours

**Layer 4: MMP Deep Links (If Budget Allows)**

Integrate a Mobile Measurement Partner (AppsFlyer, Adjust, or Branch).

- MMPs use probabilistic fingerprinting: they match the device that clicked the influencer's link to the device that opened the app, using IP address, device type, and timestamp
- 60-80% match rate on iOS post-ATT (not perfect, but better than nothing)
- Cost: $0-500/month depending on install volume (most MMPs have free tiers under 10K installs/month)
- **Recommendation**: Defer MMP integration until monthly influencer spend exceeds $2,000. Below that, promo codes + organic lift analysis is sufficient.

**Layer 5: Post-Install Survey**

Add "How did you hear about VerseFlow?" to onboarding with options: App Store search, Friend/family, Instagram, TikTok, YouTube, Church, Other.

- Low-effort, qualitative signal
- Not precise, but directionally useful for channel allocation

### Attribution Priority (Now vs Later)

| Method | Build Now? | Effort | Accuracy |
|--------|-----------|--------|----------|
| UTM landing pages | YES | Low (1-2 hours) | High for clicks, none for installs |
| Unique promo codes | YES | Low-Medium (add field to onboarding) | Medium (captures 30-50%) |
| Organic lift analysis | YES | None (just math) | Low-Medium (directional) |
| Post-install survey | YES | Low (add onboarding step) | Low (self-reported) |
| MMP deep links | LATER ($2K+/mo spend) | Medium (SDK integration) | Medium-High (60-80%) |

### Accepted Gaps

- You will never have 100% attribution on iOS. Accept this.
- The true CPI is always better (lower) than the measured CPI, because organic lift is real but undercounted.
- Lolo's $5.71 CPI was likely calculated from promo codes or link clicks only, meaning the true CPI was probably $3-4. Keep this in mind when benchmarking new influencers.

---

## 4. Budget Framework

### Per-Influencer Rate Ranges

| Tier | Followers | Instagram Reel | Instagram Story (3-frame) | Story + Reel Bundle | TikTok Video |
|------|-----------|---------------|--------------------------|--------------------:|-------------|
| **Nano-Micro** | 10K-50K | $150-500 | $100-300 | $200-700 | $100-400 |
| **Micro** | 50K-100K | $500-1,500 | $300-800 | $700-2,000 | $400-1,000 |
| **Mid-Tier** | 100K-250K | $1,500-4,000 | $800-2,000 | $2,000-5,000 | $1,000-3,000 |

**Notes:**
- Faith/Christian niche tends to run 10-20% below general lifestyle rates because creators are often mission-motivated and more willing to partner with aligned brands at lower rates
- Rates above assume 1 post. Negotiate package deals (3-post minimum) for 15-25% discount
- Usage rights (reposting their content on VerseFlow channels) adds 20-50% to the base rate. Negotiate upfront.

### Compensation Structure

**Recommended: Hybrid (Flat Fee + Performance Bonus)**

| Component | Structure | Example |
|-----------|-----------|---------|
| **Base fee** | Flat rate per deliverable (Reel, Story, or bundle) | $300 for 1 Reel + 3 Stories |
| **Performance bonus** | $2-3 per verified install (via promo code) | If promo code generates 100 installs, $200-300 bonus |
| **Recurring bonus** | $1 per subscriber who converts to paid (tracked via promo code cohort) | If 10 users from their code convert, $10/month recurring |

**Why hybrid works:**
- Base fee ensures creators are compensated regardless of attribution gaps (builds goodwill)
- Performance bonus aligns incentives without putting all risk on the creator
- Recurring bonus incentivizes creators to mention VerseFlow organically over time, not just in paid posts

**Alternative for very small creators (10K-20K):**
- Gifted partnership: Free premium subscription + feature on VerseFlow social + small flat fee ($50-150)
- Many nano-creators in the faith space will post for free if they genuinely love the app. But always offer at least something.

### Monthly Budget Recommendation

| Phase | Monthly Spend | Influencers | Expected Installs (conservative) |
|-------|--------------|-------------|--------------------------------|
| **Phase 1 (Now - Month 2)** | $500-1,000 | 2-3 nano-micro (10K-50K) | 100-200 |
| **Phase 2 (Month 3-4)** | $1,500-3,000 | 3-5 micro (mix of tiers) | 300-600 |
| **Phase 3 (Month 5+)** | $3,000-5,000 | 5-8 across tiers | 600-1,000+ |

**Phase 1 rationale:** Low spend, test attribution pipeline, validate that new creators can match or beat Lolo's CPI. Do not scale until promo code tracking and onboarding fix (from 10K plan) are both live.

**Break-even math:** At $49.99/year subscription, each paid subscriber is worth ~$50. If trial-to-paid conversion is 15% (the target), each install is worth $7.50. A $6.00 CPI means positive unit economics from day one. Scaling spend is justified once conversion rate is proven.

---

## 5. Top 10 Influencer Candidates

The following candidates were identified through web research across influencer directories, faith community lists, and Instagram. Follower counts and engagement rates are estimates based on publicly available data as of March 2026. IMPORTANT: These are starting points for Jeff to evaluate. Actual follower counts, engagement rates, and theological alignment must be verified before outreach.

**Verification needed before outreach:** Pull each account through HypeAuditor or Social Cat free engagement calculator. Check last 12 posts for brand deal frequency, theological tone, and audience quality.

| # | Handle | Est. Followers | Est. Engagement | Content Type | Why They Fit VerseFlow |
|---|--------|---------------|----------------|-------------|----------------------|
| 1 | **@she_lives_loved** (Megs) | ~45K | ~4-5% (niche Bible journaling community) | Bible study journaling, daily quiet time, faith-filled reflections | Perfect overlap: daily scripture practice, "finding joy in a quiet life," anti-hustle, devotional-focused. Audience is women 24-35 doing daily Bible study. Direct match for "3 minutes with God." |
| 2 | **@ashleysbiblestudy** (Ashley) | ~44K | ~4-6% (estimated, niche devotional) | Daily Bible study encouragement, digging deep into Scripture | Encourages others to study Scripture daily. Authentic voice, not polished. Her audience actively studies the Bible, meaning they would naturally adopt a daily devotional app. |
| 3 | **@drcourtneymiller** (Dr. Courtney Miller) | ~43K | ~3-5% (estimated) | Faith + psychology, helping women thrive, pastor + psychologist | Faith-meets-mental-health crossover is exactly VerseFlow's "breathe + scripture" positioning. Licensed psychologist adds credibility. Anti-anxiety angle aligns with breathing devotional. |
| 4 | **@faithflicks** | ~15-30K (est.) | ~5-7% (estimated, small niche) | Quick creative scripture videos, "spiritual energy shots" | Format is nearly identical to what VerseFlow offers: short, punchy scripture content. Audience already consumes micro-devotional content. Natural alignment. |
| 5 | **@dailygraceandgiggles** | ~10-25K (est.) | ~5-8% (estimated, small niche) | Faith-forward humor, coffee + Psalms memes, relatable devotional | Reaches a younger, casual Christian audience who might not seek out "serious" devotional apps but would try a 3-minute app. Humor lowers the barrier to entry. |
| 6 | **@epicprayermoments** | ~10-25K (est.) | ~5-8% (estimated, small niche) | Cinematic prayer videos, visual worship content | Visual-first content aligns with VerseFlow's breathing/scripture visual experience. Could create stunning sponsored Reels showing the app in a prayer setting. |
| 7 | **@instabiblestudygroup** (Jennifer Belle) | ~139K | ~2-3% (larger account, lower rate typical) | Bible study tips, journaling, "your relatable Christian bestie" | Larger but highly relevant. Audience is actively doing daily Bible study. Her "relatable bestie" tone matches VerseFlow's warm-not-saccharine brand voice. Negotiate a bundle deal given larger audience. |
| 8 | **@theseunbabara** (Seunbabara Babajide) | ~167K | ~2-3% (estimated) | Faith tools, Scripture resources, equipping believers | "Equipping people with faith tools and truth" is directly aligned with what VerseFlow is. Also runs @scripturehavenco, a Scripture resource brand, showing entrepreneurial alignment. Mid-tier budget required. |
| 9 | **Liana** (TikTok-first, cross-posts to IG) | ~70K+ | ~4-6% (estimated, high TikTok engagement) | Conversational scripture explainers, end times, prayer | Strong Gen Z voice. "I want to be a spokesperson for Christianity in my generation." Her explainer format could translate well to an app walkthrough or "day in my devotional life" Reel. |
| 10 | **@praywithpals** (TikTok/IG) | ~10-20K (est.) | ~6-10% (estimated, very small niche) | Spontaneous prayer duets, everyday devotion glimpses | Community-driven prayer content. Could create a collaborative "pray with me using VerseFlow" format that encourages downloads through genuine use. Very small but highly engaged. |

### Candidate Sourcing -- Next Steps for Sentinel

Once Matthew provides Instagram Graph API access:
1. Scrape hashtags: #dailydevotional, #quiettimewithGod, #scriptureoftheday, #biblejournaling, #morningdevotional, #faithoverfear
2. Filter: 10K-100K followers, 3%+ engagement, US-based, posted within last 7 days
3. Score by: engagement rate (40%), content relevance (30%), audience demo match (20%), posting consistency (10%)
4. Output top 25 candidates to staging for Jeff review

### Platforms for Discovery (Manual, Before API)

- **Collabstr**: 2,661+ indexed Christian creators, filterable by follower count and engagement
- **Heepsy**: Filter by niche, location, follower range, engagement rate
- **Modash**: Audience demographic analysis (age, gender, location of followers)
- **HypeAuditor**: Fraud detection and audience quality scoring

---

## 6. Outreach Template

### Initial DM (Instagram)

Jeff sends this from a personal or VerseFlow brand account. Keep it short -- DMs over 3 sentences get ignored.

```
Hey [Name]! I'm Jeff with VerseFlow -- a 3-minute daily devotional app
(scripture + guided breathing). Your content around [specific thing they
post about, e.g., "daily quiet time" or "faith and mental health"] really
resonates with what we're building.

Would you be open to trying the app and chatting about a potential
partnership? Happy to give you premium access. No strings.
```

### Follow-Up Email (If They Respond Positively)

```
Subject: VerseFlow x [Name] -- quick details

Hi [Name],

Thanks for being open to this! Here's the quick rundown:

**What VerseFlow is:** A daily devotional app -- 3 minutes of scripture +
guided breathing. We built it as an anti-doom-scroll: instead of 4 hours
on TikTok, give God 3 minutes. Available on iOS and Android.

**What we're looking for:** 1 Instagram Reel (30-60 sec) + 3 Stories
showing you using the app during your quiet time. Authentic, in your own
voice -- not a scripted ad read.

**Compensation:**
- [Flat fee: $___] for the Reel + Stories package
- Bonus: $2 per install through your unique promo code
- Free premium subscription (lifetime)

**Timeline:** Flexible. We'd love content within 2-3 weeks of agreement,
but we work around your schedule.

**Next step:** Want to hop on a 15-min call this week? I can walk you
through the app and answer any questions.

Best,
Jeff
[VerseFlow link]
```

### Key Outreach Principles

1. **Lead with their content, not your app.** Show you actually follow them.
2. **Offer the app for free first.** Let them use it. If they don't like it, don't push. Forced partnerships produce bad content.
3. **Don't over-negotiate upfront.** Get the first post done. If it works, negotiate a longer-term deal.
4. **Respect their theology.** If their content doesn't align after closer review, gracefully pass. Don't try to mold them into something they're not.
5. **Jeff owns the relationship.** Sentinel finds candidates. Jeff builds the human relationship. This is non-delegable.

---

## 7. Operational Playbook

### Weekly Cadence

| Day | Task | Owner |
|-----|------|-------|
| Monday | Review influencer pipeline + performance from prior week | Jeff + Matthew |
| Tuesday-Wednesday | Send outreach to new candidates (3-5/week) | Jeff |
| Thursday | Review any incoming content drafts from active partners | Jeff (Matthew reviews if needed) |
| Friday | Post performance check: engagement, promo code redemptions | Sentinel (automated once API connected) |

### Influencer Onboarding Checklist (Per Creator)

- [ ] Verify theological alignment (review last 30 posts)
- [ ] Check engagement rate via HypeAuditor or Social Cat
- [ ] Confirm audience demographics (age, location) via Modash or creator's media kit
- [ ] Send initial DM
- [ ] If interested: send follow-up email with terms
- [ ] Provide premium app access
- [ ] Generate unique promo code (e.g., `MEGS30`)
- [ ] Create UTM-tagged landing page (`verseflow.app/megs`)
- [ ] Agree on deliverables, timeline, and compensation
- [ ] Review and approve content before posting (optional -- depends on trust level)
- [ ] Track: post date, engagement, link clicks, promo redemptions, organic lift

### Content Guidelines for Creators

Share these with every partner:

1. **Be yourself.** We chose you because of your voice. Don't change it for us.
2. **Show, don't sell.** Record yourself actually using the app during your quiet time. Let viewers see the experience, not hear a pitch.
3. **Mention the "3 minutes" hook.** That's the sticky idea. "3 minutes. Scripture. Breathe."
4. **Use your promo code.** Mention it naturally -- "I have a code for you: [CODE] for a free trial."
5. **Tag @verseflowapp.** We'll reshare your content (with permission).
6. **Disclose the partnership.** Use #ad or #partner. Non-negotiable for FTC compliance.
7. **No theological claims on our behalf.** Don't say VerseFlow teaches X theology or endorses Y position. It's a devotional tool, not a doctrinal statement.

---

## 8. Risk Assessment

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|-----------|
| Influencer says something controversial after partnering | Medium | High | Short-term contracts only (per-post, not annual). No exclusivity. Morality clause in written agreement. |
| Attribution gap makes ROI unmeasurable | High | Medium | Accept the gap. Use multi-layer approach (promo codes + organic lift + survey). Don't expect perfection. |
| Creators produce low-quality or off-brand content | Medium | Medium | Provide content guidelines. Review first post before publishing (for new partners). Drop creators who miss the mark. |
| Oversaturation -- too many faith apps competing for same influencers | Low (for now) | Medium | Move fast. Lock in relationships before Hallow, Glorify, or Pray.com scale their influencer programs. |
| Trial-to-paid conversion is still 0%, making all installs worthless | High (current state) | Critical | DO NOT scale influencer spend past Phase 1 ($1K/mo) until onboarding is fixed and conversion rate exceeds 10%. Every install into a broken funnel is wasted money. |

---

## 9. Decision Points for Matthew

1. **Approve Phase 1 budget?** $500-1,000/month for 2-3 nano-micro influencers. Low risk, tests the pipeline.
2. **Promo code onboarding field**: This requires a code change. Who builds it? When?
3. **UTM landing pages**: Who sets up `verseflow.app/[name]` pages? Sentinel can draft them but someone needs to deploy.
4. **Graph API access for Sentinel**: Once provided, Sentinel can automate candidate discovery at scale.
5. **Does Jeff have bandwidth?** Jeff owns Hammer Golf + NinetyFive consulting + VerseFlow. Influencer relationship management takes 3-5 hours/week. Is this realistic in his current load?

---

## Sources

- [Micro Influencer Rates 2026 -- Influencer Marketing Hub](https://influencermarketinghub.com/micro-influencer-rates/)
- [Influencer Rates 2026 -- Afluencer](https://afluencer.com/influencer-rates/)
- [Influencer Pricing 2026 -- Shopify](https://www.shopify.com/blog/influencer-pricing)
- [How to Measure Influencer Campaigns Without Full Attribution -- App Growth Summit](https://appgrowthsummit.com/how-to-measure-influencer-campaigns-in-the-absence-of-full-attribution/)
- [Influencer Marketing for Apps -- Adjust](https://www.adjust.com/blog/influencer-marketing-for-mobile-apps/)
- [Cost Per Install with Influencers -- Influencer.co](https://influencer.co/blog/cost-per-install-how-to-use-influencers-to-supercharge-your-next-mobile-app-campaign)
- [Mobile App Attribution -- Branch](https://www.branch.io/resources/blog/how-mobile-app-install-attribution-works-for-ios-and-android/)
- [UTM Links for Apps -- Gummicube](https://www.gummicube.com/blog/utm-links-what-they-are-and-how-to-track)
- [Instagram Engagement Rate Benchmarks 2026 -- Social Insider](https://www.socialinsider.io/social-media-benchmarks/instagram)
- [Instagram Engagement Rate Benchmarks 2026 -- InfluenceFlow](https://influenceflow.io/resources/instagram-engagement-rate-benchmark-complete-2026-guide-for-creators-brands/)
- [Top Christian Influencers -- Socially Powerful](https://sociallypowerful.com/post/top-20-christian-influencers)
- [Christian Influencers -- IZEA](https://izea.com/resources/christian-influencers/)
- [Christian Influencers on Instagram -- Crosswalk](https://www.crosswalk.com/faith/spiritual-life/uplifting-instagram-influencers-to-follow-now.html)
- [Young Christian Influencers 2025 -- Christ Life Club](https://christlifeclub.com/10-young-christian-influencers-on-tiktok-instagram-u-s-in-2025/)
- [Find Christian Influencers -- Collabstr](https://collabstr.com/top-influencers/christian)
- [Christian Influencers -- Click Analytic](https://www.clickanalytic.com/find-influencers/worldwide/christian-influencers/)
- [Gen Z Christians on Social Media -- Katy Christian Magazine](https://katychristianmagazine.com/?p=76297)
- [Religious Influencers Teaching Online -- CBN News](https://cbn.com/news/us/these-influencers-are-teaching-christianity-online-and-young-people-are-listening)
