
# 1 — AI Pilot Plan core

Mục tiêu: viết phần kế hoạch xin pilot — scope, người, data, budget, timeline, metric, exit criteria, adoption, lời hứa, lời xin. Bước này giãn ra (liệt kê hết những thứ cần) rồi siết lại (chốt bản gọn đủ để stakeholder quyết).

Lý do làm bước này: đây là thứ stakeholder dùng để **quyết approve hay dừng**. AI Pilot Plan **không phải proposal xin tiền** — là *cam kết hai chiều*: nhóm xin nguồn lực, đổi lại hứa giao evidence + chấp nhận dừng nếu metric fail. Demo đẹp mà không nói được "xin gì, hứa gì, đo gì, dừng khi nào" → trượt Gate 5.

Quy tắc: **budget tách từng hạng mục, không gộp 1 cục; không có mục "miscellaneous".** Exit criteria phải có người có quyền thực thi, không chỉ trên giấy.

## Quy trình 10 phút

```text
6 phút  — Điền 10 mục core (kéo nguyên liệu từ 00 + 01-frame + 02-solution)
3 phút  — Phần exit criteria + adoption (chỗ nhóm hay bỏ quên)
1 phút  — Tự phản biện
```

---

## 10 mục core

Câu hỏi phụ (tự trả lời):

- Nếu tóm vấn đề không gọn trong 1 câu → nhóm chưa hiểu vấn đề.
- Exit criteria của nhóm có ai DÁM thực thi khi sếp vẫn thích pilot không?
- Adoption: ai dùng đầu tiên — không phải "cả khóa ~500 người"?

#### Trả lời

1. **Tóm vấn đề** (1 câu, từ Problem Framing): 
Cá nhân và freelancers tự quyết toán thuế TNCN đang tốn từ 4 đến 8 tiếng mò mẫm thủ công trên eTax với tỷ lệ tờ khai hợp lệ ngay lần đầu chỉ đạt 15% - 20%, hoặc phải mất tối thiểu 700.000 VNĐ cho đại lý dịch vụ ngoài (IFA) và chờ đợi tới 5 ngày vì e ngại các mức phạt nộp chậm tăng nặng lên tới 12.500.000 VNĐ của Nghị định 310/2025/NĐ-CP.

2. **Cách làm + lý do** (từ 02-solution, 1 câu): 
Sử dụng mô hình **Boost** - dùng Gemini 2.5 Pro Vision API để OCR chứng từ thuế thô sang JSON, chạy qua code Javascript Rules Engine cứng để bảo đảm tính toán chính xác 100%, kết hợp giao diện đối soát song song (Side-by-side Fallback UI) để người dùng làm Human-in-the-loop review số liệu trước khi xuất kết quả.

3. **Scope pilot**: phục vụ ai · bao nhiêu người · bao lâu · mấy phase: 
Phục vụ nhóm **50-100 Freelancers và lập trình viên tự do** có từ 2 nguồn thu nhập trở lên trong cộng đồng AI Thực Chiến; thời gian chạy thử nghiệm trong **14 ngày (2 tuần)**; gồm 2 phase: Phase 1 (Tuần 1 - Alpha test 50 bộ dữ liệu mẫu) và Phase 2 (Tuần 2 - Pilot diện rộng cho 100 người dùng thật).

4. **Người**: nhóm làm · ai review output rủi ro cao · ai có quyền quyết approve/dừng: 
- **Nhóm thực hiện**: Nguyễn Bá Khánh (PM), Lưu Thị Ngọc Quỳnh (Designer), Nguyễn Phương Nam (Developer).
- **Người review output rủi ro cao**: Người nộp thuế (User) trực tiếp rà soát và chỉnh sửa số liệu trên Form đối soát trước khi tính toán.
- **Cố vấn chuyên nghiệp**: 01 Kế toán trưởng rà soát bộ công thức tính thuế lũy tiến và RAG luật.
- **Người có quyền quyết approve/dừng**: Nguyễn Bá Khánh (PM - dự án trưởng).

5. **Data**: dùng data gì (mẫu/giả định) · cơ chế privacy/citation: 
- Dùng **50 bộ chứng từ khấu trừ thuế TNCN giả định** (đã ẩn thông tin cá nhân và thay thế bằng các số liệu kiểm thử ngẫu nhiên) để huấn luyện hệ thống.
- **Cơ chế Privacy**: Dùng Canvas JS masking tự động bôi đen CCCD và Địa chỉ tại trình duyệt của người dùng trước khi gửi lên API; sử dụng Enterprise API có cam kết không lưu dữ liệu (Zero Data Retention) trên server của hãng.
- **Cơ chế Citation**: Trích xuất chính xác Điều, Khoản của Nghị định 310/2025/NĐ-CP trong chatbot tư vấn giảm trừ gia cảnh.

6. **Budget** (tách hạng mục): 
- **API Token (Gemini 2.5 Pro + GPT-4o Fallback OCR)**: 3.500.000 VNĐ.
- **Server & Hosting (Vercel Pro + Supabase Database)**: 2.000.000 VNĐ.
- **Marketing & User Acquisition (Facebook targeted ads)**: 1.500.000 VNĐ.
- **Chi phí Thuê cố vấn kế toán kiểm chuẩn (Calibrate cost)**: 1.000.000 VNĐ.
- **Quỹ dự phòng rủi ro khẩn cấp**: 2.000.000 VNĐ.
- *Tổng ngân sách: 10.000.000 VNĐ (Tuyệt đối không có chi phí ẩn).*

7. **Timeline + cổng giữa phase**: 
- **Phase 1: Phát triển & Alpha Test (Ngày 1 - 7)**: Hoàn thiện Backend, OCR parser, Rules Engine và Fallback UI. Chạy test trên 50 bộ dữ liệu giả định $\rightarrow$ *Cổng 1 (Hết ngày 7)*: Độ chính xác OCR > 85%, 100% công thức tính toán thuế chính xác, hệ thống RAG trích dẫn luật không bị lỗi ảo giác.
- **Phase 2: Chạy Pilot Thực Tế & Đóng Gói (Ngày 8 - 14)**: Phát hành bản Beta cho 100 Freelancers sử dụng thật, thu nhận feedback qua Google Form $\rightarrow$ *Cổng 2 (Hết ngày 14)*: Đạt tỷ lệ người dùng tự nộp tờ khai thành công eTax ngay lần đầu > 95%, thời gian hoàn thành dưới 15 phút.

8. **Metrics** (SMART + baseline + ngưỡng + ai đo):

| Metric | Đo bằng gì · ai đo | Baseline | Ngưỡng đạt |
|---|---|---|---|
| **Thời gian hoàn thành quy trình** | Log thời gian tự động từ lúc upload đến lúc xuất kết quả (Hệ thống tự đo) | 4 - 8 tiếng (Tự làm thủ công) | **Dưới 15 phút** |
| **Tỷ lệ tờ khai hợp lệ ngay lần đầu (Task Success Rate)** | Khảo sát Google Form tỷ lệ cơ quan thuế chấp nhận tờ khai XML (Nhóm PM đo) | 15% - 20% (Tự mò eTax) | **Trên 95%** |
| **Độ chính xác OCR số liệu** | Log so khớp tỷ lệ số liệu AI trích xuất khớp với số liệu người dùng xác nhận cuối cùng (Hệ thống tự đo) | N/A | **Trên 85%** |

   Leading indicator (biết kết quả sớm trong 1–2 tuần): Tỷ lệ người dùng hoàn thành bước Human Review (Xác nhận số liệu đúng trên Form UI) đạt trên 90% trong 3 ngày đầu chạy pilot.

9. **Exit criteria** (định trước, ≥2 mức):

| Mức | Điều kiện | Hành động | Ai có quyền dừng |
|---|---|---|---|
| **Cảnh báo** | - Chi phí API vượt quá 300.000 VNĐ/ngày.<br>- Tỷ lệ OCR chính xác dưới 80% trong 2 ngày liên tục. | Tối ưu hóa prompt, nén ảnh client-side trước khi tải lên, điều chỉnh temperature của Gemini. | Nguyễn Phương Nam (Developer) |
| **Nghiêm trọng** | - Phát hiện bất kỳ lỗi rò rỉ dữ liệu nhạy cảm hoặc CCCD của người dùng.<br>- Lỗi ảo giác toán học (AI tính sai số thuế so với JS Rules Engine cứng).<br>- Chi phí API vượt quá ngân sách dự phòng. | **Dừng ngay lập tức pilot**, ngắt kết nối database, đóng server và gửi email xin lỗi người dùng. | Nguyễn Bá Khánh (PM - Trưởng dự án) |

   *Exit criteria này hoàn toàn ngăn chặn được 2 Red Flag cốt lõi: Rủi ro sai số liệu tài chính gây phạt tiền (chặn bằng JS Rules Engine và Human review bắt buộc) và Rủi ro bảo mật dữ liệu nhạy cảm (chặn bằng Client-side masking và tắt lưu trữ đĩa cứng).*

10. **Adoption** (tool không ai dùng = $0): ai dùng đầu tiên · workflow đổi ở đâu · ai train/support · nếu không ai dùng thì sao: 
- **Người dùng đầu tiên**: 50-100 Freelancers, Lập trình viên tự do trong cộng đồng AI Thực Chiến có từ 2 nguồn thu nhập trở lên, bận rộn và lo lắng trước kỳ quyết toán thuế TNCN.
- **Workflow đổi**: Chuyển từ quy trình phức tạp: "Mò mẫm chứng từ $\rightarrow$ Tra cứu luật $\rightarrow$ Khai tay trên eTax dễ sai sót $\rightarrow$ Phạt tiền hoặc tốn 700.000đ dịch vụ" sang quy trình tinh gọn: "Tải ảnh lên $\rightarrow$ AI tự động điền Form $\rightarrow$ Người dùng kiểm tra trực quan và bấm nút $\rightarrow$ Nhận ngay kết quả số thuế hoàn chính xác trong 15 phút".
- **Hỗ trợ**: Nhóm cung cấp 01 video hướng dẫn nộp hồ sơ dài 2 phút và hỗ trợ giải đáp thắc mắc 24/7 qua nhóm Discord/Zalo của dự án.
- **Kế hoạch dự phòng**: Nếu tỷ lệ đăng ký thấp, nhóm sẽ phát hành ebook miễn phí *"Cẩm nang tối ưu hóa hoàn thuế TNCN cho Freelancer 2026"* kèm link giới thiệu công cụ AI để thu hút người dùng.


---

## Tự phản biện

- Budget thiếu hạng mục ẩn nào không?
- Exit criteria đủ mạnh để THẬT SỰ dừng, hay chỉ trên giấy?
- Giả định quan trọng nhất sai → plan gì?

---

## Tổng kiểm tra trước khi sang `2-FINAL-pitch.md`

| Hạng mục | Xong? |
|---|---|
| Tóm vấn đề trong 1 câu | / |
| Budget tách hạng mục, không "miscellaneous" | / |
| Metric có baseline + ngưỡng + ai đo | / |
| Exit criteria có người có quyền thực thi (≥2 mức) | / |
| Adoption: chỉ rõ ai dùng đầu tiên (không "cả khóa") | / |

 Coach kiểm tra ở Mốc 4: *"Xin gì? Hứa gì? Đo gì? Dừng khi nào?"*

Sau bước này, mở `2-FINAL-pitch.md` — dồn tất cả thành 5-slide pitch + AI Support Log.

*Liên quan: handbook §A7+§A8 · `templates/ai-pilot-plan-core.md` · `prompts/06-pilot-plan-challenge.md`*
