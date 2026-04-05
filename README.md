# rag_ner

2026-03-01

Version 1.

IOB 파일 입력
    ↓
SpaCy noun chunk + 대문자 토큰 + 생의학 약어 추출
    ↓
_shrink_query()로 모든 subspan 생성
    ↓
GPT 필터링 — 바이오 의미 있는 chunk만 선별 (문장 컨텍스트 포함, 1회)
    ↓
유효한 chunk로 MeSH 온톨로지 검색 (LlamaIndex VectorStoreIndex)
    ↓
GPT에게 문장 + 온톨로지 컨텍스트 전달 → 엔티티 span 추출
    ↓
엔티티 span → 원본 IOB 토큰에 매핑
    ↓
IOB 파일 저장 + 성능 평가


                          Exact  Partial
  Baseline F1            0.5064   0.6859
  RAG F1                 0.5000   0.6623
  Δ F1                  -0.0064  -0.0236
