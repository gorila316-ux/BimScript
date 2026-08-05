<div align="center">

# BimScript

**Revit과 Civil 3D를 Claude에게 말로 시키세요.**

[![Latest Release](https://img.shields.io/github/v/release/gorila316-ux/BimScript?label=%EC%B5%9C%EC%8B%A0%20%EB%A6%B4%EB%A6%AC%EC%8A%A4&color=2ea44f)](https://github.com/gorila316-ux/BimScript/releases/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)

</div>

BimScript를 설치하면 **Claude(Desktop/Code)** 가 여러분의 **Revit·Civil 3D·Dynamo**를 직접 조작할 수
있게 됩니다. 조회·수정·자동화를 자연어로 시키고, AI가 만든 스크립트는 팔레트에 저장해
다음에 재사용합니다.

> **"Revit 객체 목록을 카테고리 기준으로 일람표로 작성해줘"**
>
> **"Civil 3D 선형을 활용해 Revit에 구조물을 모델링해줘"**
>
> **"방금 그 코드를 스크립트로 저장해줘"**

---

## 설치 및 시작

1. **다운로드** — [최신 릴리스](https://github.com/gorila316-ux/BimScript/releases/latest)를
   내려 받습니다.
2. **설치** — Revit·AutoCAD/Civil 3D·Claude Desktop(트레이까지)을 모두 종료한 뒤 실행합니다.
   애드인·MCP 브리지·Claude 등록까지 전부 자동입니다.

   > [!IMPORTANT]
   > 설치기 첫 실행 때 파란 SmartScreen 화면이 뜨면 **[추가 정보] → [실행]**.
   >
   > **Civil3D/Revit** 첫 실행 때 보안 창이 뜨면 반드시 **[항상 로드]** 를 누르세요.

3. **말 걸기** — Claude를 켜고(재시작 필요) Revit이나 Civil 3D를 연 상태에서
   *"Revit 레벨 목록 보여줘"* 라고 해보세요.

자세한 절차·문제해결: **[INSTALL.md](INSTALL.md)**

---

## 무엇을 시킬 수 있나요

**실무 활용 예시** — 이렇게 시키면 Claude가 필요한 조회·수정·스크립트를 알아서 조합합니다.

- *"Revit 프로젝트의 객체 목록을 카테고리 기준으로 일람표로 작성해줘"*
- *"속성정보 중 Mark를 참고해서 교량 하부 구조물에 해당하는 것만 색상을 적용해 가시성 필터링해줘"*
- *"CAD 도면의 구조물 횡단을 프로파일로 사용하고, Civil 3D 선형을 활용해 Revit에 구조물을 모델링해줘"*

**스크립트 저장·재사용**

- *"방금 그 코드를 'C3D선형 단면스윕'라는 스크립트로 저장해줘. 태그는 Civil3D, Revit, 조회로."*
- *"저장된 스크립트 중 'C3D 단면스윕'을 실행해줘"*

---

## 팔레트 사용법

| 호스트 | 위치 |
|---|---|
| Revit | 리본 → **애드인 탭** → BimScript 아이콘 |
| AutoCAD/Civil 3D | 리본 → **추가 기능 탭** → BimScript 아이콘 |

- 저장된 스크립트는 **카드 이름 클릭 → [실행] 버튼**으로 재실행합니다.
- 태그·패널·검색으로 분류하고, 팔레트는 **현재 호스트의 스크립트만** 보여줍니다.
- 같은 프로그램을 여러 개 띄웠다면, 팔레트 하단 **[연결]** 버튼을 누른 창이 AI의 대상입니다.

---

## 자주 묻는 것

- **보안 창이 자꾸 떠요** — 코드 서명이 없어 뜨는 정상 창이며, 버전 업데이트 때마다 다시
  나옵니다. 항상 [항상 로드]를 누르세요.
- **내 스크립트는 어디 저장되나요** — `%APPDATA%\BimScript\`. 제거해도 지워지지 않습니다.
- **Claude에 도구가 안 보여요** — Claude를 재시작하세요(서버 목록은 시작할 때 읽습니다).
- **뭔가 이상해요** — 시작 메뉴 → BimScript → **"설치 점검"** 더블클릭. 그 화면 캡처가
  문의의 전부입니다.

---

## 지원 범위

| 호스트 | 버전 | 상태 |
|---|---|---|
| Revit (+Dynamo 3.x) | 2025 · 2026 | ✅ |
| AutoCAD / Civil 3D | 2025 · 2026 | ✅ |
| Navisworks | — | 예정 |

- **스크립트 작성·저장·팔레트는 모든 지원 호스트에서 동일**합니다. Dynamo 그래프 제어만 Revit 고유.
- Claude Desktop·Claude Code 모두 지원.

---

## 라이선스 (Attribution)

이 프로젝트는 **BimOnMcp**
(Copyright © 2026 **JungGeun Park (General Soju)**, MIT License)에서 파생됐습니다.
파이프 서버·MCP 브리지·호스트 플러그인의 기반 코드가 여기서 파생됐고, 그 위에 자체
스크립트 팔레트·설치기를 얹었습니다. 원본 저작권 고지를 포함한 전체 제3자 고지는
[LICENSE](LICENSE) 하단에 동봉합니다.

**MIT License.** Autodesk의 승인·보증을 받지 않았습니다. Revit·AutoCAD·Civil 3D·Navisworks는
Autodesk, Inc.의 상표입니다.
