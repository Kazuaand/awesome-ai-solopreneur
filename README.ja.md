[English](README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md)

# Awesome AI Solopreneur [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> AI agent のチームを使って、一人で事業を回す人のための厳選リスト。実際に使って残ったものだけを載せています。

[English](README.md) | 日本語

主役は事業そのものです。AI 組織 (役割を持った agent・仕事の振り分け・レビュー) も集客も、一人の事業を回すための道具であって、それぞれ別の趣味ではありません。各項目には、日々の運用で残った理由を 1-2 行で書いています。各節の最後の **運用メモ** は、リンク先の要約ではなく、この形で実際に回して得た教訓です。

*(Kazuaand)* が付いた項目は、このリストの管理者が自分で公開している文書と tool です。

## 目次

- [原則](#原則)
- [AI 組織](#ai-組織)
  - [役割分担と委譲](#役割分担と委譲)
  - [検証とレビュー](#検証とレビュー)
  - [人に聞くとき](#人に聞くとき)
- [ハーネスと運用](#ハーネスと運用)
  - [指示とコンテキスト](#指示とコンテキスト)
  - [記憶と判断の記録](#記憶と判断の記録)
  - [タスク管理と作業の再開](#タスク管理と作業の再開)
  - [セッションとコンテキスト窓](#セッションとコンテキスト窓)
- [集客と販売 (GTM)](#集客と販売-gtm)
  - [ポジショニングとオファー](#ポジショニングとオファー)
  - [コンテンツ・検索・AI 検索](#コンテンツ検索ai-検索)
  - [ローンチ](#ローンチ)
- [安全な公開](#安全な公開)
- [計測とコスト](#計測とコスト)
- [貢献のしかた](#貢献のしかた)
- [ライセンス](#ライセンス)

## 原則

- [Do Things that Don't Scale](https://paulgraham.com/ds.html) - 最初の数回は手でやる。一人で回す人にとっては、その手作業こそが「どの工程を agent に渡す価値があるか」を知る方法になります。
- [MAKE](https://readmake.com/) - チームなしでアイデアから売上まで持っていくための、個人開発者向けの手引き。一人で何を出せるかを、今もいちばん素直に書いた本です。
- [Building effective agents](https://www.anthropic.com/research/building-effective-agents) - まず動く中でいちばん単純な形から始める。「agent の問題」の多くは、実は workflow の問題です。
- [A practical guide to building agents](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf) - agent にする価値があるのはどんな時か、安全柵の足し方、agent 間の受け渡し。作る前の確認表として使えます。

> **運用メモ**
>
> - 自分が抱える約束は少なく保つ。追加の費用も頭の負担もほぼゼロで回せる施策は、agent に全部やらせる。
> - 自分の注意は方向に使う: どの課題を、誰のために、出来上がりの筋が良いか。契約どおりかの確認は機械に任せる。

## AI 組織

### 役割分担と委譲

- [Graph Compound Engineering](https://github.com/Kazuaand/graph-compound-engineering) *(Kazuaand)* - 複数日の仕事を agent に任せるための手引き。仕様・仕事の地図・組織表を書き、判断の重さで役割を席に割り当て、振り返りのたびに次の仕事を楽にしていきます。
- [How we built our multi-agent research system](https://www.anthropic.com/research/multi-agent-research-system) - 並列に振ると token がどれだけかかるか、指示書の出来がどれだけ結果を左右するかを率直に書いています。
- [Compound engineering](https://every.to/chain-of-thought/compound-engineering-how-every-codes-with-agents) - 1 つの仕事が次の仕事を楽にするように積み上げる、という考え方の出どころ。
- [Compound Engineering plugin](https://github.com/EveryInc/compound-engineering-plugin) - 計画・作業・レビュー・積み上げの循環を、入れて読める形で実装したもの。
- [Awesome Graph Engineering](https://github.com/DEEP-JLU/Awesome-Graph-Engineering) - graph・loop・harness・context・prompt の各 engineering を並べて整理した survey と論文リスト。自分の仕組みがどこに位置するかを見るのに役立ちます。
- [Claude Code subagents](https://code.claude.com/docs/en/sub-agents) - 隔離されたコンテキスト窓と agent ごとの tool が、実際にどう動くか。

> **運用メモ**
>
> - 振るかどうかは 1 つの問いで決まる: 途中の生の出力 (file の中身・取得結果・試行錯誤) を自分の窓に残したいか。残したくないなら振る。
> - 振る前に、まず材料を窓の外に出せないか試す。file に置き、手元には path といくつかの事実だけを持つ。
> - 指示は要約し直さず file の path で渡す。どの指示にも予算と止める地点を書く。
> - 返却の最後に「どの論点が閉じて、どれがまだ開いているか」を 1 行で書かせる。
> - 作った本人に採点させない。レビューは新しいコンテキストで行う。

### 検証とレビュー

- [Your AI Product Needs Evals](https://hamel.dev/blog/posts/evals/) - 指標を設計する前に、実際の失敗を見る。小さなチームにとって最も役に立つ eval の助言です。
- [promptfoo](https://github.com/promptfoo/promptfoo) - prompt と agent のテストを繰り返し実行でき、CI に組み込めます。
- [Claude Code hooks](https://code.claude.com/docs/en/hooks) - tool を呼ぶたびに必ず走る決定論の検査。指示文だけでは守りきれない境界に使います。

> **運用メモ**
>
> - 主張はすべて仮説として扱う: 引き継ぎメモ、記憶 file、sub-agent の報告、そして自分の思い込みも。上に積む前に、いちばん安い反証を 1 つ回す。
> - 「無い」と言うには、独立した確認が少なくとも 3 つ要る。検索が 1 回空振りしただけでは、ほとんど何も言えない。
> - テストされる側は自分の潔白を証明できない。自分の環境でテストが緑・成功のトーストが出た、は時間や環境に依存する不具合の反証にならない。
> - deploy や設定変更の後は、出力を目で読むのでなく、期待した状態を exit code で assert する。
> - 危ない操作には段階を付ける: 自動で実行 / 安全柵つきで実行 / 人が要る / 実行しない。表に行が無い操作は実行しない。

### 人に聞くとき

- [Measuring AI agent autonomy in practice](https://www.anthropic.com/research/measuring-agent-autonomy) - 数百万件の人と agent のやり取りから、agent が人の手を挟まずに働く時間がどれだけ延びているかを示したデータ。

> **運用メモ**
>
> - sub-agent はあなたでなく親に聞く。過去の回答・規則・調べ物で決められることは、親が決める。
> - 人まで上げるのは、お金・外への送信・本番の変更・方向だけ。まとめて 1 回で聞く。
> - 質問には推奨・重大かどうか・期限を付ける。重大でない質問は、期限を過ぎたら推奨どおりに進める。
> - 沈黙・タイムアウト・届かなかった通知は、承認ではない。

## ハーネスと運用

### 指示とコンテキスト

- [AGENTS.md](https://agents.md/) - 多くの coding agent が読む、開かれた指示 file の形式。共通の正本を 1 つにし、tool ごとにはそれを指すだけの薄い入口を置く。
- [Effective context engineering for AI agents](https://www.anthropic.com/research/effective-context-engineering-for-ai-agents) - コンテキストは有限の予算。次の一手に要るものだけを読み込む。
- [Agent Skills](https://agentskills.io/home) - 手順を部品にして、要る時だけ読み込ませる仕組み。
- [anthropics/skills](https://github.com/anthropics/skills) - skill の作りを真似するための見本集。
- [Claude Code memory](https://code.claude.com/docs/en/memory) - 指示 file がどこから、どの順で読み込まれるか。
- [Model Context Protocol](https://modelcontextprotocol.io/) - agent に tool やデータをつなぐ標準の方法。
- [Hexagonal architecture](https://alistair.cockburn.us/hexagonal-architecture) - Ports and adapters。AI の仕事に当てはめると、工程を安定した単位にし、tool や model は差し替えのきく部品にする。

> **運用メモ**
>
> - 常設の指示を 1 つ足す時は、外す候補を 1 つ挙げる。規則は model が必要とするより速く増える。

### 記憶と判断の記録

- [Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) - 短い判断記録の原典。「なぜ」を残すことが、決着済みの論点を agent に蒸し返させない一番の手です。
- [Architecture decision record templates](https://github.com/architecture-decision-record/architecture-decision-record) - 書き始めるための雛形と実例。

> **運用メモ**
>
> - 新しい判断が古い判断を置き換えたら、古い方は消さずに「置き換え済み」と印を付ける。

### タスク管理と作業の再開

- [beads](https://github.com/gastownhall/beads) - agent のために作られた、git に載る issue tracker。依存関係の graph があるので、「次に何ができるか」が 1 回の問い合わせで分かります。
- [Effective harnesses for long-running agents](https://www.anthropic.com/research/effective-harnesses-for-long-running-agents) - 進捗 file と git の履歴を、セッションをまたぐ記憶として使う。

> **運用メモ**
>
> - タスクの状態の正は 1 つ (tracker) にする。経緯は進捗 file に書き、どちらも信じる前に git log と照らし合わせる。
> - 終わった単位から順に disk に書き出す。中断した run は足りない単位だけを再開し、終わった単位をやり直さない。
> - 後でやる仕事は、code やチャットに TODO で残さず、新しい issue にする。

### セッションとコンテキスト窓

- [Claude Code best practices](https://code.claude.com/docs/en/best-practices) - 長い coding session での計画・コンテキスト・検証の実践的な習慣。
- [Maximizing the value of your Claude Code sessions](https://claude.com/resources/articles/maximizing-the-value-of-your-claude-code-sessions) - 1 token あたりの価値を上げる実践的なこつ。prompt cache がセッションの費用をどう左右するかも含みます。

> **運用メモ**
>
> - cache が冷えたセッションには何も送らない。「続けて」や生存確認の 1 通で、コンテキスト全体 (しばしば数十万 token) が書き直されることがある。
> - 温かいかどうかは、最後に応答が成功してからの時間と、process が生きているかだけで判断する。判断できなければ冷えているとみなす。
> - 冷えたセッションへの用件は、そのセッションが読む file に残すか、引き継ぎメモを持たせて小さな新しいセッションを立てる。
> - 重い読み込み・走査・取得は隔離した sub-agent に任せ、短い要約か path だけを受け取る。
> - テストやビルドの出力をメインの窓に流さない。返すのは失敗だけにする。

## 集客と販売 (GTM)

### ポジショニングとオファー

- [April Dunford's books](https://www.aprildunford.com/books) - ポジショニングを決め、それを営業の話し方に落とし込むための、繰り返し使える手順。

> **運用メモ**
>
> - AI で量産した成果は、作った量でなく、取れた需要で測る。
> - 人が読むものを作る前に、その読み手が誰かを根拠付きで書き出す。作る人とレビューする人に、同じ短い説明を渡す。

### コンテンツ・検索・AI 検索

- [Creating helpful, reliable, people-first content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) - Google 自身による自己点検の問い。AI と一緒に書いた原稿は、一度これに通す。
- [AI features and your website](https://developers.google.com/search/docs/appearance/ai-features) - Google の AI 検索機能が、あなたのページをどう使い、どうリンクするか。
- [llms.txt](https://llmstxt.org/) - 言語 model がサイトを読みやすくするための、平文の索引の提案。
- [Schema.org](https://schema.org/) - 構造化データの語彙。AI の回答に引用されるようになると、実体の情報がそろっていることがより効いてきます。
- [The Open Graph protocol](https://ogp.me/) - リンクを共有された時の見え方を決める。
- [Google Search Console](https://search.google.com/search-console/about) - 何で検索に出ているか、何が壊れているかが無料で分かる。
- [PageSpeed Insights](https://pagespeed.web.dev/) - 実利用のデータも含めて、表示速度をすぐ確かめられる。

> **運用メモ**
>
> - 名前・説明・リンクは、載せているすべての場所でそろえる。実体の情報のずれは、従来の検索より AI の回答でより大きく響く。
> - SNS によっては、存在しない投稿 ID にも HTTP 200 を返す。投稿が本当にあるかは、crawler から見える本文 (たとえば `og:description` タグ) と自分が投稿した文を突き合わせて確かめる。

### ローンチ

- [Show HN guidelines](https://news.ycombinator.com/showhn.html) - 何が Show HN に当たるか、試せるものをどう見せるか。

> **運用メモ**
>
> - 製品の事実 (一言の説明・対象・価格・リンク) は 1 つの file にまとめ、各掲載先の文はそこから作る。毎回手で書き直さない。
> - 掲載はすべて 1 つの表で管理する: どこに・いつ・状態・リンク。後で実際の掲載を見直す。掲載先は変わるし、消えることもある。

## 安全な公開

- [publish-gate](https://github.com/Kazuaand/publish-gate) *(Kazuaand)* - 公開前の 4 段の関門: 独立した検出器、repo の外に置く非公開の禁止語リスト、両方が PASS する必要がある新しい AI レビュー 2 体、そして先に通っていなければならない「わざと秘密を仕込んだ selftest」。
- [gitleaks](https://github.com/gitleaks/gitleaks) - git repo や directory を対象にした、速い秘密検出器。
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) - 秘密を見つけ、見つけた認証情報がまだ生きているかも確かめられる。
- [Presidio](https://github.com/data-privacy-stack/presidio) - 文章の中の名前・住所・電話番号などの個人情報を検出する。
- [leakgate](https://pypi.org/project/leakgate/) - 一般的な検出器が見逃すもの (local のユーザー名・内部 host・自分たちの未公開の固有語) を、code と agent の会話記録から探す公開前の関門。
- [About secret scanning](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning) - GitHub が代わりに見つけてくれるもの、見つけないもの。
- [Setting your commit email address](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address) - noreply のアドレスを使い、commit から個人のメールが見えないようにする。
- [About passkeys](https://docs.github.com/en/authentication/authenticating-with-a-passkey/about-passkeys) - 公開に使うアカウントに、フィッシングに強いサインインを。

> **運用メモ**
>
> - 検出器の 0 件は、同じ run でわざと秘密を仕込んだ selftest が通るまでは何の意味もない。
> - source code 向けの検出器は、文章や HTML に書かれた認証情報を多く見逃す。「ラベル: 値」の形を拾う自前の pattern を足し、HTML タグを除いた版でもう一度検査する。
> - 公開するのは、最終的に検査を通った tree だけを入れた新しい repo にする。作業中の履歴には、消したはずのものが残っていることがある。
> - 非公開の禁止語リストは公開 repo の外に置き、検査の時に外から渡す。

## 計測とコスト

- [Prompt caching (Anthropic)](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) - cache の寿命と、書き込みと読み出しの価格差。長く動く agent の費用はほぼこれで決まる。
- [Prompt caching (OpenAI)](https://developers.openai.com/api/docs/guides/prompt-caching) - 別の provider での同じ仕組み。複数を使うなら知っておく価値がある。
- [Manage costs in Claude Code](https://code.claude.com/docs/en/costs) - 支出を見る・抑えるための組み込みの方法。
- [ccusage](https://github.com/ccusage/ccusage) - 手元の agent の log から使用量と費用をまとめる。
- [LiteLLM](https://github.com/BerriAI/litellm) - 多くの model provider を 1 つの入口にまとめる gateway。model の group で振り分け、個人情報は無料枠に流さない。
- [Langfuse](https://github.com/langfuse/langfuse) - LLM アプリの追跡と評価のための open source。
- [Plausible Analytics](https://github.com/plausible/analytics) - 軽くてプライバシーに配慮した、自前でも動かせるアクセス解析。
- [Umami](https://github.com/umami-software/umami) - もう 1 つの、自前で動かせるシンプルなアクセス解析。
- [Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/) - 4 つの基本シグナルと、なぜすべての警報に対応する人が要るのか。

> **運用メモ**
>
> - 費用は 3 列で報告する: 標準単価での費用、実際に使った credit、追加で出した現金。サブスクリプションでも、使った分はタダではない。
> - 分からない使用量は「不明」のまま残す。0 と書かない。
> - まず定期実行の自動処理を見る。ある監査では、使用量のほぼすべてが人の作業でなく、それらから来ていた。
> - 並列に振ると、cache がすべて温かくても枠を燃やす。各 turn がコンテキスト全体を読み直すから。振る前に残りの枠を確かめる。
> - 定期実行の検査はすべて台帳に載せ、その出力を誰が読むかを書く。誰も読まない検査は、黙って死んでいる。
> - 判定は梯子にする: まず決定論の検査、次に小さな分類器、残ったものだけを大きな model に回す。

## 貢献のしかた

提案を歓迎します。先に [貢献の手引き](contributing.md) を読んでください。

## ライセンス

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

法律上可能な範囲で、貢献者はこの作品に関する著作権と関連する権利をすべて放棄しています。
