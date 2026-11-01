# Awesome AI Solopreneur [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated, practice-tested list for people who run a business alone with a team of AI agents.

English | [日本語](README.ja.md)

The business is the point. Your AI organization (agents with roles, routing and review) and your go-to-market are tools inside that one-person business, not separate hobbies. Every entry here says, in a line or two, why it earned its place in daily use. Each section ends with **From practice** notes: lessons from running this setup, not summaries of the links.

Entries marked *(Kazuaand)* are the maintainer's own open-source write-ups and tools.

## Contents

- [Principles](#principles)
- [AI organization](#ai-organization)
  - [Roles and delegation](#roles-and-delegation)
  - [Verification and review](#verification-and-review)
  - [When to ask the human](#when-to-ask-the-human)
- [Harness and operations](#harness-and-operations)
  - [Instructions and context](#instructions-and-context)
  - [Memory and decisions](#memory-and-decisions)
  - [Tasks and resuming work](#tasks-and-resuming-work)
  - [Sessions and the context window](#sessions-and-the-context-window)
- [Go-to-market](#go-to-market)
  - [Positioning and offers](#positioning-and-offers)
  - [Content, search and AI search](#content-search-and-ai-search)
  - [Launching](#launching)
- [Safe publishing](#safe-publishing)
- [Measurement and cost](#measurement-and-cost)
- [Contributing](#contributing)
- [License](#license)

## Principles

- [Do Things that Don't Scale](https://paulgraham.com/ds.html) - Do the first runs by hand. For a solo operator, that manual pass is how you learn which steps are worth handing to agents.
- [MAKE](https://readmake.com/) - An indie startup manual, from idea to revenue without a team. Still the plainest account of what one person can ship.
- [Building effective agents](https://www.anthropic.com/research/building-effective-agents) - Start with the simplest pattern that works. Many "agent" problems turn out to be workflow problems.
- [A practical guide to building agents](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf) - When an agent is worth it, how to add guardrails, and how to hand work between agents. A useful checklist before you build.

> **From practice**
>
> - Keep your own commitments few. Let agents run every tactic whose marginal cost and mental load are close to zero.
> - Spend your attention on direction: what problem, for whom, and whether the result has the right taste. Leave contract checks to machines.

## AI organization

### Roles and delegation

- [Graph Compound Engineering](https://github.com/Kazuaand/graph-compound-engineering) *(Kazuaand)* - A handbook for handing multi-day work to agents: write a spec, a work graph and an org chart, seat each role by the weight of its decisions, and let each retro make the next job easier.
- [How we built our multi-agent research system](https://www.anthropic.com/research/multi-agent-research-system) - Candid about what fan-out costs in tokens and how much the brief decides the result.
- [Compound engineering](https://every.to/chain-of-thought/compound-engineering-how-every-codes-with-agents) - The idea that each unit of work should make the next one easier. The origin of the "compound" loop.
- [Compound Engineering plugin](https://github.com/EveryInc/compound-engineering-plugin) - A working plan, work, review and compound cycle you can install and read.
- [Awesome Graph Engineering](https://github.com/DEEP-JLU/Awesome-Graph-Engineering) - A survey and paper list that places graph, loop, harness, context and prompt engineering side by side. Useful for seeing where your own setup sits.
- [Claude Code subagents](https://code.claude.com/docs/en/sub-agents) - How isolated context windows and per-agent tools work in practice.

> **From practice**
>
> - One question decides delegation: do you want the raw intermediate output (file dumps, fetch results, trial and error) in your own context? If not, delegate.
> - Before delegating, try moving the material out of the window: put it in a file and keep only the path and a few facts about it.
> - Brief with a file path, not a retold summary. Give every brief a budget and a stop point.
> - Ask every return to end with one line listing which questions are closed and which are still open.
> - Never let the maker grade its own work. Review in a fresh context.

### Verification and review

- [Your AI Product Needs Evals](https://hamel.dev/blog/posts/evals/) - Look at real failures before you design metrics. The most useful eval advice for small teams.
- [promptfoo](https://github.com/promptfoo/promptfoo) - Repeatable prompt and agent tests that run in CI.
- [Claude Code hooks](https://code.claude.com/docs/en/hooks) - Deterministic checks that run on every tool call. Use them for boundaries an instruction alone cannot hold.

> **From practice**
>
> - Treat every claim as a hypothesis: handoff notes, memory files, a sub-agent's report, and your own cached assumptions. Run the cheapest disproof before you build on it.
> - "It isn't there" needs at least three independent checks. One empty search proves little.
> - The system under test cannot clear itself. Its own green tests or success toast do not disprove a timing or environment bug.
> - After a deploy or config change, assert the expected state with an exit code instead of reading the output by eye.
> - Give each risky action a tier: run automatically, run with a guard, needs a human, or never. If an action has no row in the table, it does not run.

### When to ask the human

- [Measuring AI agent autonomy in practice](https://www.anthropic.com/research/measuring-agent-autonomy) - Data from millions of human-agent interactions on how long agents now work between human turns.

> **From practice**
>
> - Sub-agents ask their parent, not you. The parent settles what earlier answers, rules or research can settle.
> - Only money, outbound messages, production changes and direction reach the human, bundled into one round.
> - Each question carries a recommendation, whether it is critical, and a time after which a non-critical one proceeds with the recommendation.
> - Silence, timeouts and failed delivery are never approval.

## Harness and operations

### Instructions and context

- [AGENTS.md](https://agents.md/) - One open instruction format read by many coding agents. Keep one shared source and give each tool a thin adapter that points to it.
- [Effective context engineering for AI agents](https://www.anthropic.com/research/effective-context-engineering-for-ai-agents) - Context is a finite budget. Load only what the next step needs.
- [Agent Skills](https://agentskills.io/home) - Package a procedure so it loads only when it is needed.
- [anthropics/skills](https://github.com/anthropics/skills) - Example skills to copy the structure from.
- [Claude Code memory](https://code.claude.com/docs/en/memory) - How instruction files are found and loaded, and in what order.
- [Model Context Protocol](https://modelcontextprotocol.io/) - The standard way to plug tools and data into agents.
- [Hexagonal architecture](https://alistair.cockburn.us/hexagonal-architecture) - Ports and adapters. Applied to AI work: keep the stages stable and make every tool and model a swappable adapter.

> **From practice**
>
> - When you add a standing instruction, name one to remove. Rules pile up faster than models need them.

### Memory and decisions

- [Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) - The original short decision record. Recording the "why" is what stops agents from reopening settled questions.
- [Architecture decision record templates](https://github.com/architecture-decision-record/architecture-decision-record) - Templates and examples to start from.

> **From practice**
>
> - When a decision replaces an older one, mark the old one as superseded instead of deleting it.

### Tasks and resuming work

- [beads](https://github.com/gastownhall/beads) - A git-backed issue tracker built for agents. Its dependency graph turns "what can I do next?" into a single query.
- [Effective harnesses for long-running agents](https://www.anthropic.com/research/effective-harnesses-for-long-running-agents) - A progress file plus git history as the memory between sessions.

> **From practice**
>
> - Keep one source of truth for task state (the tracker). Keep the story in a progress file, and check both against the git log before you trust them.
> - Write each finished unit to disk as you go. An interrupted run should resume the missing units only, never redo finished ones.
> - File follow-up work as a new issue instead of leaving a TODO in code or chat.

### Sessions and the context window

- [Claude Code best practices](https://code.claude.com/docs/en/best-practices) - Practical habits for planning, context and verification in long coding sessions.
- [Maximizing the value of your Claude Code sessions](https://claude.com/resources/articles/maximizing-the-value-of-your-claude-code-sessions) - Practical tips for getting more from every token, including how the prompt cache shapes session cost.

> **From practice**
>
> - Do not send anything to a session whose cache has gone cold. One "continue" or heartbeat can rewrite its whole context, often hundreds of thousands of tokens.
> - Judge warmth only by the time since the last successful response and whether the process is alive. If you cannot tell, treat it as cold.
> - For a cold session, leave the request in a file it will read, or start a small fresh session with a handoff note.
> - Push heavy reads, scans and fetches into isolated sub-agents and take back a short distillate or a path.
> - Keep test and build output out of the main window. Return failures only.

## Go-to-market

### Positioning and offers

- [April Dunford's books](https://www.aprildunford.com/books) - A repeatable way to work out positioning, then turn it into a sales pitch.

> **From practice**
>
> - Measure AI-scaled output by demand captured, not by volume produced.
> - Before drafting anything for a human reader, write down who that reader is, from evidence. Give the same short brief to the maker and the reviewer.

### Content, search and AI search

- [Creating helpful, reliable, people-first content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) - Google's own self-assessment questions. Run your AI-assisted drafts through them.
- [AI features and your website](https://developers.google.com/search/docs/appearance/ai-features) - How Google's AI search features use and link to your pages.
- [llms.txt](https://llmstxt.org/) - A proposed plain-text index that helps language models read your site.
- [Schema.org](https://schema.org/) - Structured data vocabulary. Consistent entity data matters more once AI answers cite you.
- [The Open Graph protocol](https://ogp.me/) - Controls how your links look when shared.
- [Google Search Console](https://search.google.com/search-console/about) - Free data on what you rank for and what is broken.
- [PageSpeed Insights](https://pagespeed.web.dev/) - Quick performance checks with field data.

> **From practice**
>
> - Keep your name, description and links identical everywhere you are listed. Inconsistent entity data costs more in AI answers than in classic search.
> - Some social platforms return HTTP 200 for any post ID, real or not. To confirm a post exists, compare the text a crawler sees (for example the `og:description` tag) with what you posted.

### Launching

- [Show HN guidelines](https://news.ycombinator.com/showhn.html) - What qualifies, and how to present something people can try.

> **From practice**
>
> - Keep one fact file about the product (one-line pitch, audience, pricing, links). Generate each directory listing from it instead of rewriting by hand.
> - Track every listing in one table: where, when, status and link. Re-check the live listing later; directories change and sometimes drop entries.

## Safe publishing

- [publish-gate](https://github.com/Kazuaand/publish-gate) *(Kazuaand)* - A four-stage gate before anything goes public: independent detectors, a private denylist kept outside the repo, two fresh AI reviewers who must both pass, and a selftest with planted secrets that must pass first.
- [gitleaks](https://github.com/gitleaks/gitleaks) - Fast secret scanner for git repos and directories.
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) - Finds secrets and can check whether a found credential is still live.
- [Presidio](https://github.com/data-privacy-stack/presidio) - Detects personal data such as names, addresses and phone numbers in text.
- [leakgate](https://pypi.org/project/leakgate/) - A pre-publish gate for what generic scanners miss: local usernames, internal hosts and your own unpublished project terms, in code and agent transcripts.
- [About secret scanning](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning) - What GitHub catches for you, and what it does not.
- [Setting your commit email address](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address) - Use the noreply address so commits do not expose your personal email.
- [About passkeys](https://docs.github.com/en/authentication/authenticating-with-a-passkey/about-passkeys) - Phishing-resistant sign-in for the account you publish from.

> **From practice**
>
> - Zero hits from a scanner mean nothing until a selftest with planted secrets has passed on the same run.
> - Scanners built for source code miss many credentials written in prose or HTML. Add your own patterns for "label: value" text and re-scan with HTML tags stripped.
> - Publish a fresh repository holding only the final, checked tree. The working history may still contain what you removed.
> - Keep the denylist of private words outside the public repo and pass it in at check time.

## Measurement and cost

- [Prompt caching (Anthropic)](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) - Cache lifetimes and the price of writes versus reads. Long-running agents live or die by this.
- [Prompt caching (OpenAI)](https://developers.openai.com/api/docs/guides/prompt-caching) - The same mechanics on another provider. Worth knowing if you run more than one.
- [Manage costs in Claude Code](https://code.claude.com/docs/en/costs) - The built-in ways to see and limit spending.
- [ccusage](https://github.com/ccusage/ccusage) - Usage and cost reports built from local agent logs.
- [LiteLLM](https://github.com/BerriAI/litellm) - One gateway across many model providers. Route by model group, and keep personal data away from free tiers.
- [Langfuse](https://github.com/langfuse/langfuse) - Open-source tracing and evaluation for LLM apps.
- [Plausible Analytics](https://github.com/plausible/analytics) - Lightweight, privacy-friendly web analytics you can self-host.
- [Umami](https://github.com/umami-software/umami) - Another simple self-hostable analytics option.
- [Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/) - The four golden signals, and why every alert needs someone who acts on it.

> **From practice**
>
> - Report cost in three columns: cost at standard rates, credits actually consumed, and extra cash spent. A subscription does not make usage free.
> - Unknown usage stays "unknown". Never write it down as zero.
> - Look at scheduled background automations first. In one audit they, not human work, made up almost all usage.
> - Parallel fan-out burns quota even when every cache is warm, because each turn re-reads its whole context. Check your remaining quota before you spread work out.
> - Keep a registry of every scheduled checker and who reads its output. A checker nobody reads is silently dead.
> - Judge in a ladder: deterministic checks first, a small classifier next, and a large model only for what is left.

## Contributing

Suggestions are welcome. Please read the [contribution guidelines](contributing.md) first.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related rights to this work.
