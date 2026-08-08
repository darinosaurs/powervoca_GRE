# 표제어 2505

"파보카 표제어 리스트"(2,505개)를 120단어 세트 21개로 나눠서 외우는 정적 사이트.
영단어 → 한글 뜻 4지선다, Leitner 5상자 간격 반복, 오답 선택지는 뜻이 비슷한 단어에서 뽑음.

## GitHub Pages에 올리기

1. 새 저장소를 만들고 `index.html`, `words.json`, `README.md`를 올린다.
2. Settings → Pages → Source를 `Deploy from a branch`, 브랜치 `main` / `/ (root)`로 지정.
3. 1~2분 뒤 `https://<아이디>.github.io/<저장소이름>/` 에서 열린다.

## 로컬에서 확인

`index.html`을 더블클릭하면 브라우저가 `fetch`를 막는다. 폴더에서:

```bash
python3 -m http.server 8000
```

후 `http://localhost:8000` 접속.

## 데이터 구조 (`words.json`)

```json
{"i":1,"w":"abandon","m":"1. 포기하다 2. 방종","n":"","s":[2,14,313]}
```

- `i` 표제어 번호 (1–2505, 세트 순서를 결정)
- `w` 단어 · `m` 뜻 · `n` 파생어 메모
- `s` 뜻이 비슷한 단어 번호들. 오답 선택지와 "헷갈리는 이웃" 표시에 쓰인다.

암기 힌트(어근 쪼개기 등)를 넣고 싶으면 `"h"` 필드를 추가한 뒤
`index.html`의 `reveal()` 함수에서 `w.h`를 출력하면 된다.

## 학습 기록

브라우저 `localStorage`의 `pyoje-progress-v1` 키에 `{번호: {b:상자, d:다음복습일, x:틀린횟수}}`로 저장된다.
기기 간 동기화는 없다. 초기화하려면 개발자도구 콘솔에서:

```js
localStorage.removeItem('pyoje-progress-v1')
```

## 상자별 복습 간격

| 상자 | 다음 복습 |
|---|---|
| 1 | 다음 날 |
| 2 | 1일 뒤 |
| 3 | 3일 뒤 |
| 4 | 7일 뒤 |
| 5 | 16일 뒤 |
| 6 | 졸업 (더 안 나옴) |
