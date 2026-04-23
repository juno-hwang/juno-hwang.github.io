# Juno Hwang's CV website

github.io 형식으로 배포할 예정인 cv 웹사이트
한국어 영어 두가지를 지원할거임.
모바일 PC에서 비슷하게 잘보였으면 좋겠음

navbar 탭 목록: About, More, Links 
각 서브페이지마다 우측상단에 한영 전환버튼이 있으면 좋겠음. 가급적이면 적절한 이미지 혹은 외부 폰트에셋같은 라이브러리를 사용해서 모든 브라우저 및 운영체제에서 아주 깔끔하고 간결하게 구별되도록하고, 이 한영설정이 페이지 내 전역으로 유지되도록했으면 좋겠음. 이 기본값은 한국어인데, 혹시 브라우저 사용자가 영어권이라는걸 확인할 방법이 있으면 영어를 우선시하도록. footer와 페이지 내부내용만 언어번역이 적용되도록 하면 좋겠음.

# 페이지 반영방식

1. 먼저 About.md, More.md, Links.md 파일을 한국어로 작성 (섹션제목을 만약 파일에서 영어로 작성했다면, 그 제목은 영어로 하는게 맞음. 마찬가지로 한국어파일에서 영어로 된 부분은 한영 둘다 그렇게 표기되는거임.)
2. 그다음 agent에 의해 {page}_en.md  영어파일로 번역 갱신 (적절한 번역을 못찾은 경우 CV.tex참조)
3. 마지막으로 index.html에 반영됨 (About 탭: `About.md` / `About_en.md`를 fetch 후 마크다운 렌더링. More·Links도 같은 방식으로 확장 가능)

## About 이력 행(CV-style) 규칙

- Education / Career / Certificate 등 이력 블록은 **마크다운 텍스트만** 작성한다. 줄 끝 날짜·기간은 공백 뒤 **`( … )` 한 덩어리**로 적는다. 예: `서울대학교 … 학사 (2021)`, `… 조교 (2019–2023)`.
- 한 줄 안에서만 날짜를 괄호로 묶고 싶지 않으면 해당 줄은 자동 레이아웃 대상에서 빠진다.
- 같은 단락 안에서 줄바꿈(`<br>`)으로 여러 줄을 쓴 경우, **각 줄이 모두** 위 `( … )` 패턴을 만족해야 자동 레이아웃이 적용된다.
- 실제 두 컬럼·우측 정렬은 **index.html의 `enhanceAboutCv`**가 렌더 후 DOM에 적용한다. 마크다운 안에 `cv-list` / `cv-line` HTML을 직접 넣지 않는다.
- 자동 처리되는 섹션 제목(대소문자 무관): Education, Career, Certificate, Credentials, Teaching assistant, Experience, Awards, Papers, Books, Invited Talks, Posters & talks 및 한글 `학력`, `경력`, `자격`, `조교`, `수상`, `포스터·구두 발표`(필요 시 목록 확장).