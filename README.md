# FILTER_log

대학생연합 사진동아리 FILTER의 공식 GitHub Pages + Jekyll 블로그 저장소입니다.
비전공자도 Pages CMS UI만으로 글을 작성할 수 있도록 설정했으며, 저장 결과는 Jekyll 표준 구조를 그대로 유지합니다.

## 배포 방식

- 저장소 이름이 `filter-log.github.io` 이므로 GitHub Pages 조직 사이트로 배포됩니다.
- 별도 프레임워크 없이 GitHub Pages의 기본 Jekyll 동작을 사용합니다.
- 게시글은 `_posts/` 폴더의 Markdown 파일로 관리됩니다.

## Pages CMS를 사용하는 목적

- 동아리 운영진과 구성원이 코드 수정 없이 브라우저 UI에서 새 글을 작성할 수 있습니다.
- 작성된 글은 자동으로 `_posts/`에 저장되어 기존 Jekyll 템플릿에서 바로 렌더링됩니다.
- 대표 이미지와 본문 이미지는 `assets/images/`에 저장되어 경로 관리가 단순합니다.

## 주요 파일 구조

- `_config.yml`: 사이트 기본 설정
- `_layouts/default.html`: 공통 레이아웃
- `_layouts/post.html`: 글 상세 레이아웃
- `_includes/label-map.html`: 내부값을 화면용 라벨로 변환하는 공통 include
- `_posts/`: 게시글 저장 위치
- `assets/images/`: 대표 이미지와 본문 이미지 저장 위치
- `.pages.yml`: Pages CMS 설정
- `index.html`: 홈
- `posts.html`: 전체 글 목록 소스 파일, 실제 페이지 경로는 `/posts/`

## Pages CMS 저장 구조

- 새 글 저장 위치: `_posts/`
- 대표 이미지 저장 위치: `assets/images/`
- 본문 이미지 저장 위치: `assets/images/`
- 파일명 패턴: `"{year}-{month}-{day}-{primary}.md"`
- 본문 편집기: `rich-text`

## Pages CMS에서 새 글 작성하는 기본 절차

1. `https://app.pagescms.org/` 에 GitHub 계정으로 로그인합니다.
2. `filter-log.github.io` 저장소와 운영 브랜치를 선택합니다.
3. `블로그 글` 컬렉션에서 새 글을 생성합니다.
4. 제목, 날짜, 요약, 대분류, 카테고리, 대표 이미지, 태그, 본문을 입력합니다.
5. 저장하면 `_posts/` 아래에 날짜 기반 파일명이 자동 생성됩니다.
6. GitHub Pages가 이를 빌드해 사이트에 반영합니다.

## Pages CMS 필드 구성

- `layout`: 숨김 필드, 기본값 `post`
- `title`: 제목
- `date`: 날짜
- `summary`: 요약
- `group`: 대분류
- `category`: 카테고리
- `coverImage`: 대표 이미지
- `tags`: 태그 목록
- `body`: 본문

## 내부값과 화면 표시값

Pages CMS의 선택 UI에서는 한글 라벨을 보여주지만, 실제 front matter에는 안전한 영문 내부값이 저장됩니다.
블로그 화면에서는 `_includes/label-map.html` 이 내부값을 한글 표시값으로 변환합니다.

### group

| 저장값 | 화면 표시 |
| --- | --- |
| `notice` | 공지 |
| `11th` | 11기 |
| `12th` | 12기 |

### category

| 저장값 | 화면 표시 |
| --- | --- |
| `notice_general` | 일반공지 |
| `regular` | 정기출사 |
| `flash` | 번개출사 |
| `special` | ★ 특별편 ★ |
| `exhibition` | 전시회 |

## 현재 분류 구조

- group: `notice`, `11th`, `12th`
- category: `notice_general`, `regular`, `flash`, `special`, `exhibition`

기수 구분은 `group`에서만 처리합니다.
`category`에는 기수 정보를 넣지 않습니다.

## 운영 기준

- 블로그 글 작성은 11기부터 시작합니다.
- 홈에서는 최신 글 5개와 최근 공지 3개를 자동으로 보여줍니다.
- 전체 글 목록은 `/posts/` 경로에서 자동 생성됩니다.
- 글 상세 페이지 URL은 `/posts/:year/:month/:day/:title/` 형식을 사용합니다.

## 추후 기수 추가 방법

13기, 14기 등을 추가할 때는 기본적으로 아래만 수정하면 됩니다.

- `.pages.yml`: `group` 선택 옵션 추가
- `_includes/label-map.html`: 새 group의 화면 표시 라벨 추가
- `README.md`: 운영 문서 갱신

`category`는 공통값 구조이므로, 기수가 늘어나도 category는 그대로 유지할 수 있습니다.
