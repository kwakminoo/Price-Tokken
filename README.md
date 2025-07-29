# Price-Tokken

# AI 토큰 가격 비교 사이트 (한국어 버전)

## 개요
이 프로젝트는 **한국 개발자와 크리에이터**를 대상으로,  
GPT, Claude, Gemini, Llama, Stable Diffusion 등 **최신 AI 모델들의 토큰당 요금과 성능**을  
**한눈에 비교할 수 있는 웹사이트**를 제작하는 것을 목표로 합니다.

**pricepertoken.com**의 단순한 UI를 유지하면서,  
카테고리별 모델 분류, 컬럼 커스터마이즈, 원화 환산, 비용 계산 기능을 추가합니다.

---

## 핵심 기능

### 1. 카테고리별 AI 모델 비교
- **대화형 AI (챗봇/문서 처리)**  
  GPT-4o, Claude 3.5, Gemini 1.5 Pro, Llama 3.1, HyperCLOVA X 등

- **코딩 특화 AI**  
  GPT-4o-mini (코딩), Claude Sonnet (코딩), Cursor Code AI, Tabnine, Replit Code 등

- **이미지 생성형 AI**  
  DALL·E 3, MidJourney, Stable Diffusion XL, Firefly, Ideogram 등

- **영상 생성형 AI**  
  Runway Gen-3, Pika Labs, Stable Video Diffusion, Kling AI 등

- **기타 AI (음성/멀티모달/분석)**  
  OpenAI TTS, Whisper, ElevenLabs, Descript AI, Speechmatics 등

---

### 2. 표 기반 UI (컬럼 커스터마이즈)
- **기본 표시 (항상 켜짐)**  
  - Input 가격 (1K 토큰, USD)  
  - Output 가격 (1K 토큰, USD)  
  - 원화 환산 가격 (1K 토큰)

- **토글로 켜고 끌 수 있는 항목**  
  - Context 크기 (최대 입력 길이)  
  - 벤치마크/성능 점수 (MMLU, HumanEval, 이미지 품질 등)  
  - 모델 속도/지연 시간  
  - 월 예상 비용 계산기 버튼  
  - 지원 언어 (한국어 포함 여부)  
  - API 제공 여부 및 사용 편의성  
  - 모델 출시일 및 업데이트 주기  
  - 무료/오픈소스 대체 모델 링크

---

### 3. 추가 기능
1. **비용 계산기 (표 하단 배치)**  
   - 토큰 수와 요청 횟수를 입력하면 **카테고리별 예상 월 요금** 계산  
   - **실시간 환율 API** 연동 (원/달러 변환)

2. **가격 변동 알림**  
   - 이메일, 카카오톡, 웹 푸시 알림 지원  
   - 예: *"Claude 3.5 가격 인하 알림"*

3. **벤치마크 그래프**  
   - 토글 시 모델 성능/가격 비율을 그래프로 시각화

---

## 사이트 구조 (사용자 흐름)
1. 접속 시 **대화형 AI 카테고리 표**가 기본 노출  
2. 상단 **카테고리 탭**을 클릭해 코딩, 이미지, 영상, 기타 카테고리로 전환  
3. **컬럼 토글 메뉴**로 "성능", "속도", "언어 지원" 등 원하는 데이터만 표시  
4. **하단 비용 계산기**로 사용량 기반 예상 요금 확인  
5. **알림 구독**으로 가격 변동이나 신규 모델 출시 시 알림 수신

---

## 기술 스택
- **프론트엔드:** Next.js (React)  
- **백엔드:** Supabase (PostgreSQL + Edge Functions)  
- **데이터 업데이트:** 공식 가격 문서/API 크롤링 (1일 1회 자동)  
- **환율 API:** Fixer.io 또는 오픈 환율 API 연동

---

## 데이터셋 관리
- 카테고리별 주요 모델 **20~30개 데이터** (2025년 7월 기준)  
- CSV 또는 JSON 형태로 관리 → Supabase에 저장  
- 항목: 모델명, 카테고리, Input/Output 가격(USD), 원화 환산, Context 크기, 성능 점수, API 지원, 출시일

---

## 향후 확장 기능
- **모델 검색 및 필터** (가격/성능/지원 언어별)  
- **한국어 성능 벤치마크 리포트** (번역, QA, 코드, 이미지 생성 등)  
- **프리미엄 기능 (유료)**  
  - 대량 API 가격 추적 및 알림  
  - 실시간 사용량 기반 비용 추적 (OpenAI, Anthropic API 연동)

---

## 설치 및 실행 (개발 단계)
```bash
# 프로젝트 클론
git clone https://github.com/your-repo/token-price-kor.git
cd token-price-kor

# 의존성 설치
npm install

# 개발 서버 실행
npm run dev


## TODO (1단계 MVP)
- 카테고리별 표 + 탭 UI 구현
-  컬럼 토글 기능 구현
- 초기 데이터셋 (CSV) 적용
- 환율 변환 및 비용 계산기 연결
- 가격 변동 알림(이메일/카카오톡) 기본 세팅
