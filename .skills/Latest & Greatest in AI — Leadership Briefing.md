Leadership briefing · Latest in AI

# Three shifts reshaping enterprise AI

Each topic follows the same path: what it is, how it works, why it matters, where it fits at the bank, and what to watch.

### 1Always-on agents

**Core difference:** AI that keeps working between conversations. It watches, remembers, prepares, then asks for approval.

OpenAI Dots · Meta Muse · Grok Bot · Google Gemini agent

### 2Decision models

**Core difference:** AI that decides instead of writes. It picks from a fixed list and scores its own confidence in a fraction of a second.

Jev · AWS Strands Decider · OpenAI Decisions API

### 3Ultrafast AI & Gemini 4 Argon

**Core difference:** AI that is faster, or can work far longer in one run, if you can pay for it and qualify for access.

OpenAI Ultrafast · Cerebras wafer-scale chips · Gemini 4 Argon

**The thread connecting all three:** autonomy is arriving together with control. Read-only modes, approval gates, confidence scores and gated access are now part of the product, and that is what a bank should evaluate first.

1 · Always-on agents · what it is and how it works

## From a tool you ask to a colleague you delegate to

**Today's chatbot**\
Waits for your prompt · forgets between sessions · you do the follow-up and the checking.

**Always-on agent**\
Watches your sources · remembers context · prepares the work overnight · returns only when it needs a decision.

Every product is built from the same five parts, like a new hire with a laptop, standing instructions, a notebook, app keys, and a manager who signs off on irreversible actions.

### 1Own computer

A persistent cloud machine with a browser, so it runs when your laptop is off. Dots connect to 4,000+ apps.

### 2Triggers

Schedules, events and standing goals. Example: "every morning at 8, brief me on AI news."

### 3Memory

Context persists for days. Team Bots share team knowledge while private chats stay isolated.

### 4Connectors

Direct app APIs where possible (Spark with Gmail), a browser where not, and MCP for outside tools.

### 5Permission gate

The control point. Dots: background research is read-only, enforced in code. Muse: a separate Sentinel agent approves outbound actions.

**Why it matters:** value comes from the loop (trigger, context, prepared action, human approval), not from a smarter chat window.

1 · Always-on agents · what differs and where it fits

## Same engine, different bets

| Product | Core difference | Best at | Watch-out |
| --- | --- | --- | --- |
| **OpenAI Dots** | Clearest published control model: read-only background research, rules to allow, ask or block | Personal and team work across ChatGPT, Slack, Teams | Memories outlive a disconnected app; admin enablement needed |
| **Meta Muse** | Security-first design: isolated machine, Sentinel approver, credential vault | Errands, purchases, reservations; now adding business app links | Consumer-first; enterprise consoles thin |
| **Grok Bot / Team Bots** | Named AI teammates, now a model router: picks the best backend per task (Claude Opus 5.5 for reasoning, Midjourney for images, Suno for music) | Sales briefs, engineering triage, live X trend monitoring | Routing is automatic with no reported off switch; the vendor mix can change, so data may reach several providers |
| **Gemini agent** (Google Cloud) | One enterprise agent across Workspace, Microsoft 365 and Slack; gets its own account, email and calendar; four kinds of memory; routes between Gemini and Claude; per-agent identity, activity log and hard spend caps | Cross-app work in mixed environments; a financial-services version is in preview | Private preview only |
| **Gemini Spark** | Real API access to Workspace, not screen-clicking | Email, calendar, document workflows | Workspace-centric; regional gaps |
| **Microsoft Autopilot** | Agent with its own identity and configurable permissions | Microsoft 365 work through Graph | Strongest inside the Microsoft stack |

### Use cases at the bank

- Overnight client brief for every relationship manager: news, calls, documents, what changed, what to do
- Continuous KYC and compliance monitoring that updates records and alerts before audits
- Transaction alert support: investigate, gather context, draft the report for a human
- Engineering triage: read tickets and chat, open issues, start fixes

### Why leaders care

- Work progresses off-hours
- Fewer handoffs and status meetings
- Context carries over instead of being re-explained

### Guardrails to require

- Read-only by default; approval for anything that changes state
- Its own identity per agent; shared tasks can see more than one person should
- Plan for prompt injection, the top-ranked LLM security risk

1 · Always-on agents · how they operate software

## Computer use is getting better by clicking less

Computer use lets an agent operate software built for humans. For a bank that matters because many legacy systems and vendor portals have no API. Reliability is improving through five shifts.

### 1Pixels → structure

Agents used to read screenshots only. Now they also read the page's underlying structure. In one benchmark this doubled Claude Opus 4.6's score (26% to 52%); vision-only frontier models clustered at 20–29%. Muse reads pages this way.

### 2Clicking → calling

Hybrid agents use commands, APIs and MCP tools where possible and click only as a last resort. One open model issued commands for 41–55% of its actions. Gemini agent draws on an enterprise tools registry; Dots connect 4,000+ apps.

### 3One step → batches

Agents now send several actions per turn (about 40% in that study), which cuts round trips and cost.

### 4Harder, honest tests

The classic OSWorld test is saturated at 79–83%. Its successor uses 108 long tasks of about 300 steps, and the best agent at launch fully completed only 20.6%. OpenAI reports GPT-6.1 Sol up seven points on it at under half the cost (vendor-reported).

### 5Cheaper and safer

Sol is within 2.1 points of Astra at roughly one-seventh the cost per task (OpenAI). Safety is moving into the design: separate approver agents, credential vaults, spend caps.

**Emerging option, WebMCP:** a proposed browser standard that lets a website publish safe, defined actions for agents instead of making them click through screens. It is experimental (Chrome and Edge origin trials) and needs both the site and the agent set up, so treat it as a pilot on one low-risk internal site while Playwright stays for testing.

**Bank takeaway:** computer use is the bridge to legacy screens, but long tasks still fail more often than they succeed. Use APIs first, computer use for the last mile, a human checkpoint at the end, and keep it away from irreversible actions. It also explains why testing agents can find breaks that fixed Playwright scripts miss.

Sources: OSWorld 2.0 paper, iOSWorld study, Qwen-UI-Agent report, OpenAI GPT-6.1 Sol post, Google Cloud, SpaceXAI.

2 · Decision models · what it is and how it works

## An "instinct" model: choose, score, move on

A language model writes an answer. A decision model never writes. It reads a situation and a fixed list of options, then returns a choice, a yes/no probability or a score, with a confidence.

Situation + options→One pass, no text generated→Choice or score + confidence→System acts or escalates

|  | Language model | Decision model |
| --- | --- | --- |
| Output | A paragraph to parse | A typed answer with a confidence |
| Time | Seconds | About 0.1 to 0.3 seconds |
| Cost | Billed per output word | Jev charges for input only |
| Best for | Open-ended work | Bounded, high-volume judgments |

### Jev (TypeSafe AI)

Hosted service. Trained so its confidence matches how often it is actually right. Speed reported at 70–500 ms.

### Strands Decider 2B (AWS)

Open model that runs on your own hardware. Takes a small language model, removes its text-writing ability, and adds a tiny scoring layer for the options. About 115 ms.

### OpenAI Decisions API

Limited preview, accepts text and images. Speed claimed near 150 ms; price and confidence behavior not yet published.

2 · Decision models · where it fits

## The fast lane in front of the expensive model

Incoming request→Decision model→Confident: act instantlyorUnsure: escalate to large model→High stakes: human

### Use cases at the bank

- Routing customer emails and calls by intent
- Triage: which fraud or compliance alerts deserve an analyst
- Document completeness checks ("is the signature block filled in?")
- Guardrail before an agent acts: "is this transfer within its authority?"

### Why leaders care

- Cuts cost and delay on high-volume yes/no work
- Open models can run inside the bank's environment
- Confidence scores create a natural review threshold
- Answers at 0.9+ confidence were right about 95% of the time on unseen short tasks (Strands)

### Honest limits

- Cannot write, summarize or hold a conversation
- Strands scores 72% overall on the public benchmark: 100% on easy tasks, 50% on hard ones
- Public tests are small and results vary widely between vendors

**Recommendation:** deploy as triage and guardrail, not as final approver of consequential actions such as security patches. Validate on the bank's own labeled cases before trusting any published number.

Bonus shift · Local AI

## Local AI: bring the model to the data, not the data to the model

Cloud AI sends your data to a vendor's servers. Local AI runs the model on your own laptop, workstation or servers. Google and Meta are both pushing in this direction, with different bets.

### Google: AI Edge Foresight

- Experimental Mac app that records meetings, transcribes offline, expands your shorthand into full notes, and answers questions from your own files
- Runs Gemma 4 plus EmbeddingGemma 2 (740M parameters, Apache 2.0); Gemma 4 12B fits laptops with 16 GB
- Privacy claim (nothing leaves the device) is Google's own

### Meta: Muse Glimmer

- 30B open-weight model (Apache 2.0) built for always-on agents on a single GPU or Mac Mini
- Distilled from Meta's closed flagship, Muse Spark
- Zuckerberg's framing: distribute AI widely instead of centralizing it

### Same direction, two tracks

- Both still run their strongest models in the cloud (Muse Spark is closed; Muse agents run on Meta's servers)
- Local handles private, routine work; cloud handles hard reasoning
- Hardware is following: Nvidia is shipping compact PCs for local agents

### Why leaders care

- Sensitive audio, documents and notes never reach a third party
- Works offline, with low delay and no per-token fee
- Weakens the objection that regulated firms cannot send transcripts to a vendor

### Use cases at the bank

- Notes for confidential deal, legal or regulatory calls
- Private search across local documents
- Small decision models at the edge for fast checks (Strands Decider runs locally)

### Watch-outs

- Smaller models are weaker on hard tasks
- Local apps can bypass central logging and controls, so endpoint management is essential
- Foresight is experimental and Mac-only

**Recommendation:** pilot local note-taking and document search with a small, managed group, and design a hybrid: local for sensitive routine work, cloud frontier models for hard reasoning, with logging in both.

Sources: Google Developers Blog and coverage (heise, Notebookcheck, TechCrunch via AI Weekly), Meta Connect recap, InfoQ, Engadget, Nvidia IFA 2026 post.

3 · Ultrafast AI · how it works

## Fast AI is a memory problem, not a math problem

An AI writes one word at a time, and each word needs the entire model read from memory. On a standard GPU the math units sit idle waiting for data. Speed comes from fixing that wait.

**Standard GPU**

Compute chip

⇄

Memory stacks off the chip\
\~3–4 TB/s

Model weights shuttle back and forth every word. The wait caps speed per user.

**Cerebras wafer-scale chip**

Compute and 44 GB of memory on one wafer-sized chip\
\~21 PB/s on-chip (Cerebras claims \~7,000×)

Weights live next to the cores, so there is far less waiting. The chip is about 56× larger than the biggest GPU die.

| Way to go faster | How it works | Trade-off |
| --- | --- | --- |
| **Wafer-scale memory** (Cerebras) | Weights held in on-chip memory; 1,000+ words per second reported on OpenAI's Codex-Spark | Only 44 GB per wafer, so big models span several; built for speed per user, not many users at once |
| **Low-batch GPU serving** | Give each user more of a GPU by sharing it with fewer people | Each word costs more, which is why a 6× speed-up carries a 6× price |
| **Leaner software path** | Persistent connections and streaming that trim delay around the model | Helps modestly; does not change the model |

### What OpenAI's Ultrafast is

Same model, faster serving: up to 6× faster in the API at 6× the price. OpenAI has not said what hardware serves the current tier, and an analyst report says it runs on GPUs. Earlier previews were attributed to Cerebras. AWS has also announced Cerebras for Bedrock.

### Use cases: when a human is waiting

- Live call-center and advisor copilots
- Real-time voice banking agents
- Trading-desk summaries of breaking news
- Interactive coding that feels instant

**Skip** batch and overnight jobs. Not offered on EU or Australian residency endpoints.

3 · Gemini 4 Argon

## An AI that can finish a whole job in one run

Most leading models can write about 128,000 tokens (roughly a long report) per response. Argon can write 1 million, built to stay on task through long, multi-step work.

### Core difference

Sustained output and long-horizon reasoning: migrate a large codebase, draft a long filing, or run a patch campaign without being cut off or losing the thread.

### Advantages (Google-reported)

- Long coding tasks: 77.9% vs 74.2% for Claude Opus 5.5
- Long agent workflows: 51.3% vs 42.5%
- Very long documents: 84.2% vs 66.8%
- Intro price $2 / $10 per million tokens, then $4 / $20

### Use cases at the bank

- Legacy code modernization
- Find, validate and patch vulnerabilities, easing the Run-the-Bank backlog
- Long financial research and legal drafting

### Reality check

- Available only to vetted defenders in Google's Fairwind Program (650+ organizations reported); not on the public API; no general date
- Independent index: 53 for Argon vs 58 for Opus 5.5, which leads terminal-style agent tasks (66% vs 57%)
- Benchmarks are vendor-reported and cannot yet be re-run by others

### Recommendation

- Plan on models you can buy now: a workhorse tier for volume and a frontier tier for hard work
- Ask Google about Fairwind-style access for a patching pilot
- Keep an independent checker and a human in any patch loop; the same skill that fixes flaws can find them

Sources: Google DeepMind, Cerebras and OpenAI technical material, AWS Strands Labs, TypeSafe AI, SpaceXAI, Meta, 9to5Google, Artificial Analysis, SemiAnalysis via OfficeChai.

3 · Gemini 4 Argon · versus the field and the chip economics

## Argon's price is a chip story; its cost per task is a token story

| Model | Independent index | Cost per task | Price per M tokens (in / out) | Max output | Stands out for |
| --- | --- | --- | --- | --- | --- |
| **Gemini 4 Argon** | 53 | $1.99 intro, $3.98 later | $2 / $10, then $4 / $20 | 1M | Long-horizon, legal and finance work |
| **Claude Opus 5.5** | 58 | $5.98 | $4 / $20 | 128K | Terminal-style agent coding |
| **Claude Sonnet 5.5** | 56 | not listed | $2 / $10 | 128K | Everyday workhorse |
| **GPT-6 Astra** | 53 | $3.26 | $10 / $50 | 128K | Frontier coding |
| **GPT-6.1 Sol** | 52 | $0.72 | $2 / $10 | 128K | Best value |

### Why chips show up in price

- Google designs its own TPU chips, so it avoids most of the margin GPU buyers pay (Nvidia's gross margin is estimated near 75%)
- Independent tests: Google's TPU v7 serves tokens for about $0.18 per million versus $0.22 on Nvidia B200 and $0.28 on B300 at the same per-user speed
- Google says Gemini serving costs fell 78% in 2025

### Caveats

- Google has not disclosed the hardware behind Argon; TPUs are the likely driver, not a confirmed one
- TPU rental list prices are not cheaper than GPUs; the edge is chip-to-model co-design

### Where the advantage ends

- After the intro period, Argon's list price equals Opus 5.5's
- Argon used about 62,000 output tokens per task versus 27,000 for Astra, and costs roughly 2.7× Sol per task

**Three chips, three price signals:** Cerebras wafer-scale buys speed at a premium, TPUs buy a lower cost per token, GPUs remain the general-purpose benchmark. Budget per completed task, and model both the intro and standard rates.

Sources: Artificial Analysis and Vals via eesel.ai, NeuralTrust, Fello AI; SemiAnalysis InferenceX; SemiAnalysis TPUv7 analysis; io-fund.