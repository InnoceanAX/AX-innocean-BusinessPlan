# INNOCEAN BusinessPlan

BX1본부 2027 사업계획 시스템 (프로토타입) — 캠페인 단위 매출이익·인력(FTE) 계획, 공헌이익/표준보상모델 자동 계산, 팀장·준사업조직·본부장 역할별 입력·승인 워크플로우 솔루션.

🔗 **Production:** (배포 후 채워짐)

---

## 빠른 시작 (인수인계용)

### 1. 로컬에서 보기

별도 빌드 도구 없음 — `index.html`을 브라우저로 열면 됩니다.

```bash
git clone https://github.com/InnoceanAX/AX-innocean-BusinessPlan.git
cd AX-innocean-BusinessPlan
open index.html        # macOS
# 또는 python3 -m http.server 8000 후 http://localhost:8000
```

### 2. Cloud Run 배포

GCP 프로젝트: `innocean-perf-apac-kr`, 리전: `asia-northeast3`

```bash
gcloud run deploy innocean-businessplan \
  --source . \
  --region asia-northeast3 \
  --allow-unauthenticated \
  --port 8080 \
  --quiet
```

배포는 `Dockerfile`(nginx:alpine) + `nginx.conf`(port 8080, Cache-Control: no-store)로 처리됩니다.

---

## 아키텍처

- **단일 HTML 파일** (`index.html`) — React(단일 파일 번들) + 인라인 CSS
- 대상: BX 팀장(캠페인·자기 팀 인력), 준사업조직(협업 인력), 본부장(열람·승인)
- 핵심 계산: 공헌이익1 = 매출이익 − 자기조직 인건비×1.25, 공헌이익2 = 공헌이익1 − 협업 인건비×1.25, 표준보상모델 = 순인건비×2.353
- 헤더/서브헤더/푸터 구조는 [AX-innocean-Report](https://github.com/InnoceanAX/AX-innocean-Report), [AX-innocean-Benchmark](https://github.com/InnoceanAX/AX-innocean-Benchmark)와 동일한 INNOCEAN AX 템플릿을 따릅니다.
- 프로토타입 특성상 데이터는 저장되지 않으며(새로고침 시 초기화), 예시 수치는 가상입니다.

## 원본 산출물

- `20260806_BX1_사업계획_prototype.html` — 원본 프로토타입(헤더/푸터 미적용)
- `20260806_BX1_사업계획_AX.html` — INNOCEAN AX 템플릿 적용본(= `index.html`)
- `20260806_BX1_사업계획_프로토타입_사용설명서.docx` — 사용 설명서 (작성: 사업전략1팀 이기욱 팀장)

## 문의

경영전략본부 사업전략1팀
