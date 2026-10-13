# RE:Quest · 본부 AI 리터러시 콘텐츠 사이트

업무에서 생긴 "이것도 AI로 될까?"라는 질문을 받아, 먼저 직접 해 보고 따라 할 수 있는 에피소드로 공유하는 사이트입니다.

## 폴더 구조

```
index.html              사이트 본체 (화면, 디자인, 동작이 모두 이 파일 하나에 있어요)
data/quests.json        에피소드 목록과 사이트 설정 (제목, 소개, 썸네일, 구글 폼 연결 등)
quests/ep01.html        EP.01 본문 (알고 시작하기 · 직접 해보기 · 정리)
quests/_template.html   새 에피소드를 만들 때 복사해서 쓰는 틀
assets/ep01/            EP.01에 쓰는 그림 · 실습 영상 · 썸네일(thumb.svg) · 대표 이미지(cover.svg)
slides/ep01/            EP.01 발표 슬라이드 원본 이미지 (01.jpg ~ 25.jpg)
```

## 사이트 미리 보기

`index.html`을 더블클릭해서 열면 에피소드 목록이 나오지 않아요. 사이트가 `data/quests.json`과 `quests/ep01.html`을 불러와서 화면을 만드는데, 브라우저가 내 컴퓨터 파일을 이렇게 불러오는 것을 막기 때문이에요. 아래 중 한 가지 방법으로 열어 주세요.

- **Claude에 맡기기:** "이 저장소를 사이트로 올려줘"라고 요청하면 사이트 주소를 만들어 줘요.
- **VS Code:** 'Live Server' 확장을 설치하고, `index.html`에서 오른쪽 클릭 → Open with Live Server를 눌러요.
- **터미널:** 이 폴더에서 `python -m http.server 8000`을 실행하고 브라우저에서 `http://localhost:8000`을 열어요.

## 자주 바꾸는 곳

| 바꾸고 싶은 것 | 파일 | 위치 |
|---|---|---|
| 에피소드 제목 · 소개 · 소요시간 | `data/quests.json` | `episodes` 안의 `title`, `lead`, `minutes` |
| 도입장 '오늘의 질문' | `data/quests.json` | `goal.label`, `goal.line` |
| 홈 카드 썸네일 / 도입장 대표 이미지 | `data/quests.json` | `thumb`, `cover`에 그림 경로를 넣어요 |
| 리퀘스트를 받는 구글 폼 | `data/quests.json` | `settings.googleForm` (`url`과 질문별 `entry` 번호) |
| 본문 내용 | `quests/ep01.html` | 페이지는 `<h3 class="sub">`가 나올 때마다 한 쪽씩 나뉘어요 |

## 새 에피소드 추가하기

1. `quests/_template.html`을 복사해 `quests/ep02.html`로 저장하고 내용을 채워요. 파일 맨 위 설명에 쓸 수 있는 부품이 정리되어 있어요.
2. 그림과 영상은 `assets/ep02/`에 넣어요.
3. `data/quests.json`의 `episodes` 목록에 EP.02 정보를 추가해요. 날짜가 가장 최근인 에피소드가 홈의 대표 카드가 되고, 나머지는 아래 '지난 에피소드' 목록에 자동으로 쌓여요.

가장 쉬운 방법은 발표 자료를 Claude에게 주면서 "RE:Quest EP.02로 추가해줘"라고 요청하는 거예요.

## 알아둘 점

- **진행 기록:** 진행 상황, 완료 배지, 리퀘스트 작성 중인 내용은 보는 사람의 브라우저에만 저장돼요. 다른 기기나 브라우저로 열면 이어지지 않고, 운영자가 모아서 볼 수 없어요.
- **리퀘스트 접수:** 리퀘스트는 사이트에서 미리 채워진 구글 폼을 연 다음, 보내는 사람이 폼에서 '제출'을 눌러야 접수돼요. 폼의 질문을 지우고 새로 만들면 질문 번호(`entry`)가 바뀌니 `quests.json`도 함께 고쳐 주세요.
- **글꼴:** Noto Sans KR을 Google Fonts에서 불러와요.
