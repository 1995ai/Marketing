# Research: Email Nurture Tool Selection + Canva Automation for Verseflow

> Last Updated: 2026-03-24
> Agent: Sentinel (on-demand research)
> Sources: 14 sources consulted

## Decisions — Matt/Jeff Alignment 2026-03-24

| # | Question | Decision |
|---|----------|---------|
| E1 | **Who sets up Loops.so?** | ✅ **Jeff sets up.** |
| E2 | **Can we email Apple Sign-In users?** | ✅ **No — Apple private relay blocks marketing email. Exception: some users may share real email. Majority unreachable via email. Push notifications are primary re-engagement channel.** |
| E3 | **Who owns email content creation?** | ✅ **Cowork drafts, Jeff executes.** |

**Priority note:** Email nurture is secondary to onboarding improvements. Fix onboarding first (add optional email capture screen), then build Loops sequences. Don't invest in Loops setup until email capture yields real addresses.

## Sources Read

- `vault/INDEX.md` -- vault state, existing staging items
- `vault/_templates/research-output.md` -- output format
- https://www.sender.net/pricing/ -- Sender free tier details
- https://loops.so/pricing -- Loops.so pricing and features
- https://loops.so/docs/integrations/supabase -- Loops native Supabase integration
- https://www.klaviyo.com/pricing -- Klaviyo free tier and mobile SDK
- https://www.sender.net/reviews/mailchimp/pricing/free-plan/ -- Mailchimp free plan gutted in 2025-2026
- https://encharge.io/customer-io-pricing/ -- Customer.io pricing breakdown
- https://www.canva.com/help/mcp-canva-usage/ -- Canva MCP actions available
- https://www.canva.dev/docs/connect/autofill-guide/ -- Canva Autofill API (Enterprise only)
- https://www.canva.com/help/mcp-agent-setup/ -- Canva AI Connector setup
- https://www.bannerbear.com/pricing/ -- Bannerbear API pricing
- https://www.macrumors.com/2026/01/27/claude-app-integration-asana-slack-figma-canva/ -- Claude interactive MCP apps launch
- https://github.com/dataenthusiast-io/supabase-loops-webhook -- Supabase-to-Loops middleware

---

# Part 1: Email Nurture Tool Selection

## Comparison Matrix

| Tool | Free Tier | Paid Starting | Automation on Free? | Supabase Integration | Best For |
|------|-----------|--------------|---------------------|---------------------|----------|
| **Sender** | 2,500 contacts / 15K emails/mo | $15/mo | YES -- full automation | No native. Custom via API + Supabase Edge Functions or n8n | Budget-conscious, general email. Best free tier by far. |
| **Loops.so** | 1,000 contacts / 4K emails/mo | $49/mo (5K contacts) | YES -- full automation | NATIVE -- built-in Supabase webhook integration for auth.users | SaaS trial nurture. Purpose-built for this exact use case. |
| **Klaviyo** | 250 contacts / 500 emails/mo | $20/mo | YES -- full automation | No native. Has mobile SDKs (iOS/Android/RN). Custom API integration. | E-commerce, mobile app marketing at scale. Overkill now. |
| **Mailchimp** | 250 contacts / 500 emails/mo | $13/mo (Essentials) | NO -- automation removed from free in June 2025 | No native. Custom API only. | ELIMINATED. No automation on free = useless for this. |
| **Customer.io** | No free tier (14-day trial only) | $100/mo (5K profiles) | N/A | No native. Strong API/webhooks for custom integration. | Complex behavior-triggered flows at scale. Way too early. |

## Key Findings

1. **Mailchimp is dead for this use case.** Free plan was gutted twice in 2025 -- automation removed entirely in June, contacts halved to 250 in December. No sequences on free tier. Eliminate immediately.

2. **Customer.io is premature.** $100/mo minimum, no free tier, steep learning curve, requires engineering resources. Built for companies with thousands of users and complex multi-channel flows. Come back at 1,000+ subscribers if behavior-triggered messaging becomes critical.

3. **Sender has the most generous free tier** (2,500 contacts, 15K emails, full automation). But it has no native Supabase integration -- you would need to build a custom pipeline with Edge Functions or use n8n as middleware. It is also not SaaS-focused; it is built for e-commerce and general email marketing.

4. **Loops.so has a native Supabase integration** that auto-syncs users from `auth.users` via database webhooks. INSERT/UPDATE/DELETE events on the auth table are handled out of the box. New signups in Supabase automatically become Loops contacts and can be enrolled in sequences immediately. The free tier covers 1,000 contacts with full automation.

5. **Klaviyo is interesting for later** -- it has native mobile SDKs (iOS, Android, React Native) with push notifications, in-app messaging, and geofencing. At 23 subscribers you would hit the 250-contact ceiling fast, and the mobile features are not needed until the app has significant DAU. Worth revisiting at 500+ subscribers if mobile push becomes a priority.

## Recommendation: Loops.so

**For where Verseflow is right now, Loops.so is the clear pick.** Here is the rationale:

**Why Loops wins:**
- Native Supabase integration. This is the decisive factor. No custom Edge Functions, no middleware, no n8n. Configure a database webhook in Supabase, point it at Loops, done. New trial users auto-sync.
- Purpose-built for SaaS trial nurture. The entire product is designed around the exact workflow Verseflow needs: user signs up, enters trial, receives automated sequence, converts or churns.
- 1,000 contacts on free tier with full automation. At 23 subscribers, that gives massive runway before hitting a paywall.
- Clean API for transactional emails too -- password resets, trial expiry notices, etc., all in one platform. No need for a separate SendGrid/Mailgun setup.
- Simple pricing with no feature gates. Every tier gets the full product.

**Why not Sender despite the bigger free tier:**
- No native Supabase integration means custom development work to connect the two systems. For a solo founder moving fast, integration friction matters more than an extra 1,500 free contacts you won't need for months.
- Sender is e-commerce-focused. Its templates, automations, and segmentation logic are built around carts and purchases, not app trials and feature adoption.

**Growth path:**
- Free tier (now): 0-1,000 contacts. Set up the 7-day nurture sequence and transactional emails.
- $49/mo tier: When you cross 1,000 contacts. By then, the tool should be paying for itself through trial-to-paid conversions.
- Re-evaluate at 5,000+ contacts: If mobile push becomes critical, consider migrating to Klaviyo or adding Customer.io as a layer. Loops may feel limiting for complex multi-channel flows at scale.

**Setup effort estimate:** 2-4 hours. Configure Supabase webhook, build the 7-day email sequence in Loops' editor, test with a dummy signup. No engineering beyond the webhook config.

---

# Part 2: Canva MCP / API Integration

## 1. Does Canva Have an Official MCP Server?

**Yes.** Canva has a fully official MCP server, and it is one of the launch partners for Claude's interactive MCP Apps (shipped January 2026).

Two flavors exist:
- **Canva Connect APIs MCP Server** -- for design management, autofill, export. This is the one relevant for automated post creation.
- **Canva Apps SDK MCP Server** -- for developers building Canva apps/extensions. Not relevant here.

The Canva MCP is available as a Claude Connector (free on all Claude plans for basic tools; interactive apps require a paid Claude plan).

## 2. Does Canva Have a Public API?

**Yes.** The Canva Connect API is a full REST API that supports:
- Creating designs programmatically
- Uploading assets
- Exporting designs as images/PDFs
- Autofill (filling brand templates with dynamic data)

**Critical limitation:** The Autofill API -- which is the key feature for automated template-based post generation -- **requires a Canva Enterprise account.** Standard and Pro plans cannot use Autofill via API. This is a hard blocker for cost-effective automation.

## 3. What Can Be Automated?

| Action | Via MCP (Claude) | Via API | Requirement |
|--------|-----------------|---------|-------------|
| Create new design from scratch | YES (Canva AI generates it) | YES | Any Canva plan |
| Search existing designs | YES | YES | Any Canva plan |
| Export as PNG/PDF | YES | YES | Any Canva plan |
| Autofill template (swap text/images) | YES | YES | **Enterprise only** |
| Resize designs | YES | Limited | Any Canva plan |
| Swap text in templates | Only via Autofill | Only via Autofill | **Enterprise only** |
| Swap images in templates | Only via Autofill | Only via Autofill | **Enterprise only** |
| Use AI to generate design from prompt | YES (via MCP interactive) | NO (AI not exposed via API) | Claude paid plan |

**Bottom line:** You can ask Claude to "create a Verseflow social post about daily devotionals" via the MCP connector and Canva AI will generate a design. But systematically filling branded templates with swapped text/images at scale requires Enterprise, which is not justified at this stage.

## 4. Effort to Connect Canva to Cowork (Claude Desktop)

**Low effort for basic use.** Setup:
1. Open Claude Desktop settings
2. Go to Integrations
3. Enable Canva connector (it is in the directory)
4. Authorize with your Canva account
5. Start asking Claude to create/find/export designs

That is a 5-minute setup. The interactive MCP app lets you see and refine designs inside Claude's chat window.

**Limitation:** This is a manual workflow -- you talk to Claude, Claude talks to Canva, you iterate. It is not a "run overnight and generate 30 posts" pipeline. Each design requires a conversational loop.

## 5. Alternative Tools for Automated Static Post Generation

| Tool | What It Does | Pricing | API Quality | Best For |
|------|-------------|---------|-------------|----------|
| **Bannerbear** | Template-based image generation API. Define template, swap text/images via API. | $49/mo (1,000 images). No free tier beyond 30-image trial. | Excellent. REST + Zapier + Make. Synchronous and async endpoints. | Automated social post pipelines. Exactly this use case. |
| **Templated.io** | Bannerbear alternative, similar concept. | $7/mo (50 images) up to $89/mo (2,000 images). | Good. REST API. | Budget-friendly alternative to Bannerbear. |
| **Adobe Express API** | Adobe's answer to Canva API. | Part of Adobe Creative Cloud. API access requires enterprise agreement. | Emerging. Less mature than Bannerbear. | Teams already in Adobe ecosystem. |
| **Creatopy** | Ad/banner creation with automation. | $36/mo. Has API but primarily a UI tool. | Moderate. More manual than Bannerbear. | Display ad creation specifically. |
| **Placid.app** | Template-based image/video generation. | $29/mo (1,000 images). | Good REST API. Zapier/Make integrations. | Similar to Bannerbear, slightly cheaper. |

## Recommendation: Hybrid Approach

**Right now (0-6 months):** Use the Canva MCP connector in Cowork for on-demand design work. Matthew or Cowork describes what is needed, Claude creates it via Canva AI inside the chat, iterates on it, exports. This costs nothing beyond the existing Claude plan and a free/Pro Canva account. It handles the current volume (a few posts per week) without any infrastructure.

**When volume increases:** If Verseflow content needs scale to 3+ posts/day or templated batch generation (e.g., "generate 30 daily verse posts for the month"), move to **Bannerbear** or **Placid.app**. These are purpose-built for the "design template + dynamic data = auto-generated image" pipeline. Bannerbear at $49/mo gives 1,000 images/month, which is more than enough.

**Do not pursue Canva Autofill API.** The Enterprise requirement makes it a non-starter at this stage. The MCP connector gives you 80% of the value for interactive use, and Bannerbear/Placid give you the remaining 20% (batch automation) at a fraction of Enterprise cost.

**Specific next step for Cowork:** Enable the Canva connector in Claude Desktop. Test it by asking Claude to create a Verseflow social post. Evaluate whether the output quality meets the bar. If yes, this becomes the standard workflow for social content. If not, a human designs templates in Canva, and Cowork drafts the copy/specs.

---

## So What?

Two decisions needed:
1. **Email tool:** Set up Loops.so with the Supabase webhook integration. Estimated 2-4 hours of work. This unblocks the 7-day trial nurture sequence, which is the highest-leverage marketing automation Verseflow can build right now.
2. **Design automation:** Enable Canva MCP in Cowork for immediate use. Defer any paid design API (Bannerbear/Placid) until content volume justifies it.

## Unverified / Flagged

- Loops.so free tier limit: Multiple sources say 1,000 contacts / 2,000-4,000 sends. The exact send limit on the free plan varied across sources (some said 2,000, others 4,000). UNVERIFIED -- check Loops pricing page directly before committing.
- Canva MCP interactive apps: Confirmed available on paid Claude plans. UNVERIFIED whether it works on Claude Free tier for basic (non-interactive) Canva tools.
- Bannerbear $49/mo tier: Sources varied on exact credit count (some said 1,000, others listed different numbers). UNVERIFIED -- check bannerbear.com/pricing directly.

## Follow-Up Questions

- Does Verseflow currently collect email addresses at any point in the trial signup flow? If not, that needs to be added before any email tool matters.
- What Canva plan does Matthew currently have (Free, Pro, Enterprise)?
- Should the 7-day nurture sequence be drafted as a next step after tool selection is approved?
