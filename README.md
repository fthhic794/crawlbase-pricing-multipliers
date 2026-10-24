# crawlbase pricing: What 1,000 Pages Really Costs, the Multipliers Nobody Mentions, and When ScraperAPI Is the Better Deal

Crawlbase pricing runs on a single rate card: you pay only for successful requests, starting at $3.00 per 1,000 and falling to as low as $0.02 per 1,000 as your volume grows. There's no monthly fee and no card required to start, and if you prefer a fixed bill, subscriptions run from $99/month for 200,000 credits up to $599/month for 2 million. That's the short version.

The longer version matters more, because two things sit underneath those headline numbers: a site-difficulty multiplier that can multiply your entire bill by up to 20×, and JavaScript rendering that doubles the cost of any request. Most articles covering crawlbase pricing stop at the plan table and skip both. This one doesn't — and by the end, you'll be able to estimate what your specific crawl list would actually cost, and decide whether Crawlbase's model or a flat-credit alternative like ScraperAPI fits your targets better.

> **Quick take:** If most of your targets are easy, static sites, Crawlbase's pay-as-you-go ladder is genuinely cheap at volume. If you're pulling structured data from Amazon, Google, or Walmart and don't want to write your own parsers, ScraperAPI's pre-built endpoints will save you engineering time that easily outweighs a small per-request difference — plans start at $49/month with a 5,000-credit free trial. 👉 [See ScraperAPI's plans and start with 5,000 free credits](https://www.scraperapi.com/pricing?fp_ref=coupons)

## Crawlbase pricing at a glance

Crawlbase sells capacity in two ways: pay-as-you-go and monthly subscriptions. Both draw from the same credit balance, and that balance covers every product — the Crawling API (including screenshots), the Crawler, the Smart AI Proxy, and Cloud Storage.

**Pay-as-you-go** has no monthly fee and no card to start. You're billed monthly in arrears, only for successful requests, at a graduated ladder:

| Volume bracket | Price per 1,000 successful requests |
| --- | --- |
| First 1K | $3.00 |
| Next 10K | $2.00 |
| Next 100K | $0.60 |
| Next 1M | $0.50 |
| Next 10M | $0.10 |
| Next 100M | $0.05 |
| Next 1B | $0.04 |
| Beyond 1B | $0.02 |

You can set a hard spend cap so a runaway script can't drain your card. Crawlbase's own worked examples, for standard requests: 100K requests cost $76.40 (about $0.76 per 1,000), 1M requests cost $527.50 (about $0.53 per 1,000), and 10M requests cost $1,471.90 (about $0.15 per 1,000).

**Subscriptions** buy a monthly credit block at a lower effective rate, and — this part often gets missed — if you blow through the block, overage continues on the same rate card at the bracket your volume already reached. You don't get punished for exceeding your plan; you just keep paying metered rates.

| Plan | Monthly credits | Monthly price | Annual price | Effective rate |
| --- | --- | --- | --- | --- |
| Starter | 200K | $99 | $1,089 | ≈ $0.50 per 1k |
| Scale 500K | 500K | $199 | $2,189 | ≈ $0.40 per 1k |
| Scale 1M | 1M | $349 | $3,839 | ≈ $0.35 per 1k |
| Growth | 2M | $599 | $6,589 | ≈ $0.30 per 1k |

Yearly billing gets you one month free plus 8% off. If you need more than 2M credits a month, that moves to a custom enterprise arrangement with SLA and invoicing.

## The part most Crawlbase pricing write-ups skip: difficulty multipliers

Here's the detail that changes real-world budgets. The rate card above shows standard requests, but Crawlbase applies a site-difficulty multiplier to a group's whole ladder total, automatically:

- Standard ×1
- Moderate ×1.5
- Complex ×2
- Complex I ×3
- Complex II ×4.5
- Extreme ×9
- Extreme I ×13.5
- Extreme II ×20

What do those tiers mean? Standard covers structurally stable sites with little or no anti-bot protection. Moderate covers lighter countermeasures or sites that depend on JavaScript rendering. Complex covers sites that actively fingerprint browsers, rate-limit, and throw CAPTCHAs — those need adaptive proxy rotation and AI-driven request handling, which costs more to operate, so it costs you more per request.

On top of that, rendering a page in a real browser doubles the credits of any request, whatever the site's tier. There's no separate "browser tier" — it's a straight ×2. Screenshots through the Crawling API cost 2 credits, and storing a page in Cloud Storage runs 0.5 credits per month.

The practical consequence: a million requests against heavily defended targets doesn't cost $527.50. At a ×4.5 tier with JS rendering, you're looking at roughly ten times the standard figure. Crawlbase's own guidance is to use normal requests wherever the data already sits in the HTML and reserve rendering for sites that genuinely need it. That advice is worth money.

## What a crawl actually costs: Crawlbase's model vs flat credits

The honest answer to "what will this cost me" depends far more on your target sites than on the sticker plan prices.

Crawlbase charges per delivered page, scaled by difficulty. ScraperAPI, by contrast, uses a flat credit system where a standard page costs 1 credit — but specific hard targets have custom credit prices. Straight from ScraperAPI's pricing page: Amazon costs 5 credits per request, Google and Bing (including their subdomains) cost 25, LinkedIn costs 30, and sites behind Cloudflare, Datadome, or PerimeterX protection add 10 credits per request when the bypass succeeds. You can check the exact cost of any URL with the Domain Cost Estimator in your dashboard, and set a `max_cost` per scrape to cap any single request.

Put numbers on it: a Startup plan at $149/month buys 1,000,000 credits. Against plain static pages, that's a million pages. Against Google Search, it's 40,000 searches. That gap is the single most important thing to understand before comparing any scraping API's price list — and it's exactly why a comparison that only quotes plan prices misleads people.

Crawlbase handles LinkedIn differently from everything else. It sits in a "Fixed" category requiring a dedicated setup: requests run through trained AI bots that mimic human behavior, rely exclusively on premium residential proxies, and often need multiple retries because success rates are inherently low. You agree to separate fixed pricing for those domains rather than paying ladder rates. On the ScraperAPI side, LinkedIn simply costs 30 credits per request — no separate agreement, but also no ambiguity about what you're paying.

One more contrast that third-party comparisons keep highlighting: Crawlbase doesn't charge for failed or blocked requests at all. "You pay for successes, not attempts" is their framing, so cost tracks the pages you actually receive. If you're budgeting 50,000 delivered pages, you budget 50,000 successful requests, no failure-rate padding. That's a real advantage when your targets are hostile.

## Crawlbase vs ScraperAPI: pricing models side by side

Since you're evaluating crawlbase pricing, you're almost certainly weighing it against alternatives. Here's the structural comparison, using verified numbers:

| Dimension | Crawlbase | ScraperAPI |
| --- | --- | --- |
| Billing model | Per successful request, difficulty-tiered ladder; optional subscriptions | Flat monthly credit allowance, 7 plans |
| Entry price | $0 monthly fee (pay-as-you-go) | $49/mo (Hobby), $0 free plan |
| Subscription range | $99–$599/mo | $49–$1,975/mo |
| Standard request cost | $3.00 falling to $0.02 per 1,000 | 1 credit per standard page |
| Hard-target pricing | Difficulty multiplier ×1 to ×20, applied to whole group | Amazon 5, Google/Bing 25, LinkedIn 30 credits; +10 for Cloudflare/Datadome/PerimeterX bypass |
| JS rendering | ×2 credits on any request | Included as a feature; third-party comparisons report roughly 5–10 credits per rendered call |
| Annual discount | 1 month free + 8% off | 10% off |
| Free tier | 1,000 credits, up to 5,000 after setup steps, no card | 1,000 free credits on signup; 7-day trial with 5,000 credits |
| Failed requests | Not charged | Automatic retries included |
| Structured data | Raw HTML or rendered content; you write parsers | Pre-built parsers for Amazon, Google Search, Walmart returning clean JSON |
| Non-engineer workflow | API integration at every step | DataPipeline: no-code scheduling, output to Google Sheets or cloud storage |

Both companies run anti-bot handling, rotating residential proxies, and CAPTCHA processing inside the base request price — neither charges those as line items.

## ScraperAPI's full plan lineup

If the comparison leans ScraperAPI for your use case, here's the complete current list from its pricing page. Every paid tier includes JavaScript rendering, premium residential and mobile IPs, advanced bypassing, parsing and structured data APIs, DataPipeline access, and pay-as-you-go capability on the upper tiers.

| Plan | Monthly price | Annual (per month) | Credits | Concurrent threads | Get started |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 | $44.10 | 100,000 | 20 | [ Start Hobby](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [ Start Startup](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [ Start Business](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [ Start Scaling](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [ Start Professional](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [ Start Advanced](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | Custom | — | 22M+ | 500+ | [ Talk to sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

Two limits worth knowing before you commit: Hobby and Startup only offer geotargeting for the US and EU — country-level targeting starts at Business. And on concurrency, exceeding your thread limit returns a 429 response telling you to drop back; requests are rejected rather than queued, with no extra charge.

When your credits run out, scraping pauses by default until the next renewal. Hobby through Professional can opt into auto-upgrade, which bumps you to the next plan automatically. Scaling and above can instead use pay-as-you-go at a fixed per-credit rate, capped by a monthly spend limit you set yourself. 👉 [Check what your target sites cost on ScraperAPI](https://www.scraperapi.com/pricing?fp_ref=coupons) before picking a tier — the Domain Cost Estimator will tell you whether that $149 plan covers your workload or burns out in a week.

## Free tiers: how each one actually works

Crawlbase gives every new account 1,000 free credits with no card on file, and completing setup steps grows that to as much as 5,000. The credits work across every product, which makes it easy to test the Crawling API and the Smart AI Proxy against your real targets before paying anything.

ScraperAPI splits its free capacity in two: a permanent free plan with 1,000 API credits (maximum 5 concurrent connections), and a 7-day trial with 5,000 credits that doesn't require a credit card. If you need extra credits specifically for testing, support can grant more. Between the two, ScraperAPI's trial is the faster way to put a meaningful volume through real pages; Crawlbase's setup-step credits require a bit more legwork but stretch further across products.

Either way, both vendors' free tiers are large enough to run several hundred requests against your actual target list — which is the only reliable way to know what your difficulty tier or credit costs will look like in practice. 👉 [Try ScraperAPI free with 5,000 credits for 7 days](https://www.scraperapi.com/signup?fp_ref=coupons)

## Which pricing model fits your workload

Neither model wins outright; they reward different crawl profiles.

**Crawlbase's tiered pricing fits you if:**
- Your crawl list is mostly Standard or Moderate sites, where the ×1–×1.5 multipliers keep the ladder rates close to the headline figures.
- You want zero commitment — pay-as-you-go with no monthly fee and billing only for delivered pages suits project-based or spiky workloads.
- You're running high-volume mixed-difficulty pipelines (the 1M–500M request range) and want cost to scale down as volume grows. Third-party comparisons consistently call this model more predictable at scale for engineering teams.
- You're wiring LLM agents (Claude, Cursor, Windsurf) to live web data — Crawlbase ships a production-ready MCP server with anti-bot handling built in.

**ScraperAPI's flat-credit model fits you if:**
- You need structured JSON from Amazon, Google Search, or Walmart without writing or maintaining parsers. The pre-built endpoints survive target-site DOM changes; Crawlbase has no equivalent, so you'd write your own extraction logic.
- Non-engineers on your team need to schedule recurring scraping jobs — DataPipeline handles this visually, outputting to Google Sheets or cloud storage, where Crawlbase requires API integration at every step.
- Your volume sits in the 100K–3M monthly range, where ScraperAPI's Startup ($149) and Business ($299) tiers land below Crawlbase's equivalent-capacity subscriptions ($349 for 1M, and Growth tops out at 2M for $599).

One caveat from independent benchmarking cited in third-party comparisons: on heavily protected targets, ScraperAPI's success rate has been measured around 63% versus Scrapfly's 96%, though that gap narrows at enterprise configurations. Crawlbase doesn't publish comparable numbers either way, so test both against your targets before scaling spend.

## FAQ

**Is Crawlbase really free to start?**
Yes. New accounts get 1,000 free credits with no credit card, growing to up to 5,000 after completing setup steps, and the free credits apply to every product. Paid subscriptions are commitment-free and can be stopped or changed anytime.

**Does Crawlbase charge for failed requests?**
No. Only delivered pages count as billable. A request that gets blocked or returns nothing costs nothing, which is why cost tracks output rather than attempts.

**How much does scraping Google cost on Crawlbase?**
That depends on which difficulty tier Google's domains land in, and Crawlbase applies the multiplier automatically to the group's ladder total — it doesn't publish a fixed per-domain figure for Google the way ScraperAPI does (25 credits per request there). Use Crawlbase's on-site pricing calculator with your request type and domain complexity to get a concrete estimate.

**Is annual billing worth it on either platform?**
On Crawlbase, yearly billing means one month free plus 8% off — Scale 1M drops from $4,188 billed monthly to $3,839. On ScraperAPI, annual takes 10% off every tier, so Startup falls from $149 to $134.10 per month. Both are meaningful if your volume is stable; if it isn't, monthly billing keeps you flexible with no lock-in on either side.

## The final call

Match the decision to your crawl list, not to a leaderboard. Mostly static, easy targets at serious volume → Crawlbase's ladder and multipliers will treat you well, and its pay-as-you-go mode costs nothing to keep idle. Amazon/Google/Walmart data feeds, structured JSON without parser maintenance, or analysts who need scheduled jobs without writing code → ScraperAPI's model was built for exactly that, and its free trial lets you verify it before spending a dollar.

Two things to confirm before you pay anyone: run a few hundred requests against your three hardest targets on the free tier, and check the per-request credit cost for each of them. The sticker price on the plan page means very little until you know what your specific URLs actually consume. When you're ready, 👉 [compare ScraperAPI's plans and pick the tier that matches your credit math](https://www.scraperapi.com/pricing?fp_ref=coupons).
