# PUBG HUD Icons

흰색 실루엣 + grain 텍스처 — PUBG HUD / 데스피드 / 무기 슬롯에 쓰는 스타일.

## 출처

[pubg/api-assets](https://github.com/pubg/api-assets) (PUBG 공식 API 자산 레포). 모든 아이콘은 `Assets/Icons/Item/...` 경로에서 가져옴.

## 구조

```
pubg-hud-icons/
├── weapons/
│   ├── main/        45개 — AR/DMR/SR/SMG/SG/LMG/Crossbow 등 주무기
│   ├── handgun/      9개 — 권총 (DesertEagle, G18, M1911, M9, Nagant, Rhino, Sawnoff, vz61, FlareGun)
│   └── melee/        4개 — 근접 (Cowbar=쇠지렛대, Machete=마체테, Pan=프라이팬, Sickle=낫)
└── throwables/       9개 — Grenade, SmokeBomb, FlashBang, Molotov, C4, DecoyGrenade, BluezoneGrenade, StickyGrenade, SpikeTrap
```

총 67개.

## 네이밍 규칙

`Item_Weapon_<Name>_C.png` 또는 `Item_Weapon_<Name>_c.png` (FlashBang 은 소문자 c — 원본 그대로)

## 사용 예시

```html
<img src="/figma-assets/pubg-hud-icons/weapons/main/Item_Weapon_AK47_C.png" alt="AKM">
<img src="/figma-assets/pubg-hud-icons/throwables/Item_Weapon_Grenade_C.png" alt="Frag">
```

CSS 배경으로:
```css
.hud-icon-akm {
  background: url('/figma-assets/pubg-hud-icons/weapons/main/Item_Weapon_AK47_C.png') no-repeat center / contain;
}
```

## 회복 / 부스트 아이템

흰 실루엣 버전은 이 repo 에 없음 (`Assets/Item/Use/Heal/`, `Boost/` 에는 컬러 인벤 아이콘만). 필요 시:
- 임시: CSS `filter: brightness(0) invert(1)` 로 컬러 PNG 단색화
- 진짜 실루엣 필요하면: 게임에서 직접 추출 (UE Editor / FModel)

## 갱신

새 패치로 무기 추가되면:
```powershell
# GitHub API → 일괄 재다운로드
$base = "<프로젝트>\public\figma-assets\pubg-hud-icons"
$apiPaths = @("Assets/Icons/Item/Weapon/Main", ...)
# (전체 스크립트는 작업 히스토리 참조)
```
