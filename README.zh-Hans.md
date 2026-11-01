[English](README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md)

# Awesome AI Solopreneur [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> 为独自经营业务、与 AI 智能体团队协作的人精选的资源清单，经过实际使用检验。

英语 | [日本語](README.ja.md)

经营业务才是目的。你的 AI 组织（具备角色分工、任务路由和审查机制的智能体）与市场进入策略，都是服务于这门单人业务的工具，而不是各自独立的业余爱好。清单中的每个条目都用一两句话说明，它为什么值得在日常工作中使用。每节末尾的**实践心得**来自实际运行这套体系的经验，而非对链接内容的摘要。

标注 *(Kazuaand)* 的条目是维护者自己的开源文章与工具。

<a id="contents"></a>
## 目录

- [原则](#principles)
- [AI 组织](#ai-organization)
  - [角色与委派](#roles-and-delegation)
  - [验证与审查](#verification-and-review)
  - [何时询问人类](#when-to-ask-the-human)
- [智能体运行框架与运维](#harness-and-operations)
  - [指令与上下文](#instructions-and-context)
  - [记忆与决策](#memory-and-decisions)
  - [任务与工作恢复](#tasks-and-resuming-work)
  - [会话与上下文窗口](#sessions-and-the-context-window)
- [市场进入策略](#go-to-market)
  - [定位与产品方案](#positioning-and-offers)
  - [内容、搜索与 AI 搜索](#content-search-and-ai-search)
  - [发布推广](#launching)
- [安全发布](#safe-publishing)
- [衡量与成本](#measurement-and-cost)
- [参与贡献](#contributing)
- [许可证](#license)

<a id="principles"></a>
## 原则

- [做那些无法规模化的事](https://paulgraham.com/ds.html) - 最初几轮先亲手做。对独立经营者来说，手动走一遍流程，才能知道哪些步骤值得交给智能体。
- [MAKE](https://readmake.com/) - 一本从想法到收入、不依赖团队的独立创业手册。它依然是关于一个人能做出什么的最直白的论述。
- [构建有效的智能体](https://www.anthropic.com/research/building-effective-agents) - 从最简单、能奏效的模式开始。许多所谓的“智能体问题”，实际上是工作流问题。
- [智能体构建实用指南](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf) - 何时值得使用智能体、如何添加护栏，以及如何在智能体之间移交任务。动手前值得过一遍的检查清单。

> **实践心得**
>
> - 尽量减少需要你亲自承担的事项。边际成本和心智负担接近零的策略，都可以让智能体去执行。
> - 把注意力放在方向上：解决什么问题、为谁解决，以及结果是否体现了恰当的判断与品位。把约定条件的检查交给机器。

<a id="ai-organization"></a>
## AI 组织

<a id="roles-and-delegation"></a>
### 角色与委派

- [Graph Compound Engineering](https://github.com/Kazuaand/graph-compound-engineering) *(Kazuaand)* - 一本将跨多天的工作交给智能体的手册：编写规格说明、工作图和组织架构图，按决策的分量配置各个岗位，并通过每次复盘让下一项工作更容易。
- [Agent Delegation Playbook](https://github.com/Kazuaand/agent-delegation-playbook) *(Kazuaand)* - 何时把工作交给子智能体、何时自己动手，如何写任务说明，要求它返回什么，以及该用哪一档模型和推理强度。
- [我们如何构建多智能体研究系统](https://www.anthropic.com/research/multi-agent-research-system) - 坦诚讨论并行分派任务的 token 成本，以及任务简报对结果有多大影响。
- [复利工程](https://every.to/chain-of-thought/compound-engineering-how-every-codes-with-agents) - 每一项工作都应让下一项更容易。这是“复利”循环的思想来源。
- [Compound Engineering plugin](https://github.com/EveryInc/compound-engineering-plugin) - 一套已实现的规划、执行、审查与积累改进循环，可安装使用，也可阅读其实现。
- [Awesome Graph Engineering](https://github.com/DEEP-JLU/Awesome-Graph-Engineering) - 将图、循环、运行框架、上下文和提示词工程放在一起讨论的综述与论文清单，有助于理解自己的体系处于什么位置。
- [Claude Code 子智能体](https://code.claude.com/docs/en/sub-agents) - 独立上下文窗口和按智能体配置工具的实际工作方式。

> **实践心得**
>
> - 是否委派，只需问一个问题：你希望原始中间输出（文件全文、抓取结果、试错过程）进入自己的上下文吗？如果不希望，就委派出去。
> - 委派之前，先尝试把材料移出上下文窗口：存入文件，只保留路径和少量关键信息。
> - 用文件路径传递任务简报，不要重新讲一遍摘要。每份简报都要有预算和停止条件。
> - 要求每次回报都以一行清单收尾，列明哪些问题已解决、哪些仍未解决。
> - 绝不让执行者给自己的成果打分。使用全新的上下文进行审查。

<a id="verification-and-review"></a>
### 验证与审查

- [你的 AI 产品需要评测](https://hamel.dev/blog/posts/evals/) - 先看真实的失败案例，再设计指标。对小团队最有用的评测建议。
- [promptfoo](https://github.com/promptfoo/promptfoo) - 可在 CI 中运行、可重复执行的提示词与智能体测试。
- [Claude Code hooks](https://code.claude.com/docs/en/hooks) - 每次工具调用时运行的确定性检查。适合落实那些仅靠指令无法守住的边界。

> **实践心得**
>
> - 把每项说法都当作假设：交接笔记、记忆文件、子智能体报告，以及你自己缓存下来的判断。在据此开展工作前，先用成本最低的方法尝试证伪。
> - “不存在”至少需要三项独立检查来支持。一次搜索没有结果，说明不了多少问题。
> - 被测系统不能自行证明自己没有问题。它自己的测试全绿或成功提示，不能排除时序或环境错误。
> - 部署或修改配置后，用退出码断言预期状态是否成立，不要只靠目测输出。
> - 给每项高风险操作划分等级：自动执行、加护栏后执行、需要人类介入，或禁止执行。表中没有对应条目的操作，就不执行。

<a id="when-to-ask-the-human"></a>
### 何时询问人类

- [衡量实际工作中的 AI 智能体自主性](https://www.anthropic.com/research/measuring-agent-autonomy) - 基于数百万次人机交互的数据，观察智能体在两次人类介入之间能连续工作多久。

> **实践心得**
>
> - 子智能体向上级智能体提问，而不是直接问你。能依据此前的回答、规则或研究解决的事项，由上级处理。
> - 只有资金、对外消息、生产环境变更和方向问题才提交给人类，并集中在一轮中询问。
> - 每个问题都应附带建议、是否属于关键事项，以及非关键事项在何时之后按建议继续推进。
> - 沉默、超时和送达失败都不等于批准。

<a id="harness-and-operations"></a>
## 智能体运行框架与运维

<a id="instructions-and-context"></a>
### 指令与上下文

- [AGENTS.md](https://agents.md/) - 多种编程智能体都能读取的开放指令格式。维护一份共享源，为各个工具提供指向它的轻量适配层。
- [AI 智能体的有效上下文工程](https://www.anthropic.com/research/effective-context-engineering-for-ai-agents) - 上下文是一笔有限的预算。只加载下一步需要的内容。
- [Agent Skills](https://agentskills.io/home) - 将操作流程封装起来，仅在需要时加载。
- [anthropics/skills](https://github.com/anthropics/skills) - 可借鉴结构的技能示例。
- [Claude Code 记忆](https://code.claude.com/docs/en/memory) - 指令文件如何被发现、加载，以及加载顺序。
- [Model Context Protocol](https://modelcontextprotocol.io/) - 将工具和数据接入智能体的标准方式。
- [六边形架构](https://alistair.cockburn.us/hexagonal-architecture) - 端口与适配器。应用到 AI 工作中，就是保持流程阶段稳定，让每个工具和模型都成为可替换的适配器。

> **实践心得**
>
> - 每增加一条长期指令，就明确删去哪一条旧指令。规则堆积的速度，往往比模型对规则的实际需求增长得更快。

<a id="memory-and-decisions"></a>
### 记忆与决策

- [记录架构决策](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) - 简短决策记录的原始范式。记录“为什么”，才能防止智能体反复重开已经定案的问题。
- [架构决策记录模板](https://github.com/architecture-decision-record/architecture-decision-record) - 可直接作为起点的模板与示例。

> **实践心得**
>
> - 新决策取代旧决策时，将旧决策标记为已被取代，而不是删除它。

<a id="tasks-and-resuming-work"></a>
### 任务与工作恢复

- [beads](https://github.com/gastownhall/beads) - 专为智能体打造、以 git 为基础的议题跟踪工具。通过依赖图，一次查询就能回答“接下来可以做什么”。
- [为长时间运行的智能体构建有效框架](https://www.anthropic.com/research/effective-harnesses-for-long-running-agents) - 用进度文件加 git 历史，保存跨会话的记忆。

> **实践心得**
>
> - 任务状态只保留一个权威来源，即任务跟踪工具。工作经过写在进度文件中；信任两者之前，先与 git 日志核对。
> - 每完成一个工作单元就及时写入磁盘。运行中断后，只恢复尚未完成的单元，不重复已完成的工作。
> - 将后续工作登记为新议题，不要只在代码或聊天中留一个 TODO。

<a id="sessions-and-the-context-window"></a>
### 会话与上下文窗口

- [Claude Code 最佳实践](https://code.claude.com/docs/en/best-practices) - 长时间编程会话中，关于规划、上下文与验证的实用习惯。
- [充分发挥 Claude Code 会话的价值](https://claude.com/resources/articles/maximizing-the-value-of-your-claude-code-sessions) - 提高每个 token 使用价值的实用建议，包括提示词缓存如何影响会话成本。

> **实践心得**
>
> - 不要向缓存已失效的会话发送任何内容。一句“继续”或一次心跳，都可能导致整个上下文重新写入缓存，往往涉及数十万 token。
> - 只根据距上次成功响应的时间，以及进程是否仍在运行，判断缓存是否仍然有效。无法判断时，就按已失效处理。
> - 对缓存已失效的会话，把请求写入它将读取的文件；或者带着交接笔记，启动一个小型新会话。
> - 将大量读取、扫描和抓取交给上下文隔离的子智能体，只收回简短摘要或文件路径。
> - 不要让测试和构建输出占用主上下文窗口。只回传失败信息。

<a id="go-to-market"></a>
## 市场进入策略

<a id="positioning-and-offers"></a>
### 定位与产品方案

- [April Dunford 的著作](https://www.aprildunford.com/books) - 一套可重复使用的方法，先理清定位，再将其转化为销售表达。

> **实践心得**
>
> - 衡量借助 AI 扩大产出的成效，要看承接了多少需求，而非生产了多少内容。
> - 为人类读者起草任何内容前，先依据证据写清楚读者是谁。将同一份简短说明交给创作者和审查者。

<a id="content-search-and-ai-search"></a>
### 内容、搜索与 AI 搜索

- [创建实用、可靠、以人为本的内容](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) - Google 官方的自查问题。用它们检查你的 AI 辅助草稿。
- [AI 功能与你的网站](https://developers.google.com/search/docs/appearance/ai-features) - Google 的 AI 搜索功能如何使用你的网页，并链接到它们。
- [llms.txt](https://llmstxt.org/) - 一种旨在帮助语言模型读取网站的纯文本索引提案。
- [Schema.org](https://schema.org/) - 结构化数据词汇体系。当 AI 回答开始引用你时，实体信息的一致性会变得更加重要。
- [Open Graph 协议](https://ogp.me/) - 控制链接被分享时的展示方式。
- [Google Search Console](https://search.google.com/search-console/about) - 免费查看搜索排名以及网站存在的问题。
- [PageSpeed Insights](https://pagespeed.web.dev/) - 利用真实用户数据快速检查性能。

> **实践心得**
>
> - 在所有收录你的网站上，保持名称、描述和链接一致。实体信息不一致，对 AI 回答的影响比对传统搜索更大。
> - 某些社交平台对任意帖子 ID 都返回 HTTP 200，不论帖子是否真实存在。要确认帖子存在，应将爬虫看到的文本（例如 `og:description` 标签）与你发布的内容进行比较。

<a id="launching"></a>
### 发布推广

- [Show HN 指南](https://news.ycombinator.com/showhn.html) - 哪些内容符合要求，以及如何介绍一个别人能亲自试用的作品。

> **实践心得**
>
> - 为产品维护一份事实文件，包含一句话介绍、目标受众、定价和链接。各平台的收录资料都从这份文件生成，不要每次手动重写。
> - 用一张表跟踪所有收录记录：平台、时间、状态和链接。之后再次检查实际页面；目录站会变化，有时也会移除条目。

<a id="safe-publishing"></a>
## 安全发布

- [publish-gate](https://github.com/Kazuaand/publish-gate) *(Kazuaand)* - 公开任何内容之前的四阶段检查关卡：独立检测器、保存在仓库之外的私密禁用词清单、两位均须在全新上下文中审查并给出通过结论的 AI 审查者，以及必须先通过的预先植入敏感信息样本的自测。
- [gitleaks](https://github.com/gitleaks/gitleaks) - 面向 git 仓库和目录的快速敏感信息扫描工具。
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) - 查找敏感信息，并可验证发现的凭据是否仍然有效。
- [Presidio](https://github.com/data-privacy-stack/presidio) - 检测文本中的姓名、地址、电话号码等个人数据。
- [leakgate](https://pypi.org/project/leakgate/) - 发布前检查关卡，补足通用扫描器的盲区：检测代码和智能体会话记录中的本地用户名、内部主机和未公开项目的专有词语。
- [关于敏感信息扫描](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning) - GitHub 会帮你发现什么，以及不会发现什么。
- [设置提交邮箱地址](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address) - 使用 noreply 地址，避免提交记录暴露个人邮箱。
- [关于通行密钥](https://docs.github.com/en/authentication/authenticating-with-a-passkey/about-passkeys) - 为发布内容所用的账户采用抗钓鱼的登录方式。

> **实践心得**
>
> - 在同一次运行中，预先植入敏感信息样本的自测通过之前，扫描器的零命中结果没有意义。
> - 面向源代码设计的扫描器会漏掉许多写在自然语言或 HTML 中的凭据。为“标签: 值”形式的文本补充自定义规则，并在去除 HTML 标签后重新扫描。
> - 发布一个全新的仓库，只包含最终检查过的文件树。工作历史中可能仍然保留着已删除的内容。
> - 将私密词语的禁用清单放在公开仓库之外，在检查时传入。

<a id="measurement-and-cost"></a>
## 衡量与成本

- [提示词缓存（Anthropic）](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) - 缓存有效期，以及写入与读取的价格差异。长时间运行的智能体能否持续运作，很大程度上取决于此。
- [提示词缓存（OpenAI）](https://developers.openai.com/api/docs/guides/prompt-caching) - 另一家供应商的同类机制。使用多家供应商时值得了解。
- [管理 Claude Code 成本](https://code.claude.com/docs/en/costs) - 内置的支出查看与限制方法。
- [ccusage](https://github.com/ccusage/ccusage) - 基于本地智能体日志生成用量与成本报告。
- [LiteLLM](https://github.com/BerriAI/litellm) - 用一个网关接入多家模型供应商。按模型组路由，并避免将个人数据送往免费服务层。
- [Langfuse](https://github.com/langfuse/langfuse) - 面向 LLM 应用的开源追踪与评测工具。
- [Plausible Analytics](https://github.com/plausible/analytics) - 轻量、注重隐私且支持自托管的网站分析工具。
- [Umami](https://github.com/umami-software/umami) - 另一个简单、可自托管的网站分析方案。
- [监控分布式系统](https://sre.google/sre-book/monitoring-distributed-systems/) - 四大黄金信号，以及为什么每条告警都必须有人处理。

> **实践心得**
>
> - 成本报告分成三列：按标准费率计算的成本、实际消耗的额度，以及额外支付的现金。订阅并不意味着用量免费。
> - 未知用量就写“未知”，绝不能记成零。
> - 先检查定时运行的后台自动化。在一次审计中，几乎全部用量都来自它们，而非人工发起的工作。
> - 即使所有缓存都有效，并行分派仍会消耗额度，因为每轮都要重读整个上下文。拆分工作之前，先检查剩余额度。
> - 维护一份清单，登记每个定时检查器及其输出的阅读者。无人查看的检查器，实际上已经悄无声息地失效了。
> - 分层判断：先做确定性检查，再用小型分类器，最后才将剩余问题交给大模型。

<a id="contributing"></a>
## 参与贡献

欢迎提出建议。请先阅读[贡献指南](contributing.md)。

<a id="license"></a>
## 许可证

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

在法律允许的最大范围内，贡献者已放弃本作品的所有著作权及相关权利。
