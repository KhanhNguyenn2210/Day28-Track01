---
artifact: 8 — 5-slide Pitch + AI Support Log (bản nộp cuối lab)
bai-tap: Pilot Plan — dồn thành pitch, sẵn sàng phản biện
phase: Double Diamond vòng 2 ·  output (bản nộp cuối + present)
time: ~5 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 1-pilot-plan.md + toàn bộ 01-frame + 02-solution · templates/5-slide-pitch.md
nop-cuoi: Có — bản nộp cuối lab (Part E · 5-slide Pitch + AI Support Log)
---

# 2 — FINAL: 5-slide Pitch + AI Support Log

Mục tiêu: dồn cả A3 Working Canvas thành 5 slide pitch (5 phút), chuẩn bị trả lời 3 câu phản biện, và ghi AI Support Log. Đây là bản nộp cuối cùng của lab.

Lý do làm bước này: nguyên tắc *demo đơn giản + lập luận chặt > demo đẹp + lập luận yếu*. Slide đẹp mà không trả lời được "số này lấy ở đâu" thì hỏng. Pitch không phải kể chuyện — là đưa evidence để stakeholder ra được một quyết định.

Quy tắc: **slide cuối phải là một lời xin rõ ràng** (xin gì · đổi lại hứa gì). Không có lời xin = stakeholder không biết approve cái gì.

## Quy trình 5 phút

```text
3 phút  — Dồn 5 slide (mỗi slide 1 thông điệp)
1 phút  — Chuẩn bị 3 câu phản biện
1 phút  — AI Support Log
```

---

## Phần A — 5 slide (mỗi slide 1 thông điệp)

Kéo nguyên liệu từ các file đã làm, đừng viết mới. Khung đầy đủ: `templates/5-slide-pitch.md`.

| # | Slide | Lấy từ | Nội dung 1–2 gạch đầu dòng | Ai nói |
|---|---|---|---|---|
| 1 | **Problem & User** | 01-frame/3-FINAL | - **Nỗi đau & Thiệt hại**: Freelancer/Cá nhân có thu nhập đa nguồn tốn **4-8 tiếng** mò mẫm tự khai thuế TNCN dễ sai sót, đối mặt mức phạt tăng nặng **1.000.000đ - 12.500.000đ** của Nghị định 310/2025/NĐ-CP hoặc phải chi tối thiểu **700.000 VNĐ** thuê kế toán ngoài (IFA) và chờ **6 ngày**.<br>- **User**: 50-100 Freelancers công nghệ, Lập trình viên tự do và Creators trong cộng đồng AI Thực Chiến. | **Nguyễn Bá Khánh** (PM) |
| 2 | **Breakdown & Quick Win** | 01-frame/1,2 | - **Breakdown**: Chia nhỏ nền tảng thành 7 use cases từ OCR chứng từ, RAG luật, tính toán thuế đến sinh file XML eTax.<br>- **Quick Win**: Chọn **AI OCR trích xuất chứng từ khấu trừ thuế (Mẫu 03/TNCN) + Tự động tính toán số thuế TNCN được hoàn/phải nộp**. Giải quyết ngay nút thắt nhập liệu đầu tiên, tạo giá trị tài chính thực tế và rủi ro thấp nhất. | **Nguyễn Bá Khánh** (PM) |
| 3 | **Solution & Visual Flow** | 02-solution/2-FINAL | - **Mô hình Boost**: Dùng Gemini 2.5 Pro Multimodal OCR ($1.25/1M tokens) trích xuất dữ liệu thô sang JSON + code JS Rules Engine cứng tính thuế chính xác 100% (tránh LLM ảo giác tính toán).<br>- **Safeguards**: Màn hình đối soát song song (Side-by-side Fallback UI) giúp người dùng làm Human-in-the-loop review số liệu; Canvas JS che CCCD tại trình duyệt. | **Lưu Thị Ngọc Quỳnh** (Designer) |
| 4 | **AI Pilot Plan** | 03-pilot-plan/1 | - **Kế hoạch 14 ngày (2 Phase)**: Phase 1 (Alpha test 50 dữ liệu mẫu giả định để calibrate); Phase 2 (Chạy pilot thực tế trên 100 freelancers thật).<br>- **Ngân sách 10.000.000đ**: Phân bổ API (3.5M), Server & hosting (2M), Marketing/User acquisition (1.5M), Tư vấn kế toán kiểm chuẩn (1M), Quỹ dự phòng (2M). | **Nguyễn Phương Nam** (Developer) |
| 5 | **Metric & LỜI XIN** | 03-pilot-plan/1 | - **Lời hứa**: Giảm thời gian hoàn thành xuống **dưới 15 phút** (Giảm 95%), tăng tỷ lệ nộp hồ sơ eTax thành công ngay lần đầu lên **trên 95%**.<br>- **LỜI XIN**: Xin phê duyệt **phân bổ 10.000.000 VNĐ** ngân sách pilot và **14 ngày thử nghiệm** trên **100 người dùng thật** để chứng minh giá trị và phản ứng người dùng. | **Nguyễn Phương Nam** (Developer) |

## Phần B — Chuẩn bị 3 câu phản biện

Business owner/instructor sẽ hỏi mỗi nhóm 1–2 câu. Viết sẵn câu trả lời:

1. *"Số liệu / giả định này lấy ở đâu?"* 
$\rightarrow$ Lấy trực tiếp từ các văn bản pháp luật chính thống của Việt Nam: **Mức phạt theo Nghị định 310/2025/NĐ-CP** (sửa đổi Nghị định 125/2020/NĐ-CP) và **Danh sách 4.947 người nợ thuế tính đến 31/3/2026** (Cục Thuế TP.HCM công bố) đăng tải trên Thư Viện Pháp Luật. Báo giá dịch vụ kế toán đối chiếu lấy từ biểu phí dịch vụ của **Công ty kiểm toán tư vấn IFA (chỉ từ 700.000 VNĐ/hồ sơ, hoàn thành trong 6 ngày)**.

2. *"Nếu giả định quan trọng nhất của bạn sai thì sao?"* 
$\rightarrow$ Giả định quan trọng nhất là: *"Gemini OCR có thể nhận dạng đúng các con số trên chứng từ khấu trừ thuế TNCN của các doanh nghiệp khác nhau"*. Nếu giả định này sai (AI OCR đọc lệch số do ảnh chụp kém hoặc font chữ lỗi), chúng tôi đã thiết lập **Màn hình đối soát song song (Side-by-side Fallback UI)** bắt buộc. Người dùng làm chốt chặn cuối cùng (Human review 100%), tự chỉnh sửa con số sai lệch trên Form UI trước khi đưa vào code tính toán, bảo đảm số liệu xuất ra luôn chính xác 100%.

3. *"Tình huống nào sẽ khiến bạn dừng pilot?"* 
$\rightarrow$ Chúng tôi thiết lập tiêu chí dừng (Exit Criteria) cực kỳ rõ ràng ở hai mức:
- **Cảnh báo (Warning)**: Chi phí API vượt **300.000đ/ngày** hoặc tỷ lệ OCR chính xác dưới **80%** trong 2 ngày liên tục $\rightarrow$ Hành động: Tạm dừng để tối ưu lại prompt và tham số mô hình.
- **Nghiêm trọng (Critical)**: Phát hiện bất kỳ sự cố rò rỉ thông tin CCCD nào, hoặc xảy ra bất kỳ lỗi sai lệch số thuế nào do AI ảo giác toán học (AI tính sai số thuế so với JS Rules Engine) $\rightarrow$ **Hành động: Dừng ngay lập tức pilot**, ngắt kết nối database, đóng server để bảo vệ uy tín và an toàn thông tin của người dùng.

## Phần C — AI Support Log

| Câu hỏi | Trả lời |
|---|---|
| AI giúp được gì trong lab này? | AI hỗ trợ phân tích cấu trúc Big Ask thành 7 use cases nghiệp vụ sắc bén; hỗ trợ chấm điểm Quick Win theo đúng phương pháp Double Diamond; và giúp viết code định dạng Mermaid và các bản vẽ ASCII Mockup trực quan cho giao diện Fallback UI. |
| AI đưa output nào nghe hợp lý nhưng nhóm phải sửa? | Ban đầu AI đề xuất tự động tính toán số thuế trực tiếp trong prompt của Gemini/GPT-4o. Nhóm phát hiện ra rủi ro ảo giác số học (arithmetic hallucination) của LLMs rất cao, nên đã sửa lại: Tách biệt hoàn toàn, chỉ dùng AI để OCR trích xuất chữ và số thô, còn việc tính toán số thuế do Code Javascript Rules Engine thuần túy xử lý để đảm bảo chính xác tuyệt đối. |
| Phần nào nhóm tự lập luận, KHÔNG copy AI? | Nhóm tự lập luận phần **Adoption Plan** và lựa chọn **Mô hình Boost** tối ưu chi phí (Gemini 2.5 Pro primary + GPT-4o backup) dựa trên điều kiện tài chính thực tế và mối quan hệ trực tiếp với 100 Freelancers trong cộng đồng AI Thực Chiến để bảo đảm chạy thử thành công. |

---

## Tổng kiểm tra trước khi nộp

| Hạng mục | Xong? |
|---|---|
| 5 slide, mỗi slide 1 thông điệp, đã phân ai nói slide nào | / |
| Slide 5 có lời xin rõ ràng (xin gì · hứa gì) | / |
| Có câu trả lời sẵn cho cả 3 câu phản biện | / |
| AI Support Log điền đủ 3 dòng | / |
| Tất cả file worksheet/ đã commit + push, link dán vào Discord | / |

Đây là file cuối. Pitch 5 phút + nhận phản biện theo bảng 5 Gate (`templates/rubric-gate-sheet.md`).

*Liên quan: handbook §A9 · `templates/5-slide-pitch.md` · `templates/ai-support-log.md`*
