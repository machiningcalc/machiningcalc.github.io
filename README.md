# 기계가공 허브 (Machining Hub)

한국어 절삭가공 계산기 허브. 선반과 밀링, 드릴 가공 현장에서 바로 쓰는 무료 온라인 계산기와 실무 가이드를 제공한다.

- 라이브 주소(배포 후): https://motorwindinghub.github.io/machining-hub/
- 기준: KS B, KEC / 한국 현장 전원 380V 3상 · 220V 단상 · 60Hz
- 모든 계산은 브라우저 안에서 이루어지며 서버로 전송되는 데이터가 없다.

## 계산기 (index.html)

1. **절삭속도·회전수 계산기** (`#calc-speed`) — N = 1000 × Vc ÷ (π × D)
2. **이송속도 계산기** (`#calc-feed`) — f = fz × z, Vf = fz × z × N
3. **가공 시간 계산기** (`#calc-time`) — 1패스 시간 = L ÷ Vf, 총 시간 = 1패스 × 패스 수
4. **공구 수명 계산기** (`#calc-toollife`) — 테일러 식 T = (C ÷ V)^(1/n)
5. **절삭동력 계산기** (`#calc-power`) — Fc = kc × ap × f, Pc = Fc × Vc ÷ 60000, Q = ap × ae × Vf ÷ 1000

참고 표: 재질별 권장 절삭속도(초경 공구)와 권장 날당 이송 — 탄소강, 합금강, 스테인리스강, 주철, 알루미늄 합금, 황동, 티타늄 합금, 플라스틱.

## 가이드 (guides/)

| 파일 | 주제 |
| --- | --- |
| `lathe-basics.html` | 선반 가공 기초 |
| `milling-basics.html` | 밀링 가공 기초 |
| `drilling-basics.html` | 드릴 가공과 구멍 정밀도 |
| `tool-selection.html` | 절삭공구 선택과 재질 |
| `precision-surface-finish.html` | 가공 정밀도와 표면조도 |
| `cutting-fluid.html` | 절삭유 선택과 관리 |

## 검증

- `python3 -m http.server` 로 서빙 후 index.html, 가이드 6개, favicon.svg 를 curl 로 HTTP 200 확인
- 인라인 `<script>` 를 추출해 `node --check` 실행
- 각 계산기의 손계산 예시를 node 로 재계산해 대조
