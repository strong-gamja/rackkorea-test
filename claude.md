# CLAUDE.md — Rack Korea(랙코리아) 홈페이지 제작 마스터 가이드

> **이 파일의 목적:** "랙코리아 홈페이지 만들어줘"라고 요청받았을 때, 처음부터 끝까지 정해진 순서와 규칙에 따라 B2B 기업용 정적 웹사이트를 완성한다.
> 
> 외부 프레임워크(React/Vue 등)와 백엔드 서버 없이, 오직 HTML/CSS/Vanilla JS 기반으로 고품질의 결과물을 도출한다.

---

## 🚀 시작하기

개발은 아래 **4개 Phase**를 순서대로 진행한다.

```text
Phase 1: 기획 및 브랜딩 확인
    ↓
Phase 2: 프론트엔드 개발 (정적 페이지 4개 구현)
    ↓
Phase 3: 폼 전송 연동 (mailto 방식)
    ↓
Phase 4: 배포 (GitHub Pages)
```

**각 Phase 완료 후 사용자에게 스크린샷이나 코드 구성을 확인받고 다음 Phase로 진행한다.**

---

# Phase 1: 기획 및 브랜딩 확인

> B2B 물류/산업 설비 기업에 맞는 무겁지 않으면서도 신뢰감 있는 "대기업 B2B SaaS" 느낌의 디자인 시스템을 확립한다.

## 1️⃣ 핵심 디자인 시스템
* **테마 색상:** * Primary: Navy (`#0f172a`)
    * Accent: Orange (`#f97316`)
    * Background: Light Gray (`bg-slate-50` 또는 `#f8fafc`) - 가독성을 위해 흰색과 번갈아 사용
* **폰트:** Noto Sans KR
* **인터랙션 (또로롱 효과):** * 공통 클래스 `.rk-card` 및 `.rk-img` 사용. 
    * Hover 시 카드가 살짝 위로 올라가고, 그림자가 깊어지며, 이미지가 미세하게 확대되는 입체 효과 필수.

## 2️⃣ 파일 구조 및 기술 스택
* **배포 환경:** GitHub Pages (서버 없음)
* **기술 스택:** 순수 HTML + CSS (Tailwind CDN) + Vanilla JS
* **파일 구조:**
    ```text
    /index.html (메인)
    /about.html (제품 소개)
    /portfolio.html (설치 사례)
    /contact.html (문의)
    /style.css (공통 스타일)
    /assets/logo.png
    /assets/photos/... (이미지 폴더)
    ```

---

# Phase 2: 프론트엔드 개발

> 각 페이지별 요구사항에 맞춰 HTML/CSS/JS 코드를 작성한다.

## 1️⃣ 공통 네비게이션 (GNB)
* **구성:** 로고 + 메뉴(홈/제품 소개/설치사례/문의하기) + 문의하기 버튼 + KR/EN 토글
* **언어 토글 (지구본 아이콘):** * 스크롤 전 (히어로 위): 흰색 글씨 + 글래스모피즘(반투명) 버튼
    * 스크롤 후 (네비 배경이 흰색이 될 때): Navy 글씨 + 흰색 배경 버튼
    * *Vanilla JS로 스크롤 이벤트를 감지하여 자동 전환되도록 구현할 것.*

## 2️⃣ 페이지별 구현 필수 섹션

### 📌 index.html (메인)
1.  **Hero:** 풀스크린 배경 슬라이더 (3장, 자동 전환, Dots, 텍스트 오버레이)
2.  **Space Maximization:** 좌측 이미지 슬라이더 (hover 시 멈춤) / 우측 설명 및 KPI 카드 2개 (하단 주황 라인 강조)
3.  **WHY MOBILE RACK:** 성과 배지가 포함된 4개의 카드 (공간 비용 절감 등, 텍스트 넘침 clamp 처리)
4.  **Media Center:** 유튜브/쇼츠/블로그 카드 (재생 버튼 오버레이)
    * 영상: `https://youtu.be/hEt7ZSBKqSs?si=XO83Ir8mRW3N9k8u`
    * 쇼츠: `https://youtube.com/shorts/2jipvvDY1IM?si=msw8DdQ1ttGw0Mpg`
    * 블로그: `https://blog.naver.com/rackkorea_official/224204057976`

### 📌 about.html (제품 소개)
1.  **작동 원리:** 좌측 슬라이더 + 우측 3단계 스텝 카드
2.  **비교 섹션:** 전동랙 vs 고정랙 상단 카드 + 하단 상세 비교표 (표 헤더 Navy, 강조 지점 Orange/Emerald)
3.  **Technology Types:** 레일 vs 노레일 카드 (높이/패딩 완벽히 일치, hover 입체 효과)
4.  **Certification:** 인증/특허 마크 4개 카드 (배경 `bg-slate-50`)
5.  **Quick Quote:** 하단 문의 유도 바 (한 줄 설명 + 버튼)

### 📌 portfolio.html (설치 사례)
1.  **상단:** 타이틀 + 웨이브 디자인 + KPI 4개 카드
2.  **필터 탭:** 전체/냉동/일반/부품/자동차/전자/식품 (JS로 필터링 구현)
3.  **그리드 및 모달:** * 6개 이상 카드 배치. Hover 시 중앙에 "사진 보기" 버튼 등장.
    * 클릭 시 JS 기반 모달 오픈 (상단 메인 이미지 + 좌측 썸네일 3장 + 카운터 + 좌우 화살표). 데이터는 JS 배열로 관리.

### 📌 contact.html (문의하기)
* 폼 아래에 '고객 지원 서비스' 3개 카드 배치
* 폼 필드: 업체명, 담당자명, 연락처, 창고 규모, 파렛트 규격(가로/세로/높이/무게), 단수, 층수, 지게차 타입, 환경(상온/저온 등).

## 💡 품질 및 반응형 가이드 (필수)
* **모바일 퍼스트:** 모든 섹션은 모바일에서 깨짐 없이 1열로 자연스럽게 떨어져야 함.
* **섹션 전환:** 흰색 배경과 연한 배경(`bg-slate-50`)이 끊김 없이 부드럽게 이어지도록 패딩 설정.
* 이미지 경로는 제공된 구조를 따르며, 미제공 시 placeholder(`https://placehold.co/...`) 사용.

---

# Phase 3: 폼 전송 연동 (서버리스 방식)

> 정적 호스팅(GitHub Pages)을 사용하므로 백엔드 서버 구축(Supabase 등)은 제외한다. 대신 `mailto` 방식을 고도화하여 폼 데이터를 수집한다.

## 1️⃣ Mailto 기반 폼 제출
* **제출처:** `master@rackkorea.co.kr`
* **동작 방식:** 사용자가 폼을 채우고 '제출' 버튼을 누르면, JS가 폼 데이터를 읽어 깔끔한 텍스트로 포맷팅한 뒤 사용자의 기본 이메일 클라이언트(아웃룩, 메일 앱 등)를 띄운다.
* **파일 첨부 안내:** 서버 업로드가 불가능하므로, UI 상단이나 폼 하단에 *"도면이나 현장 사진은 열리는 메일 창에서 직접 첨부해 주세요."* 라는 안내 문구를 반드시 포함한다.

```javascript
// JS 연동 예시 (contact.html)
function sendEmail(event) {
  event.preventDefault();
  const formData = new FormData(event.target);
  const subject = `[랙코리아 문의] ${formData.get('company')} - 랙 설치 견적 문의`;
  const body = `
  업체명: ${formData.get('company')}
  담당자: ${formData.get('name')}
  연락처: ${formData.get('phone')}
  창고 규모: ${formData.get('size')}
  파렛트 규격: ${formData.get('pallet')}
  지게차 타입: ${formData.get('forklift')}
  환경: ${formData.get('environment')}
  
  -- 첨부파일이 있다면 이 메일에 첨부하여 보내주세요 --
  `;
  window.location.href = `mailto:master@rackkorea.co.kr?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
}
```

---

# Phase 4: 배포 (GitHub Pages)

> 작성된 코드를 GitHub 저장소에 올리고 정적 호스팅을 켠다.

## 👤 사용자가 직접 할 일
1. `https://github.com` 에 로그인하여 새로운 Repository 생성
2. AI가 작성해 준 코드(HTML, CSS, JS)와 이미지 파일들을 업로드 (또는 git push)
3. Repository의 **Settings > Pages** 로 이동
4. Source를 `Deploy from a branch`로 선택하고, Branch를 `main`(또는 master)으로 설정 후 **Save**
5. 수 분 뒤, `https://[사용자명].github.io/[저장소명]` 링크로 사이트 접속 확인

---

# ⚠️ 엄격한 규칙 (제한 사항)

* **절대 금지:** React, Vue, Next.js 등의 프레임워크 사용 금지.
* **절대 금지:** Supabase, Firebase, 별도 DB 등 백엔드 아키텍처 추가 금지.
* **반드시 할 것:** 각 HTML 파일 상단 및 수정이 필요한 곳(이미지 경로, 텍스트 데이터)에 HTML/JS 주석으로 `` 와 같이 명확히 표기할 것.
* **반드시 할 것:** 모든 페이지의 코드는 문법 오류 없이 완전한 형태로 제공할 것.

---
**✅ AI(당신)의 행동 지침:**
이 가이드를 숙지했습니다. 위 조건에 따라 즉시 `/index.html`, `/about.html`, `/portfolio.html`, `/contact.html`, `/style.css`의 완벽한 코드를 작성하여 제공해 주십시오.