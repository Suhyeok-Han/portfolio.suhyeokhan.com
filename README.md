# portfolio.suhyeokhan.com

Suhyeok Han의 포트폴리오 정적 사이트. 빌드 도구·JavaScript 없이 순수 HTML/CSS로 동작합니다.

## 구조

```
portfolio.suhyeokhan.com/
├── index.html              # 메인 (프로필 + 카테고리 목록)
├── CNAME                   # 커스텀 도메인 (portfolio.suhyeokhan.com)
├── assets/
│   ├── css/style.css       # 전체 스타일
│   └── img/                # 이미지 (placeholder 포함)
├── uiux/                   # 카테고리 폴더
│   ├── index.html          #   - 아코디언 목록 ("UI/UX" 클릭 시)
│   ├── project-1.html      #   - 사진 클릭 시 이동하는 상세 페이지
│   ├── project-2.html
│   ├── project-3.html      #   - ScreenSaver Workshop redirect
│   └── Screensaver_Clock/  #   - ScreenSaver Workshop 독립 실행 페이지
│       ├── index.html
│       ├── Background Source/
│       └── wooden manequins/
├── visual-design/          # index.html + project-1~2.html
├── fashion-design/         # index.html + project-1~2.html
└── etc/                    # index.html + project-1~2.html
```

흐름: **메인(카테고리 목록)** → 카테고리 클릭 → **카테고리 페이지(아코디언 목록)** → 항목 클릭 시 펼쳐짐 → 펼쳐진 **사진 클릭** → **상세 페이지**.

- 아코디언은 `<details name="...">` 로 구현되어 **한 번에 하나만** 열립니다. (JS 불필요)
- 펼쳐진 영역의 사진(`.acc__media`)을 클릭하면 같은 폴더의 `project-N.html` 상세 페이지 또는 독립 실행 폴더(예: `Screensaver_Clock/`)로 이동합니다.

## 로컬에서 보기

```bash
cd portfolio.suhyeokhan.com
python3 -m http.server 8000
# http://localhost:8000 접속
```

## 채워 넣어야 할 곳 (`<!-- TODO -->` 표시)

- **프로필 사진**: `assets/img/profile-placeholder.svg` → 실제 사진(예: `assets/img/profile.jpg`)으로 교체 후 `index.html`의 `<img src>` 수정
- **한 줄 소개**: `index.html`의 `.profile__bio` 문구
- **항목 제목 / 설명 / 사진**: 각 카테고리의 `index.html` (아코디언의 `.acc__title`, `.acc__desc`, `.acc__media img`)
- **상세 페이지 내용 / 이미지 / 외부 링크**: `<카테고리>/project-N.html` (`.work__title`, `.work__body`, `.work__hero img`, `.work__link`의 `href`) 또는 독립 실행 페이지 폴더의 `index.html`

> 항목 하나를 수정할 때는 보통 2개 파일을 손봅니다 — ① 카테고리 `index.html`의 아코디언, ② 그 항목의 `project-N.html` 상세 페이지.

## 새 작업물 추가하기

1. `<카테고리>/project-N.html` 을 기존 파일을 복사해 생성하고 제목·내용·이미지·링크 수정. 독립 실행 HTML 작업물은 `<카테고리>/<작업물_폴더>/index.html` 형태로 두면 깔끔합니다.
2. 해당 카테고리 `index.html` 의 `.acc-list` 에 `<li><details class="acc" name="<카테고리>">…</details></li>` 블록을 복사·추가하고, `.acc__media` 의 `href` 를 새 `project-N.html` 또는 `<작업물_폴더>/` 로 연결

> 같은 카테고리의 `<details>` 는 `name` 값이 같아야 "한 번에 하나만 열림"이 동작합니다.

## 배포 (GitHub Pages)

1. 이 폴더를 GitHub 저장소로 push
2. 저장소 **Settings → Pages** 에서 source를 `main` 브랜치 / `/ (root)`로 설정
3. `CNAME` 파일이 커스텀 도메인을 처리합니다 (`portfolio.suhyeokhan.com`)
4. DNS 제공업체에서 `portfolio` 서브도메인에 **CNAME 레코드** 추가 → `<username>.github.io` 를 가리키도록 설정

> 메인 도메인(`suhyeokhan.com`)은 건드리지 않고, `portfolio` 서브도메인만 추가하면 됩니다.
