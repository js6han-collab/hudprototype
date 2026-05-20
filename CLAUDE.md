# hud_prototype — HUD 분리 프로젝트

## What this is

[gametest](../gametest/) (TPS Loot Prototype) 의 HUD 작업만 분리해 빠르게 반복하기 위한 별도 프로젝트. 시작 시점은 gametest 의 단일 HTML 을 그대로 복사한 상태이며, 점진적으로 HUD 외 코드를 정리할 예정.

## Stack (gametest 와 동일)

Single-file vanilla HTML/CSS/JS with **Three.js r128 from CDN**. Vite is a thin dev-server wrapper.

- Source of truth: [HUD_Prototype.html](HUD_Prototype.html)
- Entry redirect: [index.html](index.html)
- Vite config: [vite.config.js](vite.config.js)
- Dev: `npm run dev`
- Build: `npm run build` → `dist/`

**Do NOT** propose ES module extraction, npm `three` migration, TypeScript, or framework introduction unless explicitly asked. Three.js API choices stay r128-compatible.

## HUD 분리 범위

이 프로젝트의 작업 초점:

- 바닥 아이템/상자 prompt (`.gd-prompt` — key tap/hold 비주얼)
- Pickup preview (`#quickInvPreview` — 4열 슬롯 + 카운트 + 무게 %)
- Quick Loot wheel (`#qlWheel`)
- 포커스 슬롯 회전 테두리 (`@property --fi-focus-angle` + conic-gradient)
- 인벤 하단 통합 가이드 (`#fiBottomGuide`)
- 패드/마우스 글리프 ([public/figma-assets/pad-glyphs/](public/figma-assets/pad-glyphs/), [mouse-glyphs/](public/figma-assets/mouse-glyphs/))

## Figma source of truth

`3CzR6SL2LtlGXReIuatj5k` ("PUBG-V UX Part") — gametest 와 동일 Figma 파일. 자주 참조하는 HUD 노드:

- `4515:1209` — Pickup preview 레이아웃
- `4030:5021` — 인게임 픽업 미리보기 위치/크기 참조
- `4515:1202` — weight-fill 아이콘
- `4514:1353` — 스틱 클릭 글리프 (L3/R3)
- `4476:3266` — 마우스 글리프 (LMB/RMB/scroll)
- `4618:169663` — 포커스 슬롯 회전 테두리 (cream/cyan/magenta conic)
- `4515:111788` — 롤렉스 아이콘

## Conventions

- Korean comments are fine.
- gametest 와 별개 git 저장소.
- HUD 변경을 gametest 로 역포팅은 수동 (단방향).

## Notes vs gametest

- HUD 외 코드 (월드 생성, AI, 사격 등) 는 단계적으로 정리. 처음엔 그대로 두고 동작은 유지.
- 이름이 `HUD_Prototype.html` 로 바뀜 — gametest 의 `시뮬레이터_루팅_시스템_Prototype.html` 와 구분.
