`— DESIGN SYSTEM`

# 보고서 덱 스타일 가이드

프로젝트 결과 보고서를 **HTML/CSS 기반 스크롤형 슬라이드 덱**으로 제작할 때 쓰는 디자인 규칙.
방향성은 **다크 에디토리얼(dark editorial)** — 흰 배경 PPT 템플릿을 쓰지 않고, 그리드 배경 위에 타이포그래피 대비와 컬러 액센트로 위계를 만든다.

---

`— 01 · DESIGN TOKENS`

## 1. 디자인 토큰

모든 값은 `:root`의 CSS 변수로 선언하고, 컴포넌트에서는 하드코딩하지 않는다.

### 컬러

| 토큰 | 값 | 용도 |
| --- | --- | --- |
| `--bg` | `#0e1116` | 페이지 배경 |
| `--surface` | `#161b22` | 카드·표·그림 배경 |
| `--surface-2` | `#1c232d` | 카드 내부 강조면(메타 표의 키 열 등) |
| `--line` | `#2a323d` | 모든 경계선 |
| `--text` | `#e8edf3` | 본문 텍스트 |
| `--muted` | `#8b97a6` | 보조 텍스트·캡션·페이지 번호 |
| `--accent` | `#ff7a59` | 1차 액센트 — 키커, 표 헤더, 화살표, 강조 수치 |
| `--accent-2` | `#4fd1c5` | 2차 액센트 — 대조군·보조 개념 |
| `--accent-3` | `#a78bfa` | 3차 액센트 — 부가 개념·아키텍처 강조 |
| `--grid` | `rgba(255,255,255,0.035)` | 배경 그리드 라인 |

컬러는 **의미 단위로만** 쓴다. 같은 슬라이드에서 액센트 3종을 장식 목적으로 동시에 쓰지 않는다.

### 타이포그래피

| 토큰 | 값 |
| --- | --- |
| `--font-sans` | `"Inter", -apple-system, "Apple SD Gothic Neo", "Pretendard", "Segoe UI", Roboto, sans-serif` |
| `--font-mono` | `"JetBrains Mono", "SF Mono", ui-monospace, Menlo, Consolas, monospace` |

| 요소 | 크기 | 규칙 |
| --- | --- | --- |
| `h1` | `clamp(2.4rem, 1.2rem + 4vw, 5rem)` | line-height 1.02, weight 800, letter-spacing -0.02em |
| `h2` | `clamp(1.7rem, 1rem + 2.4vw, 3rem)` | line-height 1.08, weight 750 |
| `h3` | `1.15rem` | weight 700 |
| `p` | `clamp(0.95rem, 0.85rem + 0.3vw, 1.1rem)` | line-height 1.6, color `--muted` |
| kicker | `0.78rem` | mono, uppercase, letter-spacing 0.18em |

본문은 항상 `--muted`, 강조 어구만 `strong`으로 `--text` 또는 액센트를 준다.
`clamp()`로 뷰포트에 따라 스케일하므로 고정 px 폰트 크기를 쓰지 않는다.

---

`— 02 · LAYOUT`

## 2. 레이아웃 골격

### 슬라이드

```css
.slide {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 7vh 8vw;
  border-bottom: 1px solid var(--line);
  background-image:
    linear-gradient(var(--grid) 1px, transparent 1px),
    linear-gradient(90deg, var(--grid) 1px, transparent 1px);
  background-size: 48px 48px;
}
```

- 한 화면 = 한 슬라이드. 스크롤로 넘기고, 키보드(`←/→`, `PageUp/Down`, `Space`)로도 이동한다.
- 패딩은 vh/vw 기반이라 화면 크기에 따라 여백이 함께 커진다.
- 48px 그리드 배경이 전체를 관통하며 문서적 톤을 만든다.

### 컬럼

| 클래스 | 구성 |
| --- | --- |
| `.two-col` | `grid-template-columns: 1fr 1fr`, gap 2.5rem |
| `.three-col` | `repeat(3, 1fr)`, gap 1.4rem |

880px 이하에서 모두 `1fr` 단일 컬럼으로 접힌다.
비대칭이 필요하면 `style="grid-template-columns: 1.25fr 1fr"`처럼 인라인으로 비율만 조정한다.

---

`— 03 · COMPONENTS`

## 3. 컴포넌트

### 키커 (kicker)

섹션 상단의 대문자 모노 라벨. 앞에 28px 액센트 대시가 붙는다.

```css
.kicker::before {
  content: "";
  width: 28px; height: 2px;
  background: var(--accent);
}
```

형식: `02 · 데이터 분석 및 전처리` — 챕터 번호 · 챕터명.

### 카드 (card)

```css
.card {
  border: 1px solid var(--line);
  border-radius: 12px;
  background: var(--surface);
  padding: 1.5rem 1.6rem;
}
```

좌측 액센트 보더로 성격을 구분한다.

| 변형 | 보더 | 의미 |
| --- | --- | --- |
| `.accent-l` | `--accent` | 핵심·결론·주 모델 |
| `.accent2-l` | `--accent-2` | 대조군·비교 대상 |
| `.accent3-l` | `--accent-3` | 부가 설명·주의사항 |

### 메타 카드 (meta-card)

표지 슬라이드의 키/값 표. 키 열은 `--surface-2` 배경 + 고정 폭 130px, 행 사이만 구분선을 두고 바깥 테두리는 라운드 처리한다.

### 목차 (toc-item)

```
[번호] [제목]                              [부제]
```

번호는 모노 액센트, hover 시 `translateX(6px)` + 보더 색 전환. 앵커 링크로 해당 슬라이드에 연결한다.

### 지표 그리드 (metric)

큰 숫자 + 작은 라벨. 숫자는 `clamp(1.8rem, 1rem + 2vw, 2.8rem)` / weight 800, 색은 `.c1/.c2/.c3`로 액센트 3종을 순환시킨다. 4열 그리드, 880px 이하 2열.

### 표 (table)

- 헤더: 모노, `0.78rem`, uppercase, letter-spacing 0.08em, `--accent`
- 셀: `--muted`, 강조는 `td strong`으로 `--text`
- **가로 구분선만** 사용, 세로선과 바깥 테두리는 그리지 않는다
- 최적 행 `tr.best`는 `rgba(255,122,89,0.08)` 배경 + 액센트 텍스트

### 파이프라인 (pipeline)

단계 박스를 가로로 나열하고 `::before`로 `→`를 삽입한다. 마지막 단계는 `.final`로 액센트 보더 + 옅은 액센트 배경을 준다.

### 아키텍처 플로우 (arch-flow)

모노 폰트 박스 + 액센트 화살표. 특별히 강조할 노드는 `.z`로 `--accent-3` 보더/텍스트를 준다.

### 그림 (figure.fig)

```
┌─────────────────────┐
│  img (배경 흰색)     │
├─────────────────────┤
│ 그림 N · 캡션 (mono) │
└─────────────────────┘
```

캡션은 `그림 N` 부분만 액센트, 나머지는 `--muted`. 노트북에서 생성한 차트를 base64로 인라인 삽입해 단일 HTML 파일로 배포한다.

---

`— 04 · RULES`

## 4. 규칙

### 안티 템플릿

- 기본 카드 그리드에 균일 패딩만 준 배치 금지
- 라이브러리 기본값을 그대로 노출하지 않기
- 위계 없이 모든 요소를 같은 강조도로 두지 않기
- 한 슬라이드에 액센트 3종을 장식 목적으로 동시 사용 금지

### 필수 품질 요건

한 슬라이드는 아래 중 최소 4개를 만족해야 한다.

1. 스케일 대비로 만든 명확한 위계
2. 균일 패딩이 아닌 의도적 리듬
3. 카드·보더·배경 그리드로 만든 레이어링
4. 목적이 분명한 타이포그래피 페어링(sans/mono)
5. 장식이 아닌 의미 단위의 컬러 사용
6. 설계된 hover/focus 상태
7. 필요한 곳의 그리드 브레이킹(비대칭 컬럼)
8. 데이터 시각화를 디자인 시스템의 일부로 취급

### 애니메이션

- `transform` / `opacity`만 애니메이션한다
- `width` / `height` / `top` / `left` / `margin` / `padding` / `font-size`는 애니메이션 금지
- transition은 `0.15s ease` 수준으로 짧게

### 인쇄

```css
@media print {
  html { scroll-behavior: auto; }
  * { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
  .slide { page-break-after: always; break-after: page; }
}
```

### 반응형

- 상대 단위(`clamp`, `vh`, `vw`, `rem`)만 사용
- 이미지는 `max-width: 100%`
- 880px 브레이크포인트에서 멀티컬럼 → 단일 컬럼

---

`— 05 · MARKDOWN`

## 5. 마크다운 환경에 적용할 때

GitHub README처럼 CSS를 쓸 수 없는 환경에서는 **구조와 팔레트만** 옮긴다.

| 덱 요소 | 마크다운 대응 |
| --- | --- |
| kicker | 인라인 코드 스팬 `` `— 01 · SECTION` `` (모노 + 대문자가 그대로 재현됨) |
| 슬라이드 구분 | `---` 수평선 |
| 메타 카드 | 2열 표 |
| 목차 | 번호·제목·부제 3열 표 |
| 카드 | 소제목 + 본문, 또는 표 |
| 파이프라인 / 아키텍처 | 코드 블록 안의 아스키 화살표 |
| 태그 | 인라인 코드 스팬 나열 |
| 지표 그리드 | 표 (강조 행은 `**bold**`) |
| 컬러 토큰 | 배지·차트 이미지의 쿼리 파라미터로 전달 |

예시 — GitHub Stats 카드에 덱 팔레트를 그대로 넘긴다.

```
bg_color=0e1116&title_color=ff7a59&text_color=e8edf3&icon_color=4fd1c5
```

배지는 `style=flat-square`를 쓴다. 각진 형태가 덱의 에디토리얼 톤과 맞는다.
