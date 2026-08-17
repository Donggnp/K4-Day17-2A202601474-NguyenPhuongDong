# Lab 17 - Báo Cáo Nộp Bài (README Submission)

- **Họ và tên / Student**: Nguyễn Phương Đông
- **Mã sinh viên**: 2A202601474
- **Lớp / Khóa**: K4 - Day 17 AI Lab
- **Kết quả Evaluator (`student`)**: **11/11 PASS (100.0%)**

---

## 1. Kết Quả Benchmark & Baseline

- **Student Implementation**: 11/11 PASS (100% Hit rate), Avg Latency ~1.8s, Avg Token Reduction ~20.2%.
- **No-Memory Baseline**: 2/11 PASS (18.2% Hit rate - chỉ vượt qua 2 case Short-term E01, E10).
- **So sánh (Delta)**: +9 passed cases (+81.8% hit rate).

Báo cáo so sánh chi tiết đã được tự động sinh tại: `reports/comparison.md`.

---

## 2. Trả Lời Các Câu Hỏi Bắt Buộc

### Câu 1: Layer nào quan trọng nhất trong bộ test này? Chi tiết case minh họa.
- **Trả lời**: **Long-term Memory** (kết hợp Context Block) là layer quan trọng nhất trong bộ test này.
- **Minh họa**: Các case `E02`, `E03`, `E08`, `E09` và `E07` phụ thuộc hoàn toàn vào khả năng duy trì thói quen, thông tin cá nhân và open-loop công việc cross-session. Ví dụ ở `E08`, hệ thống phải phân biệt được sự thay đổi công nghệ theo từng dự án của cùng một user (dự án cá nhân ORCHID-27 dùng Python, nhưng dự án BLUEBIRD-42 bắt buộc dùng TypeScript/NestJS).

### Câu 2: Trade-off giữa Managed Context Block (Zep) vs Tự dựng Redis + Qdrant?
- **Managed Zep**:
  - *Ưu điểm*: Tự động xây dựng Temporal Knowledge Graph, tự động trích xuất Facts & Session Summary, quản lý Relevance và Recency theo thời gian thực mà dev không cần viết pipeline xử lý graph phức tạp.
  - *Nhược điểm*: Phụ thuộc vào Managed Cloud API (latency mạng ~1.5 - 2s/call), chi phí theo usage API, khó tùy biến sâu vào thuật toán indexing đồ thị.
- **Self-hosted Redis + Qdrant**:
  - *Ưu điểm*: Toàn quyền kiểm soát latency (cực thấp, <50ms), bảo mật dữ liệu tuyệt đối (on-premise), chi phí hạ tầng cố định.
  - *Nhược điểm*: Phải tự phát triển toàn bộ pipeline trích xuất thực thể, quản lý mâu thuẫn dữ liệu (conflict resolution), sliding budget và compaction thủ công.

### Câu 3: Guardrail chống Memory Poisoning (Khi user cố nạp thông tin sai lệch / Prompt Injection vào Memory)?
- **Giải pháp**:
  1. **Sanitization & Redaction at Ingestion**: Lọc bỏ các mẫu câu dạng System Instruction Override (vd: "Ignore previous instructions", "I am admin") trước khi đưa vào durable memory graph.
  2. **Opt-in & PII Minimization**: Kiểm tra quyền `memory_opt_in` (như trong `src/privacy_guard.py`) và redact các thông tin nhạy cảm trước khi lưu.
  3. **Isolation giữa User Scope và Domain KB Scope**: Phân định rõ ràng giữa User Memory (chỉ ảnh hưởng đến chính user đó) và Standalone Domain KB (chỉ được cập nhật qua kênh quản trị curated, user không thể ghi đè quy tắc domain dùng chung).

---

## 3. Phân Tích Chi Tiết Benchmark (Pha E)

1. **Layer có hit rate thấp nhất**: Khi chưa seed đồ thị tri thức dùng chung, **Semantic Memory** có hit rate 0%. Sau khi seed đầy đủ, tất cả 4 layer đều đạt hit rate 100%.
2. **Query retrieve nhiều token nhất**: Các query thuộc **Long-term Memory** (`E02`, `E03`, `E08`, `E09` ~ 840 tokens) do Zep Context Block tổng hợp toàn bộ bức tranh về user summary + persistent facts.
3. **Case Mixed (`E07`)**: Cần phối hợp **Long-term Memory** (truy xuất sở thích ngôn ngữ Python của Minh) và **Semantic Memory** (truy xuất quy tắc retry `Idempotency-Key` từ domain KB). Evidence bắt buộc: `Python` và `Idempotency-Key`.
4. **Token Reduction**: Student Memory giảm 20.2% lượng token so với full transcript. No-memory baseline giảm 81.8% token đơn giản vì nó không truy xuất dữ liệu nào (dẫn tới thất bại 9/11 case). Token reduction chỉ có giá trị khi đi kèm với Evidence Hit Rate cao.

---

## 4. Nhận Xét Về Recency (E08) & Compaction (E10)

- **E08 (Recency / Conflict handling)**: Minh cập nhật thông tin dự án BLUEBIRD-42 bắt buộc dùng TypeScript/NestJS ở stage 3. Zep Context Block đã xử lý thành công tính mới (recency), giúp agent trả lời chính xác stack của BLUEBIRD-42 mà không bị nhầm lẫn với sở thích Python ở stage 1.
- **E10 (Compaction)**: Chiến lược Sliding Window kết hợp Durable Notes trong `ShortTermMemory` đã giữ lại constraint `REVIEW-DEADLINE-1600` cùng mốc thời gian "Friday at 16:00" ngay cả khi các turn hội thoại phụ cũ đã bị evict khỏi gần turn gần nhất.

---

## 5. Quy Trình Privacy Drill

Đã thực hiện xóa dữ liệu người dùng `minh-lab17` và xác minh bằng lệnh:
- `python -m src.forget --user-id minh-lab17` -> Xóa Zep user & Redis keys.
- `python -m src.forget --user-id minh-lab17 --verify-only` -> Xác nhận:
  - `Zep user absent: True`
  - `Redis user keys remaining: 0`
