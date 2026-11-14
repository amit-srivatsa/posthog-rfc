# Battlecard: PostHog AI Observability

> **Status:** draft PR from an applicant. Every claim links to a public source, checked on 14 Nov 2026. Where PostHog's own pages disagree with each other, I say so. If a rep quotes something wrong because of this page, that's on me.

**Read time:** 4 minutes. **Use it:** five minutes before a call, or mid-call when someone says "but we already use Langfuse."

---

## The 20-second pitch

You shipped an AI feature. Now you need to know if it works, what it costs, and who it's for.

Most LLM tools stop at the trace. PostHog connects the trace to the **person**, their **session recording**, their **errors**, and your **business metrics**. Then it lets you **A/B test the prompt** with the feature flags you already use.

One tool. One bill. 100,000 events free every month.

## Who to pitch

**Good fit**
- Product teams shipping LLM features *inside* a product (chat, copilots, agents, summaries).
- Teams already on PostHog for analytics, replay or flags. This is the easiest expansion motion we have.
- Startups watching every dollar of model spend, per user and per feature.

**Poor fit (be honest, save everyone a month)**
- Teams whose main need is a **gateway**: caching, rate limits, fallbacks. We don't do that. ([source](https://posthog.com/blog/best-helicone-alternatives))
- ML platform teams whose core loop is **dataset-driven eval runs** and span-level annotation queues. Competitors are ahead here today. ([source](https://posthog.com/blog/posthog-vs-langfuse))

## Why we win

1. **Traces with a face.** "Every trace is a timeline of its generations and spans, with the person, total cost, and total latency attached." You can jump from a bad answer straight to the session replay. ([source](https://posthog.com/ai-observability))
2. **Prompt experiments, not prompt vibes.** Split users by feature flag. Compare cost, latency and eval pass rate per variant. ([source](https://posthog.com/blog/posthog-vs-langfuse))
3. **Cost by anything.** Cost is calculated automatically from model pricing. Slice it by user, plan, feature or segment with SQL. ([source](https://posthog.com/ai-observability))
4. **Failed calls become error tracking issues** automatically. No second tool, no second alert channel. ([source](https://posthog.com/ai-observability))
5. **Pricing that doesn't punish seats.** Unlimited seats, 100K events free, then $0.00035/event, dropping to $0.00006/event with volume. ([source](https://posthog.com/ai-observability))
6. **Open source, MIT core.** Self-host if you must. ([source](https://posthog.com/blog/best-langfuse-alternatives))

## Where we lose (say it before they do)

- **Gateway features.** None. If they need caching or fallbacks, they'll keep a gateway. That's fine: we sit next to it.
- **Eval depth.** Langfuse is "more mature" for eval pipelines, annotation queues and playground testing. Dataset-based eval runs are on our roadmap. ([source](https://posthog.com/blog/posthog-vs-langfuse))
- **Composable prompts.** Langfuse is further along. ([source](https://posthog.com/blog/best-langfuse-alternatives))
- **Newer product.** We say it ourselves: our tooling is "newer than some dedicated LLM observability platforms." ([source](https://posthog.com/blog/best-helicone-alternatives))

> **Rep note:** our own feature grid on the product page ticks "Datasets" and "Experiment runs", while our Langfuse comparison calls dataset evals "on the roadmap." Don't promise dataset experiments until product confirms. *(Flag for PMM: please reconcile.)*

## Competitor snapshot

| | **Langfuse** | **Helicone** | **Datadog** | **PostHog** |
|---|---|---|---|---|
| What it is | Dedicated LLM engineering platform | Proxy/gateway with observability | APM giant with LLM and agent observability | Product OS with AI observability built in |
| Free tier | 50K units/mo, 2 users, 30-day data | 10K requests, 1 seat, 7-day data | Up to 40K LLM spans *(verify)* | 100K events/mo, unlimited seats |
| Paid entry | Core $29/mo + $8 per 100K units | Pro $79/mo + usage | Pro $160/mo, 100K spans *(verify)* | $0.00035/event, down to $0.00006 |
| They beat us on | Evals, datasets, annotation, composable prompts | Gateway: caching, rate limits, fallbacks | Existing APM footprint, enterprise RBAC | |
| We beat them on | Product context, replay, flags, experiments, seats | Product context, depth beyond requests | Price, product context, speed to value | |

Sources: [Langfuse pricing](https://langfuse.com/pricing), [Helicone pricing](https://www.helicone.ai/pricing), [Datadog](https://www.datadoghq.com/products/ai/agent-observability/), [PostHog](https://posthog.com/ai-observability). Competitor prices change often. Check before you quote a number in writing.

## Objection handling

**"We already use Langfuse."**
Great, keep it if your ML team lives in its eval tooling. But who answers "did the new prompt make users churn less?" Langfuse shows the trace. We show the trace, the user, the replay and the retention curve. And you don't have to rip anything out: PostHog can ingest traces forwarded from Langfuse. ([source](https://posthog.com/docs/llm-analytics))

**"We need caching and rate limiting."**
Then you need a gateway, and we're not one. Keep your gateway for traffic control. Use PostHog to understand what that traffic did for the product. Different jobs.

**"Datadog already watches everything."**
Datadog tells you the service is up. It's built for the on-call engineer. We're built for the person deciding whether the AI feature is worth keeping. Ask them: who on your team looks at LLM cost per customer today, and in which tool?

**"You're newer. Is it mature enough?"**
Yes, for tracing, costs, errors, prompt experiments and evals on live traffic. Not yet, if your whole workflow is offline dataset experiments. I'd rather tell you that now than in month three.

**"We can't send prompts and outputs to a third party."**
Privacy mode excludes sensitive input and output from capture. You still get cost, latency, tokens and errors. ([source](https://posthog.com/ai-observability)) Self-hosting is also an option.

**"It's cheaper to roll our own logging."**
For a week, sure. Then someone asks for cost per user per model, a replay of the bad answer, and an A/B test on the prompt. That's three projects. The first 100K events a month are free, so the test costs nothing.

## Discovery questions

1. What AI features are live today, and who owns whether they're "working"?
2. How do you know a bad answer happened? A user complaint, an eval, or a guess?
3. Do you know your LLM cost per customer? Per plan?
4. When you change a prompt, how do you decide it was better?
5. What's already in your stack for analytics, replay and flags?

The answer to question 5 decides the call. If it's PostHog, this is an expansion. If it's three other tools, it's a consolidation story.

## Demo in four clicks

1. A trace with a wrong answer.
2. The person behind it, and their session replay.
3. The cost of that user's AI usage this month.
4. The prompt experiment that fixed it, with pass rates per variant.

## Landmines (don't say these)

- "We replace your gateway." We don't.
- "We have dataset experiments." Not confirmed yet. See the rep note above.
- Competitor acquisition gossip. Ownership news in this space moves weekly. Check it before you repeat it.

## Still missing (what I'd ask for in Slack, day one)

- [ ] Two customer stories with numbers. I couldn't find public ones I trust.
- [ ] Top 5 real objections from Gong calls tagged "AI observability." This card is built from public pages, so it's my best guess at the objections, not the real list.
- [ ] Win/loss notes against Langfuse.
- [ ] PMM confirmation on datasets and experiment runs.

---

*Built in an afternoon from public pages, with Claude for research and me for every judgment call. Every number has a link. That's the standard I'd hold my enablement to.*
