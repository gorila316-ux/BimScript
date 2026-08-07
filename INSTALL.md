# BimScript 설치 안내

Revit에서 AI(Claude)로 모델을 조회하고 스크립트를 실행·저장·재사용하는 도구입니다.

## 1. 필요한 것

| 항목 | 조건 |
|---|---|
| OS | Windows 10/11 (64bit) |
| 저작도구 | **Revit 2025~2027, AutoCAD·Civil 3D 2025~2027, Navisworks Manage 2025 중 하나 이상** — 설치된 것마다 전부 설치됩니다 |
| Claude | Claude Code 또는 Claude Desktop(둘 중 하나 이상 — **Microsoft Store판 Desktop도 지원**) |
| 별도 런타임 | **불필요** — 브리지는 자체 포함(self-contained), 애드인은 호스트 내장 .NET으로 구동 |

## 2. 설치

1. **Revit·AutoCAD/Civil 3D·Claude Desktop을 완전히 종료**합니다(Desktop은 트레이 아이콘까지). 실행 중이면 설치기가 중단시킵니다 — 호스트는 애드인 배치가 깨지고, Desktop은 종료 시점에 Claude 등록을 덮어써 지웁니다.
2. `BimScript_<버전>_setup.exe` 실행 → 라이선스 확인 → 설치.
   - 인터넷에서 받은 직후 첫 실행 때 **파란 "Windows의 PC 보호" 화면**(SmartScreen)이 뜰 수 있습니다.
     **[추가 정보] → [실행]** 을 누르면 됩니다. 코드 서명이 없는 새 배포 파일에 뜨는 표준 안내이며,
     파일 무결성은 릴리스 페이지의 SHA-256으로 확인할 수 있습니다.
3. 설치기가 자동으로 하는 일
   - 감지된 Revit 연도마다 애드인 배치 + AutoCAD/Civil 3D용 번들(`ApplicationPlugins`) 배치
   - MCP 브리지를 `%LOCALAPPDATA%\BimScript\`에 설치
   - Claude(Code/Desktop/Store판 Desktop)에 `BimScript-Revit`·`BimScript-AutoCAD` 서버 등록 — **기존 등록은 보존**합니다

### ⚠ 첫 실행 시 보안 창이 뜹니다 (정상)

Revit·Civil 3D를 켜면 **"게시자를 확인할 수 없습니다"** 계열의 보안 창이 나옵니다.
→ **반드시 [항상 로드]** 를 누르십시오.

- 기본 선택이 **[로드하지 않음]** 이라, 무심코 Enter를 치면 **BimScript가 조용히 빠집니다.**
  ("설치했는데 아무것도 안 보인다"의 대부분이 이 경우입니다.)
- 코드 서명이 없어서 뜨는 창이며, **버전을 업데이트할 때마다 다시 나옵니다.**

## 3. 사용

1. 팔레트 열기
   - **Revit**: 리본 → 애드인 탭 → BimScript 패널 → 로봇 아이콘
   - **AutoCAD/Civil 3D**: 리본 → **추가 기능 탭** → BimScript 패널 (명령창 `BIMSCRIPT`도 동일. 추가 기능 탭이 없는 작업공간에선 자체 BimScript 탭)
   - **Navisworks**: 리본 → **도구 애드인 탭** → BimScript 버튼 (도킹 패널로 열립니다)
2. 처음에는 목록이 비어 있습니다. Claude에게 시키면 스크립트가 쌓입니다.
   - 예: *"이 프로젝트의 레벨 목록 보여줘"* → *"방금 코드 스크립트로 저장해줘"*
3. 저장된 스크립트는 팔레트에서 카드 이름 클릭 → [실행] 버튼으로 재실행합니다. 팔레트는 **현재 호스트의 스크립트만** 보여줍니다(Revit 팔레트엔 Revit 것, Civil 3D 팔레트엔 Civil 3D 것).
4. 팔레트 하단 **연결됨 — 이 인스턴스가 MCP 대상입니다**: Revit을 여러 개 띄웠을 때 어느 창이 AI의 대상인지 표시합니다. 바꾸려면 원하는 창에서 **[연결]** 을 누르십시오.

### Claude에서 안 보일 때

Claude Code/Desktop을 **재시작**하십시오(MCP 서버 목록은 시작할 때 읽습니다). 그래도 없으면:

```bash
claude mcp list
```

`BimScript-Revit`이 `✔ Connected`인지 확인합니다.

## 4. 업데이트 · 제거

- **업데이트**: 새 설치기를 실행하면 구판을 자동 제거 후 재설치합니다. (보안 창이 다시 뜹니다 — §2 참조)
- **제거**: 제어판 → 프로그램 → BimScript 제거.
  - **스크립트 라이브러리(`%APPDATA%\BimScript`)는 지우지 않습니다.**
  - Claude 등록 해제는 수동입니다: `claude mcp remove BimScript-Revit`

## 5. 문제가 생기면

가장 먼저: **시작 메뉴 → BimScript → "설치 점검"** 을 더블클릭하십시오. 무엇이 빠졌는지 한눈에 나오고,
문의 시 그 화면 캡처만 보내면 됩니다.

| 증상 | 조치 |
|---|---|
| 리본에 아이콘이 없다 | 보안 창에서 [항상 로드]를 눌렀는지(§2). 호스트 재시작 후 재확인 |
| Civil 3D에서 BimScript 탭이 사라졌다 | 작업공간 전환 직후 잠깐 사라질 수 있으나 자동 복원됩니다 — 몇 초 후에도 없으면 재시작 |
| Claude에 BimScript 도구가 없다 | ①Claude Desktop을 **트레이까지 완전 종료** ②시작 메뉴 → BimScript → **"Claude 등록 복구"** 더블클릭 ③Desktop 재실행. (Desktop이 켜진 채 복구하면 종료 시점에 등록이 덮어써집니다) |
| 팔레트는 뜨는데 Claude가 못 붙는다 | Claude 재시작 · 팔레트 하단 [연결] 클릭 |
| 스크립트가 안 보인다 | 팔레트는 **현재 호스트(Revit)의 스크립트만** 보여줍니다. AI 파이프라인 전용 스크립트는 의도적으로 숨깁니다 |
| 로그를 보고 싶다 | `%LOCALAPPDATA%\BimScript\Logs\` |

## 라이선스

MIT. 이 소프트웨어는 BimOnMcp(© 2026 JungGeun Park, MIT)에서 파생됐습니다.
전체 고지는 설치 폴더의 `license-combined.txt`를 보십시오.

Autodesk의 승인·보증을 받지 않았습니다. Revit은 Autodesk, Inc.의 상표입니다.

## 부록 — Claude 수동 등록

설치기가 "Claude 등록이 자동으로 완료되지 않았습니다"라고 하면(또는 Claude를 나중에 설치했다면),
Claude Code에서 아래 한 줄을 실행합니다.

```
claude mcp add -s user BimScript-Revit -- "%LOCALAPPDATA%\BimScript\BimScriptBridge.exe" --target revit
claude mcp add -s user BimScript-AutoCAD -- "%LOCALAPPDATA%\BimScript\BimScriptBridge.exe" --target autocad
```

확인: `claude mcp list` → `BimScript-Revit`이 `✔ Connected`.

Claude Desktop만 쓰는 경우 `%APPDATA%\Claude\claude_desktop_config.json`의 `mcpServers`에 아래를 추가합니다
(기존 항목은 지우지 마십시오).

```json
"BimScript-Revit": {
  "command": "C:\\Users\\<사용자>\\AppData\\Local\\BimScript\\BimScriptBridge.exe",
  "args": ["--target", "revit"]
}
```
