# HUD Prototype

`gametest` 시뮬레이터에서 HUD 작업만 분리해 빠르게 반복하기 위한 별도 프로젝트.

진실의 원천: **[HUD_Prototype.html](HUD_Prototype.html)** (CSS/JS/HTML 인라인, Three.js r128 CDN). 시작 시점은 gametest 의 단일 HTML 을 그대로 복사한 상태 — HUD 외 코드는 점진적으로 정리.

## 실행

```bash
npm install
npm run dev
```

브라우저에서 `http://localhost:5173/` — Vite HMR.

## 구조

```
HUD_Prototype.html        # 본체 (단일 파일)
index.html                # localhost → 본체로 redirect
vite.config.js            # 두 HTML 모두 dist 에 포함
public/figma-assets/      # 빌드 시 dist 루트로 자동 복사
package.json              # vite devDependency
```

## HUD 분리 범위

이 프로젝트에서 다듬을 HUD 요소들 (gametest 에서 가져옴):

- **바닥 아이템/상자 prompt** (`.gd-prompt`) — 키 tap/hold 비주얼 + ring 진행률
- **Pickup preview** (`#quickInvPreview`) — 4열 슬롯 + 카운트 + 무게 %
- **Quick Loot wheel** (`#qlWheel`)
- **포커스 슬롯 회전 테두리** (`@property --fi-focus-angle` + conic-gradient)
- **인벤 하단 통합 가이드** (`#fiBottomGuide`) — tap/hold/스틱/마우스 글리프
- **HUD 무게 아이콘** (`figma-assets/hud-icons/weight-fill.svg`)
- **패드/마우스 글리프** (`figma-assets/pad-glyphs/`, `mouse-glyphs/`)

## gametest 와 동기화

이 프로젝트는 독립적으로 진화. HUD 변경 사항을 gametest 로 역포팅하려면:

1. 여기서 HUD 모듈 (CSS 블록 + JS 함수) 식별
2. gametest 의 동일 위치에 patch

자동 동기화는 안 함 — 단방향(여기 → gametest) 수동 포팅이 기본.
