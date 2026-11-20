# Privacy Policy / 개인정보 처리방침

_Last updated: 2026-11-21_

## English

**context-check** is a Claude plugin made of instructions (a skill) and plain text reference files. It contains no executable code, no MCP servers, and no connectors. The optional companion plugin **context-check-hook** only prints a fixed text file into Claude's context.

**What it reads**
- The current conversation, and files or memory that Claude can already access in your session, to understand what a request means.

**What it writes**
- Interpretations you confirm or correct (for example, "'tidy up' means summarize, not delete") are written to files on **your own computer**:
  - `~/.claude/context-check/nuance-dictionary.md` (personal dictionary)
  - `.claude/glossary.md` in the working folder (project glossary)
- On claude.ai, where files cannot be written, it saves one line to Claude's memory (if memory is on) or shows a line for you to copy.
- Only interpretations you confirmed or corrected are recorded, never Claude's guesses, and Claude tells you each time it records one.
- It does not collect names, email addresses, postal addresses, credentials, or payment details.

**What it sends**
- Nothing. The plugin makes no network requests and sends no data to the author or any third party. The author operates no service and receives or retains no data.

**Removing data**
- Delete or edit the files listed above at any time. Uninstalling the plugin does not delete them automatically.

**Contact**
- Open an issue at https://github.com/win212191-wq/context-check/issues

## 한국어

**context-check**는 지침(스킬)과 텍스트 참고 파일로만 이루어진 Claude 플러그인입니다. 실행 코드, MCP 서버, 커넥터가 없습니다. 선택 설치인 **context-check-hook**은 정해진 텍스트 파일 하나를 Claude의 문맥에 출력하는 일만 합니다.

**읽는 것**
- 요청의 뜻을 파악하려고 현재 대화와, 그 세션에서 Claude가 이미 볼 수 있는 파일과 메모리를 읽습니다.

**쓰는 것**
- 사용자가 확정하거나 바로잡은 해석(예: "정리해 줘"는 삭제가 아니라 요약)을 **사용자 컴퓨터**의 파일에 적습니다.
  - `~/.claude/context-check/nuance-dictionary.md` (개인 사전)
  - 작업 폴더의 `.claude/glossary.md` (프로젝트 용어집)
- 파일을 쓸 수 없는 claude.ai에서는 메모리 기능이 켜져 있으면 메모리에 한 줄을 저장하고, 아니면 복사할 줄을 보여 줍니다.
- 사용자가 확정하거나 바로잡은 해석만 기록합니다. Claude의 추정은 기록하지 않고, 기록할 때마다 한 줄로 알립니다.
- 이름, 이메일, 주소, 비밀번호, 결제 정보를 모으지 않습니다.

**보내는 것**
- 없습니다. 네트워크 요청을 하지 않으며, 제작자나 제3자에게 어떤 데이터도 보내지 않습니다. 제작자는 따로 운영하는 서비스가 없고, 데이터를 받거나 보관하지 않습니다.

**데이터 지우기**
- 위 파일은 언제든 지우거나 고칠 수 있습니다. 플러그인을 삭제해도 이 파일들은 자동으로 지워지지 않습니다.

**문의**
- https://github.com/win212191-wq/context-check/issues 에 이슈를 남겨 주세요.
