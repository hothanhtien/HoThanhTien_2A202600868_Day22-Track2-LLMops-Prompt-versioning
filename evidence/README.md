# Evidence — Day 22: LangSmith + Prompt Versioning

## Kết quả RAGAS: V1 vs V2

| Metric | V1 (ngắn gọn) | V2 (có cấu trúc) | Winner |
|---|---|---|---|
| faithfulness | **0.9551** | 0.9176 | V1 |
| answer_relevancy | **0.9152** | 0.8883 | V1 |
| context_recall | 1.0000 | 1.0000 | Tie |
| context_precision | **0.9450** | 0.9417 | V1 |

## Phân tích V1 vs V2

**V1 đạt điểm cao hơn trên hầu hết các metrics** vì prompt ngắn gọn, ràng buộc rõ ràng (2-4 câu) giúp LLM bám sát context hơn, ít bịa đặt thông tin ngoài context hơn → faithfulness cao hơn.

**V2 có answer_relevancy thấp hơn** vì yêu cầu viết dài hơn (3-5 câu) dễ khiến model thêm thông tin ngoài câu hỏi gốc, làm giảm độ liên quan của câu trả lời.

**context_recall cả 2 đều đạt 1.0** cho thấy FAISS retriever với k=3 đã lấy đủ context cần thiết cho mọi câu hỏi trong bộ QA.

## Danh sách file evidence

| File | Mô tả |
|---|---|
| `01_langsmith_traces.jpg` | LangSmith dashboard — 50+ traces từ bước 1 |
| `02_prompt_hub.jpg` | Prompt Hub — 2 phiên bản prompt đã push |
| `02_ab_routing_log.txt` | Log A/B routing: V1=19 câu, V2=31 câu / 50 tổng |
| `03_ragas_scores.jpg` | Terminal output bảng so sánh RAGAS V1 vs V2 |
| `03_ragas_report.json` | Báo cáo JSON đầy đủ từ RAGAS evaluation |
| `04_pii_demo_log.txt` | Demo PIIDetector: redact email, phone, SSN, credit card |
| `04_json_demo_log.txt` | Demo JSONFormatter: sửa fences, quotes, trailing commas |
