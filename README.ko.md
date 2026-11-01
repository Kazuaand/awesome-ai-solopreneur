[English](README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md)

# Awesome AI Solopreneur [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> AI 에이전트 팀과 함께 혼자 사업을 운영하는 사람을 위해, 실무에서 써 보고 엄선한 자료 목록입니다.

English | [日本語](README.ja.md)

핵심은 사업입니다. AI 조직(역할, 작업 배분, 검토 체계를 갖춘 에이전트들)과 시장 진출 활동은 1인 사업을 운영하는 수단이지, 별개의 취미가 아닙니다. 각 항목에는 일상 업무에서 왜 쓸 만했는지 한두 줄로 설명했습니다. 각 절 끝의 **실무에서 얻은 교훈**은 링크 내용을 요약한 것이 아니라, 이 체계를 직접 운영하며 배운 점입니다.

*(Kazuaand)* 표시가 있는 항목은 관리자가 직접 만든 오픈 소스 문서와 도구입니다.

<a id="contents"></a>
## 목차

- [원칙](#principles)
- [AI 조직](#ai-organization)
  - [역할과 위임](#roles-and-delegation)
  - [검증과 검토](#verification-and-review)
  - [언제 사람에게 물어볼 것인가](#when-to-ask-the-human)
- [하네스와 운영](#harness-and-operations)
  - [지침과 컨텍스트](#instructions-and-context)
  - [메모리와 의사결정](#memory-and-decisions)
  - [작업 관리와 재개](#tasks-and-resuming-work)
  - [세션과 컨텍스트 창](#sessions-and-the-context-window)
- [시장 진출](#go-to-market)
  - [포지셔닝과 제안](#positioning-and-offers)
  - [콘텐츠, 검색, AI 검색](#content-search-and-ai-search)
  - [출시](#launching)
- [안전한 공개](#safe-publishing)
- [측정과 비용](#measurement-and-cost)
- [기여하기](#contributing)
- [라이선스](#license)

<a id="principles"></a>
## 원칙

- [확장되지 않는 일을 하라](https://paulgraham.com/ds.html) - 처음 몇 번은 직접 해 보세요. 혼자 운영하는 사람에게 이 수작업은 어떤 단계를 에이전트에게 맡길 가치가 있는지 알아가는 과정입니다.
- [MAKE](https://readmake.com/) - 팀 없이 아이디어에서 매출까지 나아가는 인디 창업 안내서입니다. 한 사람이 무엇을 만들어 내놓을 수 있는지 가장 명료하게 설명하는 책입니다.
- [효과적인 에이전트 만들기](https://www.anthropic.com/research/building-effective-agents) - 제대로 작동하는 가장 단순한 패턴부터 시작하세요. 많은 "에이전트" 문제는 알고 보면 워크플로 문제입니다.
- [에이전트 구축 실무 가이드](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf) - 언제 에이전트를 쓸 가치가 있는지, 안전장치를 어떻게 추가하는지, 에이전트 간에 어떻게 일을 넘기는지 다룹니다. 구축 전에 점검하기 좋습니다.

> **실무에서 얻은 교훈**
>
> - 직접 책임지고 챙길 일은 적게 유지하세요. 추가 비용과 정신적 부담이 거의 없는 실행 방법은 에이전트가 모두 시도하게 하세요.
> - 주의력은 방향에 쓰세요. 누구의 어떤 문제를 풀 것인지, 결과물에 담긴 감각이 적절한지에 집중하고, 정해진 요건의 충족 여부는 기계에 맡기세요.

<a id="ai-organization"></a>
## AI 조직

<a id="roles-and-delegation"></a>
### 역할과 위임

- [Graph Compound Engineering](https://github.com/Kazuaand/graph-compound-engineering) *(Kazuaand)* - 여러 날에 걸친 일을 에이전트에게 맡기기 위한 핸드북입니다. 명세, 작업 그래프, 조직도를 작성하고, 판단의 무게에 맞춰 각 역할에 모델을 배치하며, 회고를 통해 다음 일을 더 쉽게 만듭니다.
- [Agent Delegation Playbook](https://github.com/Kazuaand/agent-delegation-playbook) *(Kazuaand)* - 언제 하위 에이전트에게 맡기고 언제 직접 할지, 지시서를 어떻게 쓰고 무엇을 돌려받을지, 어떤 등급의 모델과 effort를 쓸지 정리한 플레이북입니다.
- [멀티 에이전트 리서치 시스템을 구축한 방법](https://www.anthropic.com/research/multi-agent-research-system) - 작업을 여러 에이전트로 나눌 때 드는 토큰 비용과 작업 지시서가 결과를 얼마나 좌우하는지 솔직하게 설명합니다.
- [Compound engineering](https://every.to/chain-of-thought/compound-engineering-how-every-codes-with-agents) - 하나의 작업이 다음 작업을 더 쉽게 만들어야 한다는 생각입니다. "compound" 루프의 출발점입니다.
- [Compound Engineering plugin](https://github.com/EveryInc/compound-engineering-plugin) - 계획, 실행, 검토, 개선 축적의 순환을 구현한 플러그인으로, 설치해 쓰거나 내부를 살펴볼 수 있습니다.
- [Awesome Graph Engineering](https://github.com/DEEP-JLU/Awesome-Graph-Engineering) - 그래프, 루프, 하네스, 컨텍스트, 프롬프트 엔지니어링을 나란히 살펴보는 서베이와 논문 목록입니다. 자신의 체계가 어디에 해당하는지 파악하기 좋습니다.
- [Claude Code 서브에이전트](https://code.claude.com/docs/en/sub-agents) - 격리된 컨텍스트 창과 에이전트별 도구가 실제로 어떻게 작동하는지 설명합니다.

> **실무에서 얻은 교훈**
>
> - 위임 여부는 질문 하나로 결정하세요. 가공하지 않은 중간 출력(파일 전체 내용, 가져온 자료, 시행착오)을 내 컨텍스트에 넣고 싶은가? 아니라면 위임하세요.
> - 위임하기 전에 자료를 컨텍스트 창 밖으로 옮겨 보세요. 파일에 저장하고 경로와 핵심 사실 몇 가지만 남깁니다.
> - 내용을 다시 요약해서 전달하기보다 파일 경로로 작업을 지시하세요. 모든 작업 지시서에 예산과 중단 기준을 넣으세요.
> - 모든 결과 보고의 마지막에 해결된 질문과 아직 열린 질문을 한 줄로 정리하게 하세요.
> - 만든 에이전트가 자기 결과물을 채점하게 하지 마세요. 새 컨텍스트에서 검토하세요.

<a id="verification-and-review"></a>
### 검증과 검토

- [AI 제품에는 평가가 필요하다](https://hamel.dev/blog/posts/evals/) - 지표를 설계하기 전에 실제 실패 사례부터 살펴보세요. 소규모 팀에 가장 유용한 평가 조언입니다.
- [promptfoo](https://github.com/promptfoo/promptfoo) - CI에서 실행할 수 있는, 반복 가능한 프롬프트 및 에이전트 테스트 도구입니다.
- [Claude Code 훅](https://code.claude.com/docs/en/hooks) - 도구 호출마다 실행되는 결정론적 검사입니다. 지침만으로 지키기 어려운 경계를 강제하는 데 쓰세요.

> **실무에서 얻은 교훈**
>
> - 인수인계 메모, 메모리 파일, 서브에이전트 보고, 자신이 기억하고 있는 가정까지 모든 주장을 가설로 취급하세요. 그 위에 작업을 쌓기 전에 가장 저렴한 방법으로 반증을 시도하세요.
> - "없다"고 결론 내리려면 서로 독립적인 확인이 적어도 세 번 필요합니다. 검색 결과가 한 번 비었다고 많은 것이 입증되지는 않습니다.
> - 검증 대상 시스템은 스스로 결백을 입증할 수 없습니다. 자체 테스트 통과나 성공 알림만으로 타이밍 또는 환경 버그가 없다고 볼 수는 없습니다.
> - 배포나 설정 변경 뒤에는 출력을 눈으로 읽는 대신, 기대한 상태인지 종료 코드로 확인하세요.
> - 위험한 작업마다 자동 실행, 안전장치를 거쳐 실행, 사람의 판단 필요, 실행 금지 중 하나를 지정하세요. 표에 없는 작업은 실행하지 않습니다.

<a id="when-to-ask-the-human"></a>
### 언제 사람에게 물어볼 것인가

- [실제 환경에서 AI 에이전트의 자율성 측정하기](https://www.anthropic.com/research/measuring-agent-autonomy) - 수백만 건의 사람과 에이전트 간 상호작용을 바탕으로, 사람의 개입 사이에 에이전트가 얼마나 오래 작업하는지 보여줍니다.

> **실무에서 얻은 교훈**
>
> - 서브에이전트는 사람이 아니라 상위 에이전트에게 질문합니다. 상위 에이전트는 이전 답변, 규칙, 조사로 해결할 수 있는 사항을 직접 처리합니다.
> - 돈, 외부로 보내는 메시지, 운영 환경 변경, 방향에 관한 질문만 사람에게 올리고, 한 차례에 모아서 묻습니다.
> - 각 질문에는 권고안, 중대한 판단인지 여부, 중대하지 않다면 언제부터 권고안대로 진행할지를 명시합니다.
> - 침묵, 시간 초과, 전달 실패는 결코 승인이 아닙니다.

<a id="harness-and-operations"></a>
## 하네스와 운영

<a id="instructions-and-context"></a>
### 지침과 컨텍스트

- [AGENTS.md](https://agents.md/) - 여러 코딩 에이전트가 읽는 공개 지침 형식입니다. 공통 원본 하나를 유지하고, 각 도구에는 그 원본을 가리키는 얇은 어댑터를 두세요.
- [AI 에이전트를 위한 효과적인 컨텍스트 엔지니어링](https://www.anthropic.com/research/effective-context-engineering-for-ai-agents) - 컨텍스트는 한정된 자원입니다. 다음 단계에 필요한 것만 불러오세요.
- [Agent Skills](https://agentskills.io/home) - 절차를 패키지로 만들어 필요할 때만 불러오게 합니다.
- [anthropics/skills](https://github.com/anthropics/skills) - 구조를 참고할 수 있는 스킬 예제입니다.
- [Claude Code 메모리](https://code.claude.com/docs/en/memory) - 지침 파일을 어떻게 찾고 불러오는지, 어떤 순서로 적용하는지 설명합니다.
- [Model Context Protocol](https://modelcontextprotocol.io/) - 에이전트에 도구와 데이터를 연결하는 표준 방식입니다.
- [육각형 아키텍처](https://alistair.cockburn.us/hexagonal-architecture) - 포트와 어댑터를 다룹니다. AI 작업에 적용하면, 작업 단계는 안정적으로 유지하고 모든 도구와 모델은 교체 가능한 어댑터로 만드는 것입니다.

> **실무에서 얻은 교훈**
>
> - 상시 지침을 하나 추가할 때는 없앨 지침도 하나 정하세요. 규칙은 모델이 실제로 필요로 하는 것보다 더 많이 쌓이기 쉽습니다.

<a id="memory-and-decisions"></a>
### 메모리와 의사결정

- [아키텍처 결정 기록하기](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions) - 간결한 의사결정 기록 형식의 원전입니다. "왜"를 기록해야 에이전트가 이미 정한 문제를 다시 꺼내지 않습니다.
- [Architecture decision record 템플릿](https://github.com/architecture-decision-record/architecture-decision-record) - 시작할 때 참고할 템플릿과 예제입니다.

> **실무에서 얻은 교훈**
>
> - 새 결정이 이전 결정을 대체하면, 이전 것을 삭제하지 말고 대체되었다고 표시하세요.

<a id="tasks-and-resuming-work"></a>
### 작업 관리와 재개

- [beads](https://github.com/gastownhall/beads) - 에이전트를 위해 만든 git 기반 이슈 트래커입니다. 의존성 그래프 덕분에 "다음에 무엇을 할 수 있나?"를 쿼리 하나로 확인할 수 있습니다.
- [장시간 실행되는 에이전트를 위한 효과적인 하네스](https://www.anthropic.com/research/effective-harnesses-for-long-running-agents) - 진행 상황 파일과 git 이력을 세션 사이의 메모리로 활용합니다.

> **실무에서 얻은 교훈**
>
> - 작업 상태의 기준은 트래커 하나로 통일하세요. 경과는 진행 상황 파일에 남기고, 둘 다 git 로그와 대조한 뒤 신뢰하세요.
> - 작업 단위가 끝날 때마다 디스크에 저장하세요. 중단 후 재개할 때는 빠진 단위만 처리하고, 끝낸 일을 다시 하지 않아야 합니다.
> - 후속 작업은 코드나 채팅에 TODO로 남기지 말고 새 이슈로 등록하세요.

<a id="sessions-and-the-context-window"></a>
### 세션과 컨텍스트 창

- [Claude Code 모범 사례](https://code.claude.com/docs/en/best-practices) - 긴 코딩 세션에서 계획, 컨텍스트, 검증을 관리하는 실용적인 습관을 소개합니다.
- [Claude Code 세션의 가치 극대화하기](https://claude.com/resources/articles/maximizing-the-value-of-your-claude-code-sessions) - 프롬프트 캐시가 세션 비용에 미치는 영향을 포함해, 토큰을 더 알차게 쓰는 실용적인 팁을 제공합니다.

> **실무에서 얻은 교훈**
>
> - 캐시가 만료된 세션에는 아무것도 보내지 마세요. "계속해" 한마디나 생존 확인 메시지 하나로 전체 컨텍스트가 다시 기록될 수 있으며, 그 양은 종종 수십만 토큰에 달합니다.
> - 캐시가 아직 유효한지는 마지막 정상 응답 이후의 시간과 프로세스 생존 여부만으로 판단하세요. 알 수 없으면 만료된 것으로 취급하세요.
> - 캐시가 만료된 세션에는 나중에 읽을 파일로 요청을 남기거나, 인수인계 메모를 넣은 작은 새 세션을 시작하세요.
> - 대량 읽기, 스캔, 자료 수집은 격리된 서브에이전트에 맡기고, 짧은 요약이나 경로만 돌려받으세요.
> - 테스트와 빌드 출력은 메인 컨텍스트 창에 넣지 마세요. 실패 내용만 돌려받으세요.

<a id="go-to-market"></a>
## 시장 진출

<a id="positioning-and-offers"></a>
### 포지셔닝과 제안

- [April Dunford의 저서](https://www.aprildunford.com/books) - 포지셔닝을 정리한 뒤 영업 제안으로 만드는, 반복해서 활용할 수 있는 방법입니다.

> **실무에서 얻은 교훈**
>
> - AI로 늘린 산출물의 성과는 생산량이 아니라 실제로 확보한 수요로 측정하세요.
> - 사람이 읽을 글을 쓰기 전에, 근거를 바탕으로 독자가 누구인지 적으세요. 작성자와 검토자에게 동일한 짧은 지시서를 전달하세요.

<a id="content-search-and-ai-search"></a>
### 콘텐츠, 검색, AI 검색

- [유용하고 신뢰할 수 있는 사용자 중심 콘텐츠 만들기](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) - Google이 제시하는 자체 점검 질문입니다. AI의 도움으로 쓴 초안도 이 질문으로 점검하세요.
- [AI 기능과 웹사이트](https://developers.google.com/search/docs/appearance/ai-features) - Google의 AI 검색 기능이 웹페이지를 어떻게 활용하고 링크하는지 설명합니다.
- [llms.txt](https://llmstxt.org/) - 언어 모델이 사이트를 읽기 쉽게 하자는 취지로 제안된 일반 텍스트 색인입니다.
- [Schema.org](https://schema.org/) - 구조화된 데이터를 표현하는 어휘 체계입니다. AI 답변이 사이트를 인용하기 시작하면 엔티티 정보의 일관성이 더 중요해집니다.
- [The Open Graph protocol](https://ogp.me/) - 링크를 공유할 때 어떻게 표시되는지 제어합니다.
- [Google Search Console](https://search.google.com/search-console/about) - 어떤 검색어에서 몇 위에 노출되는지, 어디에 문제가 있는지 무료로 확인할 수 있습니다.
- [PageSpeed Insights](https://pagespeed.web.dev/) - 실제 사용자 데이터를 활용해 성능을 빠르게 점검합니다.

> **실무에서 얻은 교훈**
>
> - 등록한 모든 곳에서 이름, 설명, 링크를 동일하게 유지하세요. 엔티티 정보가 일치하지 않으면 기존 검색보다 AI 답변에서 더 큰 손해를 봅니다.
> - 일부 소셜 플랫폼은 실제 게시물이든 아니든 어떤 게시물 ID에도 HTTP 200을 반환합니다. 게시물이 존재하는지 확인하려면 크롤러가 보는 텍스트(예: `og:description` 태그)를 실제 게시 내용과 비교하세요.

<a id="launching"></a>
### 출시

- [Show HN 가이드라인](https://news.ycombinator.com/showhn.html) - 어떤 항목을 올릴 수 있는지, 사람들이 직접 써 볼 수 있는 것을 어떻게 소개할지 설명합니다.

> **실무에서 얻은 교훈**
>
> - 제품의 사실 정보를 파일 하나로 관리하세요(한 줄 소개, 대상 고객, 가격, 링크). 디렉터리에 등록할 때마다 직접 다시 쓰지 말고 이 파일에서 내용을 생성하세요.
> - 모든 등록 내역을 한 표에서 관리하세요. 등록처, 날짜, 상태, 링크를 기록합니다. 나중에 실제 게시 상태도 다시 확인하세요. 디렉터리는 바뀌고, 때로는 등록 항목을 삭제하기도 합니다.

<a id="safe-publishing"></a>
## 안전한 공개

- [publish-gate](https://github.com/Kazuaand/publish-gate) *(Kazuaand)* - 공개 전에 거치는 네 단계 검증 체계입니다. 서로 독립적인 탐지기, 저장소 밖에 보관하는 비공개 차단 목록, 둘 다 통과 판정을 내려야 하는 새로운 AI 검토자 두 명, 그리고 비밀정보를 미리 심어 두고 가장 먼저 통과해야 하는 자체 테스트를 사용합니다.
- [gitleaks](https://github.com/gitleaks/gitleaks) - git 저장소와 디렉터리에서 비밀정보를 빠르게 찾는 스캐너입니다.
- [TruffleHog](https://github.com/trufflesecurity/trufflehog) - 비밀정보를 찾아내고, 발견한 인증 정보가 아직 유효한지도 확인할 수 있습니다.
- [Presidio](https://github.com/data-privacy-stack/presidio) - 텍스트에서 이름, 주소, 전화번호 같은 개인정보를 탐지합니다.
- [leakgate](https://pypi.org/project/leakgate/) - 범용 스캐너가 놓치는 로컬 사용자명, 내부 호스트, 비공개 프로젝트 고유 용어를 코드와 에이전트 대화 기록에서 검사하는 공개 전 검증 도구입니다.
- [비밀정보 스캔 소개](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning) - GitHub이 대신 잡아 주는 것과 잡아 주지 못하는 것을 설명합니다.
- [커밋 이메일 주소 설정하기](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address) - 커밋에 개인 이메일이 드러나지 않도록 noreply 주소를 사용하세요.
- [패스키 소개](https://docs.github.com/en/authentication/authenticating-with-a-passkey/about-passkeys) - 공개용 계정에 피싱에 강한 로그인 방식을 적용합니다.

> **실무에서 얻은 교훈**
>
> - 같은 실행에서 비밀정보를 심어 둔 자체 테스트가 통과하기 전까지는, 스캐너의 탐지 결과 0건에 의미가 없습니다.
> - 소스 코드용 스캐너는 일반 문장이나 HTML에 적힌 인증 정보를 많이 놓칩니다. "레이블: 값" 형태의 텍스트에 맞는 패턴을 추가하고, HTML 태그를 제거한 버전도 다시 검사하세요.
> - 검증을 마친 최종 파일 트리만 담아 새 저장소로 공개하세요. 작업 이력에는 제거한 정보가 여전히 남아 있을 수 있습니다.
> - 비공개 단어의 차단 목록은 공개 저장소 밖에 보관하고, 검사할 때 전달하세요.

<a id="measurement-and-cost"></a>
## 측정과 비용

- [프롬프트 캐싱(Anthropic)](https://platform.claude.com/docs/en/build-with-claude/prompt-caching) - 캐시 수명과 쓰기·읽기 비용의 차이를 설명합니다. 장시간 실행되는 에이전트의 운영을 좌우하는 요소입니다.
- [프롬프트 캐싱(OpenAI)](https://developers.openai.com/api/docs/guides/prompt-caching) - 다른 제공업체에서 같은 원리가 어떻게 적용되는지 다룹니다. 여러 제공업체를 쓴다면 알아둘 만합니다.
- [Claude Code 비용 관리](https://code.claude.com/docs/en/costs) - 지출을 확인하고 제한하는 내장 기능을 소개합니다.
- [ccusage](https://github.com/ccusage/ccusage) - 로컬 에이전트 로그를 바탕으로 사용량과 비용을 보고합니다.
- [LiteLLM](https://github.com/BerriAI/litellm) - 여러 모델 제공업체를 하나로 연결하는 게이트웨이입니다. 모델 그룹별로 요청을 배분하고, 개인정보는 무료 요금제로 보내지 마세요.
- [Langfuse](https://github.com/langfuse/langfuse) - LLM 애플리케이션을 위한 오픈 소스 추적 및 평가 도구입니다.
- [Plausible Analytics](https://github.com/plausible/analytics) - 직접 호스팅할 수 있는 가볍고 개인정보 보호를 중시하는 웹 분석 도구입니다.
- [Umami](https://github.com/umami-software/umami) - 직접 호스팅할 수 있는 또 다른 간단한 분석 도구입니다.
- [분산 시스템 모니터링](https://sre.google/sre-book/monitoring-distributed-systems/) - 네 가지 골든 시그널과 모든 알림에 대응할 사람이 필요한 이유를 설명합니다.

> **실무에서 얻은 교훈**
>
> - 비용은 세 열로 보고하세요. 정가 기준 비용, 실제 소비한 크레딧, 추가로 지출한 현금입니다. 구독한다고 사용 비용이 없어지는 것은 아닙니다.
> - 알 수 없는 사용량은 "알 수 없음"으로 남기세요. 절대로 0으로 적지 마세요.
> - 예약된 백그라운드 자동화부터 살펴보세요. 한 차례 점검에서는 사람이 직접 진행한 작업이 아니라 이 자동화가 사용량의 거의 전부를 차지했습니다.
> - 모든 캐시가 유효해도 병렬 위임은 사용 한도를 소모합니다. 매 턴마다 전체 컨텍스트를 다시 읽기 때문입니다. 작업을 분산하기 전에 남은 한도를 확인하세요.
> - 예약 실행되는 모든 점검 작업과 그 출력을 읽는 담당자를 목록으로 관리하세요. 아무도 읽지 않는 점검은 조용히 기능을 잃은 것입니다.
> - 판단은 단계적으로 하세요. 결정론적 검사를 먼저 하고, 작은 분류기를 거친 뒤, 남은 것만 대형 모델에 맡기세요.

<a id="contributing"></a>
## 기여하기

제안을 환영합니다. 먼저 [기여 가이드라인](contributing.md)을 읽어 주세요.

<a id="license"></a>
## 라이선스

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

기여자들은 법이 허용하는 범위에서 이 저작물에 대한 모든 저작권 및 관련 권리를 포기했습니다.
