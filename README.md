# 파트 이력 관리 시스템 — 설치 방법

## 1. 저장소에 파일 올리기
```
(저장소)
├─ index.html
└─ data/
   ├─ equipment_default.json   ← 설비 호기·PRC·부위/항목 목록
   └─ history_default.json     ← 교체/CLN 이력 (자동 기록)
```
- 회사로 옮길 때는 각 파일 내용을 텍스트로 복사해서 같은 이름으로 만들면 됩니다.
- 저장소 Settings → Pages 에서 브랜치(main)를 켜면 웹 주소가 생깁니다.

## 2. index.html 맨 아래 `DEFAULT_CONFIG` 수정 (한 번만)
```js
apiBase: 'https://사내GitHub주소/api/v3',   // github.com이면 https://api.github.com
owner:   '저장소 주인 ID 또는 조직명',
repo:    '저장소 이름',
branch:  'main',
```

## 3. 토큰 발급 (각 사용자 1회)
GitHub → Settings → Developer settings → Personal access tokens
- Classic: `repo` 권한 체크
- Fine-grained: 해당 저장소 선택 → Contents **Read and write**

웹페이지 우측 상단 ⚙ 설정 → 토큰 붙여넣기 → "연결 테스트" → "저장 후 연결"
(토큰은 그 사람 브라우저에만 저장되고 저장소에는 올라가지 않습니다)

## 4. 다른 명명법 쓰는 사람
- `data/equipment_팀이름.json` 을 만들거나, ⚙ 설정의 **명명법(프로필)** 칸에 `팀이름` 을 넣고 설비를 추가하면 자동 생성됩니다.
- 주소 뒤에 `?profile=팀이름` 을 붙여서 북마크해도 됩니다.

## 신호등
| 색 | 의미 |
|---|---|
| 🟢 초록 | 실시간 연동 중 (10초마다 확인) |
| 🟡 노랑 깜빡임 | 저장 중 / "시간 수정됨 (이름)" 변경 발생 |
| 🔴 빨강 | 연결·권한 오류 |
| ⚪ 회색 | 로컬 모드 (토큰 미설정, 이 브라우저에만 저장) |
