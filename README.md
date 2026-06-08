# portfolio.suhyeokhan.com

Suhyeok Han의 포트폴리오 정적 사이트. 빌드 도구 없이 순수 HTML/CSS로 동작합니다.

## 구조

```
portfolio.suhyeokhan.com/
├── index.html              # 메인 (프로필 + 카테고리 목록)
├── CNAME                   # 커스텀 도메인 (portfolio.suhyeokhan.com)
├── assets/
│   ├── css/style.css       # 전체 스타일
│   └── img/                # 이미지 (placeholder 포함)
├── categories/             # 카테고리별 목록 페이지
│   ├── uiux.html
│   ├── visual-design.html
│   ├── fashion-design.html
│   └── etc.html
└── works/                  # 개별 작업물(게시글) 페이지
    └── uiux/
        ├── project-1.html
        ├── project-2.html
        └── project-3.html
```

흐름: **메인(카테고리 목록)** → 카테고리 클릭 → **카테고리 페이지(작업물 목록)** → 작업물 클릭 → **작업물 게시글 페이지**.

## 로컬에서 보기

`index.html`을 브라우저로 바로 열어도 되고, 간단한 서버를 띄워도 됩니다:

```bash
cd portfolio.suhyeokhan.com
python3 -m http.server 8000
# http://localhost:8000 접속
```

## 채워 넣어야 할 곳 (`<!-- TODO -->` 표시)

- **프로필 사진**: `assets/img/profile-placeholder.svg` → 실제 사진(예: `assets/img/profile.jpg`)으로 교체 후 `index.html`의 `<img src>` 수정
- **한 줄 소개**: `index.html`의 `.profile__bio` 문구
- **작업물 이미지/설명/링크**: `works/uiux/*.html`의 이미지, 본문, `View Project` 링크(`href`)

## 새 작업물 추가하기

1. `works/<카테고리>/project-N.html` 파일을 기존 파일 복사해서 생성
2. 해당 카테고리 페이지(`categories/<카테고리>.html`)의 `.work-grid`에 `<li class="work-card">…</li>` 항목 추가 후 새 파일로 링크

비어 있는 카테고리(Visual Design / Fashion Design / Etc.)는 `categories/uiux.html`의 `.work-grid` 구조를 복사해 채우면 됩니다.

## 배포 (GitHub Pages)

1. 이 폴더를 GitHub 저장소로 push
2. 저장소 **Settings → Pages** 에서 source를 `main` 브랜치 / `/ (root)`로 설정
3. `CNAME` 파일이 커스텀 도메인을 처리합니다 (`portfolio.suhyeokhan.com`)
4. DNS 제공업체에서 `portfolio` 서브도메인에 **CNAME 레코드** 추가 → `<username>.github.io` 를 가리키도록 설정

> 메인 도메인(`suhyeokhan.com`)은 건드리지 않고, `portfolio` 서브도메인만 추가하면 됩니다.
