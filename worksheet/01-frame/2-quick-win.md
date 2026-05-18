---
artifact: 3 — Quick Win Selection
bai-tap: Frame — chọn lát cắt làm trước
phase: Double Diamond vòng 1 · ◆ siết (hội tụ về 1 lựa chọn)
time: ~10 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 1-intake-breakdown.md · prompts/02-quick-win-challenge.md
nop-cuoi: Không — file trung gian (bản chốt phase này ở 3-FINAL-problem-framing.md)
---

# 2 — Quick Win: chọn lát cắt làm trước

Mục tiêu: từ 5–8 use case ở file `1`, chấm điểm nhanh và chốt **1 Quick Win** để pilot đầu tiên — kèm lý do chọn và lý do *không* chọn các phần khác. Đây là nửa "siết lại" của [Double Diamond](https://www.thefountaininstitute.com/blog/what-is-the-double-diamond-design-process) vòng 1.

Lý do làm bước này: đây là quyết định quan trọng nhất của phase Frame. Quick Win **không phải** phần dễ nhất hay nghe hay nhất — là phần *chứng minh được giá trị nhanh và có người ủng hộ*. Chọn sai → pilot fail → mất uy tín → khó xin pilot tiếp. Nhóm phải chọn được *và bảo vệ được bằng lý do*, không bằng cảm tính.

Quy tắc: **điểm số chỉ là gợi ý, không phải đáp án.** Đừng để con số quyết thay nhóm — nó chỉ giúp so sánh.

## Bước 0 — Lấy 4–6 use case mạnh nhất từ file `1` (1 phút)

## Quy trình 10 phút

```text
1 phút  — Bước 0: chọn 4–6 ứng viên
5 phút  — Phần A: chấm điểm 4 trục
3 phút  — Phần B: 1 lý do nên / 1 lý do không cho top 2
1 phút  — Phần C: chốt + ai ủng hộ + cái KHÔNG chọn
```

---

## Phần A — Chấm điểm 4 trục (1–5 mỗi trục)

Câu hỏi phụ (tự trả lời):

- "Risk" ở đây là *sai thì mất gì* — chọn đúng việc chính của user (task centrality) thì sai cũng đỡ đau; chọn việc lớn nhất thì sai rất đắt. Use case nào risk thấp thật?
- Use case nào có sẵn data + có người trong AI20k thật sự muốn dùng?

| Use case | Impact | Feasibility | Evidence nhanh | Risk (cao = an toàn) | Tổng |
|---|:--:|:--:|:--:|:--:|:--:|
| **UC 1: AI OCR trích xuất chứng từ khấu trừ thuế (Mẫu 03/TNCN) + Calculator** | 5 | 4 | 4 | 4 (Sai có thể sửa trên UI) | **17** |
| **UC 2: AI RAG tư vấn giảm trừ gia cảnh & tra cứu luật** | 4 | 5 | 5 | 3 (Ảo giác pháp lý) | **17** |
| **UC 5: AI sinh file XML tờ khai 02/QTT-TNCN** | 5 | 2 | 2 | 2 (Lỗi XML hệ thống eTax từ chối) | **11** |
| **UC 6: AI rà soát lỗi logic tờ khai trước khi nộp** | 3 | 3 | 3 | 4 (Chỉ cảnh báo lỗi) | **13** |

(Thang điểm chi tiết: `templates/quick-win-scoring.md`.)

## Phần B — 1 lý do nên / 1 lý do không, cho top 2

**Ứng viên A — AI OCR trích xuất chứng từ khấu trừ thuế + Calculator tính số thuế được hoàn/phải nộp**

```text
Nên chọn vì: 
- Giải quyết trực diện "nỗi đau đầu tiên" của người dùng: lười gõ tay hàng chục con số từ nhiều chứng từ và không biết mình được hoàn thuế bao nhiêu.
- Giá trị tài chính nhìn thấy ngay (Financial Impact) chỉ sau 1 phút tải chứng từ lên, tạo động lực cực lớn để người dùng tiếp tục sử dụng.
- Khả năng OCR ảnh cực mạnh của Gemini 2 Pro/GPT-4o cho phép xây dựng prototype cực nhanh.

Không nên vì:
- Phụ thuộc chất lượng ảnh chụp chứng từ của người dùng. Nếu ảnh mờ/lóa, OCR có thể sai lệch số liệu, cần thiết kế giao diện UI đối soát thông minh (Fallback UX) để người dùng tự điều chỉnh lại.
```

**Ứng viên B — AI RAG tư vấn giảm trừ gia cảnh & tra cứu luật**

```text
Nên chọn vì:
- Cực kỳ dễ phát triển (Feasibility tối đa). Chỉ cần đưa tệp PDF thông tư, luật thuế TNCN mới (Nghị định 310/2025/NĐ-CP) vào Vector Database và kết nối chatbot.
- Người dùng có thể đặt các câu hỏi tự do để giải quyết thắc mắc về hồ sơ phụ thuộc.

Không nên vì:
- Giá trị hành động thấp: người dùng trò chuyện xong vẫn phải tự tính toán số tiền và tự vào eTax điền tờ khai.
- Rủi ro ảo giác tư vấn pháp lý nếu mô hình tự suy luận ngoài phạm vi Vector DB, dễ dẫn tới việc người dùng hiểu sai luật và bị phạt.
```

## ⚑ Phần C — Chốt Quick Win

- **Quick Win nhóm chọn**: **AI OCR trích xuất chứng từ khấu trừ thuế (Mẫu 03/TNCN) + Tự động tính toán số thuế TNCN được hoàn/phải nộp.**
- **Vì sao chọn cái này trước**: Đây là tính năng mang lại Impact vượt trội và có Evidence nhanh rõ rệt nhất. Nó giúp freelancer từ việc mất 4–8 tiếng mày mò đọc chứng từ và tính toán thủ công rút ngắn xuống còn dưới 1 phút chụp ảnh chứng từ để biết chính xác số tiền được hoàn. Việc chọn tính năng này giúp nhóm kiểm chứng được khả năng OCR đa cấu trúc chứng từ của mô hình AI và phản ứng của người dùng về tính an toàn dữ liệu nhạy cảm trước khi đầu tư sâu vào các mô hình phức tạp hơn.
- **Ai trong AI20k sẽ ủng hộ pilot này**: Nhóm **50-100 Freelancers công nghệ, Lập trình viên tự do và Creators trong cộng đồng AI Thực Chiến**. Họ có thu nhập từ nhiều nguồn, đang lo lắng trước mùa quyết toán thuế nhưng cực kỳ bận rộn. Một công cụ giúp họ kiểm tra nhanh số tiền được hoàn mà không tốn 700.000 VNĐ thuê dịch vụ ngoài (như IFA) sẽ thu hút họ sẵn sàng tham gia thử nghiệm và cung cấp các chứng từ đã ẩn thông tin nhạy cảm.
- **Nhóm KHÔNG chọn gì + vì sao**:
  1. **AI sinh file XML tờ khai 02/QTT-TNCN**: Loại bỏ vì Feasibility quá thấp cho giai đoạn pilot 14 ngày. Định dạng XML schema của Tổng cục Thuế thay đổi liên tục, chỉ cần sai một thẻ tag, hệ thống eTax sẽ từ chối upload, gây ức chế cho người dùng.
  2. **AI Step-by-step eTax UI Companion**: Loại bỏ vì đây chỉ là tính năng bổ trợ giao diện nộp, không giải quyết nỗi đau cốt lõi là xử lý số liệu chứng từ và tính toán tối ưu thuế - rào cản lớn nhất khiến người nộp thuế bỏ cuộc.

---

## Phát hiện ban đầu

- **OCR số thực tế**: Các chữ số trên chứng từ khấu trừ thuế rất dễ bị mô hình AI đọc sai nếu nằm sát các vạch kẻ bảng biểu của chứng từ. Nhóm cần thiết lập giải thuật cắt ảnh vùng số liệu (Image cropping) hoặc dùng GPT-4o Vision API để hỗ trợ Gemini khi độ tin cậy thấp.
- **Người dùng yêu cầu bảo mật tuyệt đối**: Người dùng yêu cầu phải thấy nút "Che thông tin cá nhân" (Blur/Mask CCCD) trực quan ngay trên màn hình trước khi nhấn nút "Tải lên phân tích".

## Câu hỏi mở (mang sang Problem Framing)

- Làm thế nào để thiết kế một cơ chế "Fallback UX" - cho phép người dùng dễ dàng chỉnh sửa lại các con số AI quét sai trực tiếp trên giao diện trực quan trước khi đưa vào công thức tính thuế?
- Phương án kỹ thuật nào tối ưu nhất để bôi đen (masking) thông tin CCCD trực tiếp ở phía Client-side bằng Javascript trước khi tải ảnh lên API?


---

## Tổng kiểm tra trước khi sang `3-FINAL-problem-framing.md`

| Hạng mục | Xong? |
|---|---|
| Có bảng chấm 4 trục cho ≥4 use case | / |
| Chốt 1 Quick Win, lý do bám số/impact (không "nghe hay") | / |
| Nêu rõ ai ủng hộ pilot này | / |
| Ghi rõ ≥2 phần KHÔNG chọn + lý do | / |

⚑ Đây là phần coach kiểm tra ở Mốc 1: *"Vì sao không làm full tool? Vì sao chọn lát cắt này trước?"*

Sau bước này, mở `3-FINAL-problem-framing.md` — đóng khung vấn đề thật (bản nộp của phase Frame).

*Liên quan: handbook §A3 · `templates/quick-win-scoring.md` · `prompts/02-quick-win-challenge.md`*
