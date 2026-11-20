# context-check

**작업을 시작하기 전에 요청의 뜻을 먼저 점검하는 Claude 플러그인**입니다.
A Claude plugin that checks what a request really means **before** Claude starts working on it.

[한국어](#한국어) · [English](#english)

---

## 한국어

### 왜 필요한가
대화가 길어지거나 요약되면 Claude가 요청을 잘못 읽고 **아예 다른 일**을 하는 경우가 생깁니다.

- **단어 뉘앙스**: "정리해 줘"를 요약으로 원했는데 내용을 지우거나, "검토해 줘"를 표시만 원했는데 원본을 고칩니다.
- **문장 구조**: 단어는 다 맞게 읽어도 구조를 잘못 읽습니다. 무엇이 기준인지("A 기준으로 B 맞춰"), 부정이 어디까지 걸리는지("전부 고치지는 마"), 빠진 목적어나 "그거"가 무엇인지를 놓칩니다. 한국어와 영어 모두 해당합니다.
- **용어의 미끄러짐**: 대화에서 따로 정한 용어를 일반적인 뜻으로 바꿔 읽습니다.

### 하는 일
1. **읽기**: 바로잡은 기록, 요청 원문, 개인 사전, 프로젝트 용어집, 메모리를 먼저 봅니다.
2. **보여 주기**: 해석 후보, 채택한 해석, **하지 않을 일**을 먼저 보여 줍니다.
3. **판단**: 해석이 분명하면 두 줄만 보여 주고 진행합니다. 갈리거나 삭제처럼 되돌리기 어려우면 선택지로 묻습니다.
4. **기록**: 사용자가 바로잡은 해석을 개인 사전에 쌓아 같은 오해를 반복하지 않습니다.

선택 설치인 **context-check-hook** 플러그인을 함께 깔면 메시지마다 짧은 점검 규칙이 붙습니다. 그러면 작업 요청마다 답 첫머리에 아래 두 줄이 나옵니다.
```
🧭 해석: ...
🧭 하지 않을 일: ...
```

### 설치 (Claude Code)
```
claude plugin marketplace add win212191-wq/context-check
claude plugin install context-check@context-check-marketplace
```
매번 자동으로 점검하게 하려면 훅 플러그인도 설치합니다 (선택).
```
claude plugin install context-check-hook@context-check-marketplace
```
설치한 뒤 새 세션을 엽니다. 세션 안에서는 `/plugin` 메뉴로도 설치할 수 있습니다.

| 플러그인 | 내용 |
|---|---|
| `context-check` | 스킬. 요청이 애매할 때 자동으로 불리고, 직접 부를 수도 있습니다. |
| `context-check-hook` | 선택. 모든 메시지에 점검 규칙을 붙이는 훅입니다. `context-check`와 함께 씁니다. |

- **직접 부르기**: `/context-check:context-check`
- **개인 사전**: `~/.claude/context-check/nuance-dictionary.md`에 쌓입니다. 플러그인을 업데이트해도 지워지지 않습니다.
- **프로젝트 용어집**: 각 작업 폴더의 `.claude/glossary.md`에 쌓입니다.
- **훅이 동작하려면** (`context-check-hook`): 셸에 `cat` 명령이 있어야 합니다. Windows에서는 Git Bash를 설치하면 됩니다. 훅이 없어도 스킬은 동작합니다.

### claude.ai에서
스킬은 claude.ai 채팅에서도 동작합니다. 훅은 Claude Code에서만 동작합니다. 채팅에서는 파일을 쓸 수 없어서, 바로잡은 해석을 메모리에 저장하거나 "📌 용어집에 추가할 줄" 표로 보여 줍니다.

### 개인정보
플러그인은 어디에도 데이터를 보내지 않습니다. 자세한 내용은 [PRIVACY.md](PRIVACY.md)에 있습니다.

---

## English

### Why
In long or summarized conversations, Claude can misread a request and end up doing **a different task**.

- **Word nuance**: "tidy this up" meant *summarize*, but Claude deleted content. "Review it" meant *mark issues*, but Claude edited the original.
- **Sentence structure**: every word is read correctly, but the structure is not. Claude misses which side is the reference ("match B to A"), how far a negation reaches ("don't fix all of them"), what an omitted object or "it" points to, or where a modifier or *only* attaches. Both Korean and English are covered.
- **Term drift**: terms defined earlier in the conversation get read with their everyday meaning.

### What it does
1. **Read first**: past corrections, the exact wording of the request, the personal dictionary, the project glossary, and memory.
2. **Show**: candidate readings, the chosen reading, and **what it will NOT do**.
3. **Decide**: if the reading is clear, it shows two lines and proceeds. If readings diverge, or the action is hard to undo (delete, overwrite, bulk edit, send), it asks with concrete options.
4. **Learn**: corrections are saved to a personal dictionary so the same misreading does not repeat.

With the optional **context-check-hook** plugin, a `UserPromptSubmit` hook adds a short rule to every message, so work requests start with two lines: the reading (`🧭 해석`) and what will not be done (`🧭 하지 않을 일`).

### Install (Claude Code)
```
claude plugin marketplace add win212191-wq/context-check
claude plugin install context-check@context-check-marketplace
```
To run the check on every message, also install the hook plugin (optional):
```
claude plugin install context-check-hook@context-check-marketplace
```
Start a new session afterwards. You can also install from the `/plugin` menu inside a session.

| Plugin | What it is |
|---|---|
| `context-check` | The skill. Triggers on ambiguous requests, or invoke it directly. |
| `context-check-hook` | Optional. A hook that adds the check rule to every message. Use with `context-check`. |

- **Invoke directly**: `/context-check:context-check`
- **Personal dictionary**: `~/.claude/context-check/nuance-dictionary.md` (kept across plugin updates)
- **Project glossary**: `.claude/glossary.md` in each working folder
- **Hook requirement** (`context-check-hook`): the shell needs `cat`. On Windows, install Git Bash. The skill works without the hook.

The skill instructions are written in Korean. Claude reads them fine and applies them to English requests too.

### Privacy
The plugin sends no data anywhere. See [PRIVACY.md](PRIVACY.md).

## License
MIT
