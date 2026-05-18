

# 1 — Find existing solutions (đừng xây lại từ số 0)

Mục tiêu: trước khi quyết Build / Buy / Boost / Partner, nhóm phải biết bài này đã có ai giải ở chỗ khác chưa, và họ giải bằng cách nào. Đây là nửa "giãn ra" của `Double Diamond` vòng 2 — mở hết các lời giải đang tồn tại, chưa chốt cái nào.

Lý do làm bước này: đây là chỗ nhiều nhóm hỏng mà không biết. Hỏng vì nhảy thẳng vào "tự build" cho oai, trong khi 80–90% nhu cầu nội bộ chỉ cần Boost hoặc Buy. Hỏng vì không hỏi "ai làm rồi" nên đi lại từ số 0. Gần như bài nào cũng đã có người giải ở một ngành khác — không thấy thì phí cả pilot.

Quy tắc: **không có nguồn = giả định.** Mỗi cái AI/web nói ra, hỏi lại "lấy ở đâu?". Không chỉ được nguồn thì đánh dấu  (giả định để giảng), đừng xài như fact.

## Bước 0 — Bài này thực ra là dạng bài gì? (2 phút)

Bỏ context AI20k sang một bên. Mô tả Quick Win của nhóm như một bài toán chung — không có chữ "học viên / coach / Discord". Vài ví dụ cho dễ hình dung:

- "câu hỏi của user → câu trả lời kèm nguồn" → đây là bài Q&A có citation
- "một đống văn bản lộn xộn → data có cấu trúc" → bài extraction
- "bài nộp → nhận xét theo rubric" → bài rubric grading

Dạng bài (the pattern) đó gần như chắc chắn đã có người làm ở ngành khác. Tìm ra dạng bài → tìm ra người đã giải nó.

- **Quick Win của nhóm, viết lại thành 1 dạng bài chung (không có chữ domain)**: Trích xuất thông tin có cấu trúc (structured extraction) từ tài liệu hình ảnh đa dạng mẫu mã (unstructured visual document) và thực hiện tính toán số liệu chính xác theo bộ quy tắc toán học cứng (deterministic rules calculation).
- **Input → output thực chất là gì**: Ảnh chụp hoặc tệp PDF chứng từ khấu trừ thuế TNCN $\rightarrow$ Dữ liệu JSON có cấu trúc chứa thông tin thu nhập, thuế đã đóng, thông tin doanh nghiệp chi trả và kết quả tính toán số thuế TNCN được hoàn/nộp thêm kèm citation luật.
- **Ràng buộc không bỏ được (lấy từ `00-context.md`)**: An toàn tuyệt đối dữ liệu cá nhân (CCCD, Số tiền), độ chính xác toán học 100% (không được để AI tự tính nhẩm), ngân sách API cực nhỏ (dưới 100đ/chứng từ), giao diện trực quan và dễ dùng (Adoption).

## Quy trình 8 phút

```text
2 phút  — Bước 0: gọi tên dạng bài
4 phút  — Phần A: deep research 4 tầng "ai giải dạng bài này rồi"
2 phút  — Phần B: rút về 2–3 hướng khả thi, đánh dấu nguồn
```

---

## Phần A — Deep research: ai giải dạng bài này rồi, giải sao?

Chúng tôi thực hiện deep research qua 4 tầng để tìm ra phương án tối ưu:

### Trả lời — điền theo 4 tầng

| Tầng | Hỏi AI/web câu gì | Tìm được gì | Nguồn /  nếu là giả định |
|---|---|---|---|
| **1 · Map** | "Dạng bài structured visual document extraction và deterministic calculation thường giải bằng những hướng nào?" | Có 4 hướng giải chính:<br>1. **Template-based OCR**: Dựng bounding box tọa độ cho từng mẫu chứng từ. Ưu: Rất rẻ, chính xác 100% nếu đúng mẫu. Nhược: Phá sản nếu chụp nghiêng lệch.<br>2. **LLM OCR + JSON Mode**: Dùng Gemini Vision API để quét ảnh và trả về JSON chuẩn. Ưu: Quét cực nhạy mọi góc chụp, xử lý đa biểu mẫu. Nhược: Tốn API token.<br>3. **SaaS OCR Services**: Thuê API ngoài (như FPT AI, AWS Textract). Ưu: Tối ưu tiếng Việt. Nhược: Khó tùy biến biểu mẫu đặc thù của chứng từ thuế TNCN.<br>4. **LLM OCR + Code Rules Engine**: AI chỉ OCR dữ liệu thô sang JSON. Toàn bộ tính toán xử lý bằng code JS cứng. Ưu: Đạt độ chính xác tuyệt đối, tránh ảo giác số học của AI. |  (Theo tài liệu thiết kế hệ thống OCR Kế toán Việt Nam) |
| **2 · Tiền lệ** | "Đội nào đã làm trích xuất biểu mẫu thu nhập ở quy mô tương tự và thành công? Họ làm cách nào?" | **TurboTax (Mỹ)**: Cho phép chụp ảnh biểu mẫu W-2 (chứng từ thu nhập). Quy trình của họ: Dùng AI OCR trích xuất dữ liệu $\rightarrow$ Đổ số liệu vào Form UI cho người dùng tự kiểm tra và chỉnh sửa (Fallback UX/Human-in-the-loop) $\rightarrow$ Đẩy vào Rules Engine nội bộ để tính toán số tiền hoàn thuế. |  [TurboTax Mobile App Workflow](https://turbotax.intuit.com) |
| **3 · Phản chứng** | "Ca nào làm trích xuất và tính toán thuế bằng AI thất bại? Nguyên nhân gốc là gì?" | Các chatbot AI thế hệ đầu (nhập đề bài thuế bắt AI tự tính số thuế phải đóng trong prompt) thất bại do **ảo giác số học (arithmetic hallucination)**. LLM là mô hình xác suất từ ngữ, không sinh ra để tính toán số học phức tạp như công thức lũy tiến từng phần. Việc để AI tự tính toán số thuế dẫn đến sai sót nghiêm trọng và làm mất uy tín sản phẩm ngay lập tức. |  (Khuyến cáo thiết kế AI trong Tài chính - Kế toán 2024) |
| **4 · Thu hẹp** | "Với ràng buộc [budget nhỏ · có người review · cần citation], hướng nào khả thi cho pilot 14 ngày?" | Hướng tối ưu nhất là: **LLM OCR (Gemini 2.5 Pro JSON Mode) + Deterministic JS Rules Engine + Fallback UI Review**. Gemini Vision API chỉ quét ảnh lấy số thô $\rightarrow$ JS Code xử lý tính toán thuế $\rightarrow$ Form UI trực quan hiển thị lại toàn bộ số liệu cho người dùng review chỉnh sửa $\rightarrow$ RAG luật thuế (Nghị định 310/2025/NĐ-CP) tích hợp riêng để tư vấn điều khoản. |  (Phù hợp ngân sách 10 triệu VNĐ, tối ưu hóa độ chính xác và an toàn dữ liệu) |

---

## Phần B — Rút về 2–3 hướng khả thi

### Trả lời

| Hướng giải khả thi | Ai làm rồi (gần bài mình nhất) | Nguồn /  | Hợp ràng buộc `00-context`? |
|---|---|---|---|
| **Hướng 1: LLM OCR (Gemini 2.5 Pro) + Deterministic JS Calculator + Fallback UI Review (Boost)** | TurboTax W-2 Scanner |  [TurboTax](https://turbotax.intuit.com) | **Có**. Tối ưu chi phí API ($1.25/1M tokens input), đảm bảo 100% độ chính xác toán học, cho phép review con số trực quan. |
| **Hướng 2: Thuê SaaS OCR chuyên dụng ngoài (Buy)** | FPT AI Reader |  [FPT.AI](https://fpt.ai) | **Không**. Chi phí mua API tối thiểu cao, khó tùy biến cho các mẫu chứng từ khấu trừ thuế TNCN phi tiêu chuẩn. |
| **Hướng 3: RPA Agent tự động upload và nộp thẳng tờ khai lên eTax (Build)** | UiPath RPA bots |  | **Không**. Quá phức tạp để xây dựng trong 14 ngày, rủi ro bảo mật tài khoản của người dùng rất cao dẫn đến không ai dám dùng (Adoption = 0). |

**"Đi từ 5 lên" — nhóm kế thừa cụ thể cái gì** (1–2 câu):

```text
Chúng tôi kế thừa mô hình "Fallback UI" (cho phép con người review và chỉnh sửa lại dữ liệu OCR) của TurboTax và tận dụng API đa phương thức (Multimodal API) có sẵn của Gemini 2.5 Pro, hoặc sử dụng GPT 4o (tính năng mới nhất) để giải quyết bài toán OCR chứng từ nhanh chóng mà không cần tốn chi phí xây dựng hay huấn luyện lại các mô hình nhận diện ký tự quang học từ số 0.
```

---

## Phát hiện ban đầu

Ghi nhanh 3 cái đáng chú ý nhất:

- **Tầm quan trọng của Fallback UX**: Cho dù AI có độ chính xác 99%, chỉ cần 1 ký số bị lệch (ví dụ 8.000.000 thành 3.000.000) cũng làm sai lệch toàn bộ tờ khai thuế. Do đó, thiết kế một UI cho phép người dùng tự đối soát và sửa lại số liệu ngay bên cạnh ảnh gốc là yếu tố quyết định thành bại của sản phẩm.
- **Che dữ liệu ở client-side (CCCD)**: Nhất thiết phải bôi đen hoặc che mờ số CCCD và địa chỉ ngay trên trình duyệt của người dùng trước khi gửi ảnh lên server để bảo vệ quyền riêng tư và tạo niềm tin tuyệt đối cho người dùng.
- **API Gemini 2.5 Pro**: Với context cực lớn và khả năng xử lý hình ảnh tốt, Gemini 2.5 Pro hoàn toàn có thể trích xuất chính xác cấu trúc bảng biểu của chứng từ khấu trừ thuế với chi phí token rẻ hơn một nửa so với GPT-4o.

## Câu hỏi mở (mang sang bước chốt)

- Làm thế nào để thiết kế một Prompt hệ thống (System Prompt) tối ưu cho Gemini 2.5 Pro để nó trả về định dạng JSON ổn định 100%, không bị lỗi parse dấu câu tiếng Việt?
- Làm thế nào để giải quyết bài toán người dùng tải lên nhiều tệp chứng từ cùng lúc mà hệ thống vẫn đối soát và cộng dồn dữ liệu chính xác không bị trùng lặp?

---

## Tổng kiểm tra trước khi sang `2-FINAL-solution.md`

| Hạng mục | Xong? |
|---|---|
| Gọi được dạng bài trong 1 câu, không còn chữ domain | / |
| Đủ 4 tầng deep research, tầng nào cũng có kết quả | / |
| Mỗi kết quả có nguồn, hoặc đánh dấu  nếu là giả định | / |
| Rút về 2–3 hướng + nói được "đi từ 5 lên" cái gì | / |

Hàng nào chưa xong → quay lại Phần A, đừng sang bước chốt vội.

Sau bước này, mở `2-FINAL-solution.md` — chốt Build/Buy/Boost/Partner + data & ai review + bản vẽ trực quan (đây là bản nộp của phase này).

*Liên quan: handbook §A5 · `prompts/04-find-solutions.md` · `00-context.md`*
