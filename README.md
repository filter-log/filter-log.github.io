# FILTER_log

대학생연합 사진동아리 FILTER의 공식 GitHub Pages + Jekyll 블로그 저장소입니다.
동아리 기록과 홍보를 동시에 수행할 수 있도록 최소 구조로 구성했으며, 비전공자도 Pages CMS UI에서 글을 작성할 수 있게 설정했습니다.

## 배포 방식

- 저장소 이름이 `filter-log.github.io` 이므로 GitHub Pages 조직 사이트로 배포됩니다.
- 별도 프레임워크 없이 Jekyll 기본 동작을 사용합니다.
- 글은 루트의 `_posts/` 폴더에 Markdown 파일로 저장되고, GitHub Pages가 이를 자동 빌드해 게시합니다.

## 주요 파일 구조

- `_config.yml`: 사이트 기본 설정
- `_layouts/default.html`: 공통 레이아웃
- `_layouts/post.html`: 글 상세 레이아웃
- `_includes/label-map.html`: 내부값을 화면용 한글 라벨로 변환
- `_posts/`: 게시글 저장 위치
- `assets/css/style.css`: 전체 스타일
- `assets/images/`: 대표 이미지 및 본문 이미지 저장 위치
- `.pages.yml`: Pages CMS 설정
- `index.html`: 홈
- `posts.html`: 전체 글 목록

## Pages CMS 글 작성 방법

1. `https://app.pagescms.org/` 에 GitHub 계정으로 로그인합니다.
2. `filter-log.github.io` 저장소와 운영 브랜치를 선택합니다.
3. 좌측 메뉴의 `게시글` 컬렉션에서 새 글을 작성합니다.
4. 제목, 날짜, 요약, 대분류, 세부분류, 대표 이미지, 태그, 본문을 입력한 뒤 저장합니다.
5. 저장하면 `_posts/` 아래에 `YYYY-MM-DD-title.md` 형식의 Markdown 파일이 생성됩니다.

## 글과 이미지 저장 위치

- 게시글: `_posts/`
- 대표 이미지 및 본문 이미지: `assets/images/`
- Pages CMS의 media 설정:
  - input: `assets/images`
  - output: `/assets/images`

## 내부값과 화면 표시값

게시글 front matter와 Pages CMS 저장값은 안전한 영문 내부값을 사용합니다.
실제 블로그 화면에서는 `_includes/label-map.html` 에서 한글 라벨로 변환해 출력합니다.

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
| `regular_11` | 정기출사_11기 |
| `flash_11` | 번개출사_11기 |
| `special_11` | ★ 특별편 ★ |
| `regular_12` | 정기출사_12기 |
| `flash_12` | 번개출사_12기 |
| `special_12` | ★ 특별편 ★ |

## 현재 카테고리 구조

- 대분류(group): `notice`, `11th`, `12th`
- 세부분류(category): `notice_general`, `regular_11`, `flash_11`, `special_11`, `regular_12`, `flash_12`, `special_12`

## 운영 기준

- 블로그 글 작성은 11기부터 시작합니다.
- 홈 화면에는 최신 글 5개와 최근 공지 3개가 자동 표시됩니다.
- 전체 글 목록은 `posts.html` 에서 자동 생성됩니다.
- 글 상세 페이지 URL은 `/posts/:year/:month/:day/:title/` 형식을 사용합니다.

## 기수 확장 시 수정할 곳

13기, 14기 등 새로운 기수를 추가할 때는 아래 파일을 함께 수정하면 됩니다.

- `.pages.yml`: 새 `group`, `category` 선택 옵션 추가
- `_includes/label-map.html`: 화면 표시 라벨 추가
- `README.md`: 운영 문서와 카테고리 표 갱신

템플릿 구조 자체는 `_posts/` 기반이므로, 라벨과 CMS 옵션만 추가하면 같은 방식으로 계속 운영할 수 있습니다.
