# ✝️ 교회 카드 지출 관리

교회에서 사용하는 카드·이체 결제 내역을 기록하고, 주간 단위로 청구서를 관리하는 웹앱입니다.  
**서버 없이** GitHub Gist 1개를 데이터베이스로 사용합니다.

🌐 **[앱 바로가기](https://cdman28.github.io/chruch-card-tracker/)**

---

## ✨ 주요 기능

| 기능 | 설명 |
|------|------|
| 📋 지출 내역 관리 | 날짜·항목·금액·상호·카드사 기록, 추가/수정/삭제 |
| 🧾 주간 청구서 | 날짜 범위 선택 → 합계 자동 계산 → 청구서 생성 |
| ✅ 입금 처리 | 청구서별 입금 확인 처리 및 상태 표시 |
| 🔍 검색·필터 | 항목명, 상호, 카드사, 기간별 검색 |
| 📥 엑셀 내보내기 | 월별 시트 분리 + 전체내역 시트로 xlsx 다운로드 |
| ⚡ 빠른 입력 | 자주 쓰는 항목(교역자 식사, 커피 등) 원터치 입력 |

---

## 🛠️ 기술 스택

- **Frontend**: HTML / CSS / Vanilla JavaScript (단일 파일, 프레임워크 없음)
- **데이터베이스**: [GitHub Gist](https://gist.github.com/) (서버리스 JSON DB)
- **엑셀 내보내기**: [SheetJS](https://sheetjs.com/) (CDN)
- **배포**: GitHub Pages

---

## 🚀 시작하기

### 1단계 — Gist 생성

1. [gist.github.com](https://gist.github.com/) 접속
2. 파일명: `church-data.json`, 내용: `{}`
3. **Create secret gist** 클릭
4. 생성된 URL에서 **Gist ID** 복사  
   예: `https://gist.github.com/사용자명/`**`abc123def456...`**

### 2단계 — GitHub 토큰(PAT) 준비

1. [GitHub Settings → Developer Settings → Personal Access Tokens](https://github.com/settings/tokens)
2. **`gist`** 스코프 체크 → 토큰 발급
3. 기존에 `gist` 권한이 있는 토큰이 있다면 그대로 사용 가능

### 3단계 — 앱 접속

1. **[앱 열기](https://cdman28.github.io/chruch-card-tracker/)**
2. Gist ID와 PAT 입력 → **연결 확인** → **시작하기**
3. 인증 정보는 브라우저 로컬스토리지에만 저장됩니다

---

## 📱 화면 구성

```
📊 요약    — 이번 달 총 지출 / 카드·이체 소계 / 미입금 청구액 / 최근 내역
📋 내역    — 연도·월 필터, 지출 추가/수정/삭제
🧾 청구    — 주간 청구서 생성, 입금 처리, 상세 내역 보기
🔍 검색    — 키워드·카드사·기간 복합 검색
📥 내보내기 — 헤더 우상단 버튼, 월별 시트 xlsx 다운로드
```

---

## 💾 데이터 구조

```json
{
  "records": [
    {
      "id": "고유ID",
      "date": "2026-06-17",
      "item": "교역자 식사",
      "cardAmount": 42000,
      "cashAmount": 0,
      "merchant": "배민1",
      "card": "삼성",
      "memo": "",
      "createdAt": "ISO 날짜"
    }
  ],
  "billings": [
    {
      "id": "고유ID",
      "title": "6월 1주차",
      "startDate": "2026-06-01",
      "endDate": "2026-06-09",
      "amount": 540660,
      "isPaid": false,
      "paidAt": null,
      "createdAt": "ISO 날짜"
    }
  ],
  "lastUpdated": "ISO 날짜"
}
```

---

## ⚠️ 보안 안내

- PAT는 **소스코드에 절대 저장하지 않습니다**
- 브라우저의 `localStorage` / `sessionStorage`에만 저장됩니다
- 민감한 데이터를 다루므로 **개인 기기에서** 사용을 권장합니다

---

## 📄 라이선스

개인·교회 내부 용도 자유 사용
