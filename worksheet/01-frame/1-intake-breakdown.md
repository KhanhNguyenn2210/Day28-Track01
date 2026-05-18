---
artifact: 1 — Track & Big Ask + 2 — Tool Breakdown
bai-tap: Frame — nghe đúng đề rồi tách nhỏ
phase: Double Diamond vòng 1 · ◇ giãn (nghe rộng, chưa chốt)
time: ~12 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 00-context.md · track card · prompts/01-breakdown.md
nop-cuoi: Không — file trung gian (bản chốt phase này ở 3-FINAL-problem-framing.md)
---

# 1 — Intake & Breakdown: nghe đúng đề, tách nhỏ

Mục tiêu: cả nhóm hiểu giống nhau "công cụ lớn stakeholder muốn", rồi tách nó thành 5–8 use case nhỏ làm được riêng. Đây là nửa "giãn ra" của [Double Diamond](https://www.thefountaininstitute.com/blog/what-is-the-double-diamond-design-process) vòng 1 — nghe rộng, tách rộng, chưa chọn.

Lý do làm bước này: hai cái bẫy chết người ở đây. Một, nhận đề literal ("làm con chatbot") rồi nhảy vào build — trong khi yêu cầu mơ hồ thường chỉ là triệu chứng. Hai, ôm cả công cụ lớn đi pitch "build cả platform" → trượt Gate 1 ngay. Tách nhỏ là động tác bắt buộc để từ "một ý tưởng to" sang "danh sách phần làm được".

Quy tắc: **nghe trước, tách trước, chưa chọn.** Bước này không được chốt Quick Win (việc đó ở file `2`).

## Bước 0 — Đọc track card + 00-context (2 phút)

Đọc track card được giao và `00-context.md` (mục 2 đã điền). Đừng lướt.

## Quy trình 12 phút

```text
2 phút  — Bước 0: đọc track card + context
4 phút  — Phần A: phát biểu lại Big Ask bằng lời nhóm
6 phút  — Phần B: tách 5–8 use case + check độc lập
```

---

## Phần A — Phát biểu lại Big Ask bằng lời nhóm

Cả nhóm thống nhất phát biểu lại yêu cầu cốt lõi của công cụ hỗ trợ quyết toán thuế TNCN bằng AI:

### Trả lời

- **Big Ask, viết lại bằng lời nhóm (2–3 câu)**: Xây dựng một ứng dụng AI hỗ trợ tự động hóa toàn bộ quy trình quyết toán thuế TNCN từ khâu OCR/trích xuất chứng từ khấu trừ thuế đến đối soát điều luật và xuất file XML tờ khai quyết toán chuẩn định dạng Tổng cục Thuế để upload lên eTax trong 15 phút, giúp cá nhân và freelancer tự tin tự làm tờ khai, tối ưu hóa tiền hoàn thuế và tiết kiệm tối thiểu 700.000 VNĐ chi phí thuê kế toán ngoài.
- **Tại sao bây giờ**:
  1. **Siết chặt quản lý hành chính**: Theo Luật Quản lý thuế mới, cơ quan thuế bắt đầu công khai danh tính cá nhân chây ỳ nợ thuế (điển hình là danh sách 4.947 người nợ thuế công bố đầu năm 2026).
  2. **Chế tài xử phạt tăng nặng**: Theo Nghị định 310/2025/NĐ-CP sửa đổi mới nhất, mức phạt chậm nộp hồ sơ quyết toán thuế TNCN đã tăng vọt lên tới 12.500.000 VNĐ cho hành vi chậm nộp trên 90 ngày.
  3. **Rào cản quy trình**: Giao diện và thuật ngữ trên trang eTax cực kỳ phức tạp và dễ nhầm lẫn. Phí dịch vụ quyết toán hộ của các đại lý thuế (như IFA) dao động từ 700.000đ - 1.500.000đ và mất tới 6 ngày chờ đợi, quá đắt đỏ so với thu nhập của phần lớn freelancer.
- **Người dùng đầu tiên cụ thể**: Các **Freelancers công nghệ, Creators, Lập trình viên tự do** có từ 2 nguồn thu nhập chịu thuế trở lên tại Việt Nam. Đây là nhóm có kiến thức công nghệ cơ bản, dễ tiếp cận công cụ số nhưng lại có cơ cấu thu nhập phức tạp, dễ bị phạt chậm nộp nhất.

## Phần B — Tách công cụ lớn thành 5–8 use case

Chúng tôi chia nhỏ nền tảng quyết toán thuế TNCN thành 7 Use Cases độc lập để đánh giá và lựa chọn Quick Win:

| # | Use case (AI làm gì · cho ai · để họ làm được gì) | Người dùng | Làm được độc lập? |
|---|---|---|---|
| 1 | **AI OCR trích xuất chứng từ khấu trừ thuế**: AI tự động nhận diện và trích xuất các trường dữ liệu số tiền thuế đã khấu trừ, thu nhập chịu thuế từ ảnh chụp/file PDF chứng từ khấu trừ thuế TNCN của các đơn vị chi trả để người dùng không phải nhập tay số liệu. | Freelancer / Người nộp thuế TNCN | **Có** (Có thể chạy độc lập như công cụ nhập liệu đầu vào bằng hình ảnh). |
| 2 | **AI RAG tra cứu luật và tư vấn mức giảm trừ gia cảnh**: AI tự động đối chiếu các quy định pháp luật về người phụ thuộc, hạn mức giảm trừ gia cảnh của Nghị định 310/2025/NĐ-CP để giải đáp thắc mắc và gợi ý phương án tối ưu số thuế được hoàn cho người dùng. | Freelancer / Người nộp thuế TNCN | **Có** (Có thể chạy độc lập dưới dạng chatbot tư vấn chính sách thuế). |
| 3 | **AI đối soát MST & Xác thực chứng từ**: AI tự động kiểm tra mã số thuế của đơn vị chi trả trên chứng từ với cơ sở dữ liệu doanh nghiệp để cảnh báo người dùng các chứng từ có thông tin sai lệch hoặc không tồn tại. | Freelancer / Người nộp thuế TNCN | **Có** (Chỉ cần API kết nối dữ liệu đăng ký kinh doanh/MST của Tổng cục Thuế). |
| 4 | **Tính toán số thuế phải nộp hoặc được hoàn (Calculator)**: Hệ thống sử dụng công thức lũy tiến từng phần đã lập trình cứng để tính toán số tiền thuế được hoàn hoặc phải nộp thêm dựa trên số liệu đầu vào nhằm giúp người nộp thuế biết chính xác nghĩa vụ tài chính. | Freelancer / Người nộp thuế TNCN | **Không** (Cần dữ liệu số liệu đầu vào từ Use case 1). |
| 5 | **AI sinh file XML tờ khai 02/QTT-TNCN**: AI tổng hợp toàn bộ thông tin thu nhập, thuế đã khấu trừ và giảm trừ gia cảnh đã được xác minh để kết xuất ra tệp XML chuẩn định dạng của Tổng cục Thuế để người dùng chỉ cần upload trực tiếp lên eTax. | Freelancer / Người nộp thuế TNCN | **Không** (Phụ thuộc hoàn toàn vào dữ liệu đầu ra của Use case 1, 2 và 4). |
| 6 | **AI rà soát lỗi logic tờ khai trước khi nộp**: AI chạy bộ quy tắc logic nghiệp vụ thuế trên tệp XML người dùng tải lên để đưa ra cảnh báo lỗi sai lệch dòng tiền, sai cơ quan thuế thụ lý trước khi người dùng gửi hồ sơ lên eTax. | Freelancer / Người nộp thuế TNCN | **Có** (Có thể nhận đầu vào là một file XML bất kỳ người dùng tự tải lên để kiểm thử). |
| 7 | **AI Step-by-step UI Companion**: AI đóng vai trò người đồng hành hướng dẫn từng bước nhấp chuột, giải thích chi tiết các nút bấm trên giao diện eTax của Tổng cục Thuế nhằm ngăn ngừa sai sót thao tác trong quá trình upload XML. | Freelancer / Người nộp thuế TNCN lần đầu | **Có** (Chỉ cần hệ thống hướng dẫn đồ họa hoặc extension chạy ở client-side). |

Chúng tôi có **5 use case thật sự độc lập** (1, 2, 3, 6, 7), hoàn toàn có thể triển khai trước độc lập để kiểm chứng giá trị mà không cần chờ toàn bộ nền tảng hoàn tất.

---

## Phát hiện ban đầu

- **Định dạng chứng từ hỗn loạn**: Chứng từ khấu trừ thuế TNCN tại Việt Nam (mẫu cũ dạng giấy tự in, mẫu mới điện tử) cực kỳ đa dạng về bố cục, font chữ tiếng Việt bị lỗi mã hóa khi trích xuất bằng OCR thông thường. Đây là thách thức công nghệ lớn nhất buộc phải dùng Gemini 2.5 Pro kết hợp GPT-4o để xử lý tốt đa định dạng.
- **Tâm lý phòng thủ dữ liệu**: Người dùng rất e ngại việc chia sẻ ảnh chụp chứng từ có chứa Số CCCD và địa chỉ nhà. Việc xây dựng cơ chế mã hóa và bôi đen dữ liệu nhạy cảm (Client-side Masking) ngay tại trình duyệt là bắt buộc để có được sự tin tưởng (Adoption).
- **Rào cản quy trình nộp**: 80% người dùng bỏ cuộc không phải ở bước tính toán số thuế, mà ở bước khai báo sai cơ quan thuế thụ lý (do thay đổi công việc liên tục trong năm) dẫn đến hồ sơ bị eTax trả lại sau nhiều ngày chờ đợi.

## Câu hỏi mở (mang sang bước chọn Quick Win)

- Làm thế nào để giải quyết bài toán OCR các chứng từ thuế bị mờ, chụp nghiêng từ camera điện thoại với chi phí API tối ưu nhất (dưới 100đ/chứng từ)?
- Liệu chúng ta có nên chọn Use case **1 (AI OCR trích xuất chứng từ) kết hợp 4 (Tính số thuế hoàn/phải nộp)** làm Quick Win đầu tiên để chứng minh hiệu năng sản phẩm ngay lập tức cho người dùng không?


---

## Tổng kiểm tra trước khi sang `2-quick-win.md`

| Hạng mục | Xong? |
|---|---|
| Cả nhóm phát biểu lại Big Ask giống nhau, không cần nhìn card | / |
| Có 5–8 use case dạng "AI làm X cho ai để Y" | / |
| Có ≥4 use case thật sự độc lập | / |
| Nhóm KHÔNG còn ý định pitch "build cả platform" | / |

Sau bước này, mở `2-quick-win.md` — chấm điểm chọn 1 lát cắt làm trước.

*Liên quan: handbook §A1+§A2 · `prompts/01-breakdown.md` · `00-context.md`*
