---
title: 00 — Context (bối cảnh nhóm + track)
section: Day 28 — điền 1 lần đầu buổi, dùng lại cho mọi lần hỏi AI
format: Nhóm 3
time: Điền ~5 phút đầu buổi
---

# 00-context.md — Context nhóm + track

Điền file này một lần ở đầu buổi. Mỗi lần dùng AI ở các bước sau, paste nguyên nội dung file này vào đầu cuộc trò chuyện. AI không tự nhớ context giữa các lần — context khác nhau thì câu trả lời cũng lệch.

---

## 1. Bối cảnh AI20k (đọc, không sửa)

Khóa **AI Thực Chiến** có ~500 học viên (sinh viên năm cuối + người đi làm), đang chuẩn bị cho giai đoạn 6 tuần thực chiến sau Day 28. Lab này do track Product (~80 học viên, nhóm 3) làm. Hoạt động cả khóa nằm trên Discord, LMS, lớp live, lab, nộp bài, coaching — ở quy mô ~500 người.

Lãnh đạo chương trình muốn xây **AI20k Learning OS** — một hệ công cụ AI hỗ trợ học và vận hành khóa. Chính quy mô ~500 người là lý do **không build hết cùng lúc** được: mỗi nhóm nhận 1 track (1 công cụ lớn), tách nhỏ, chọn Quick Win, viết AI Pilot Plan để xin pilot.

Việc của nhóm hôm nay đúng là việc một PM/PO AI làm ngoài doanh nghiệp thật: stakeholder giao một "công cụ AI" quá lớn — bạn phải tách nhỏ, chọn đúng phần làm trước, và bảo vệ lựa chọn bằng lập luận chứ không bằng slide đẹp.

---

## 2. Track của nhóm (điền sau khi nhận track card)

- **Track số / tên**: Track Đặc Biệt / AI Hỗ Trợ Quyết Toán Thuế TNCN (Personal Income Tax Assistant)
- **Big Ask — chép nguyên văn câu yêu cầu trong track card**:

```text
Xây dựng một ứng dụng AI hỗ trợ tự động hóa việc thu thập, xử lý chứng từ khấu trừ thuế TNCN, tra cứu luật thuế và lập tờ khai quyết toán thuế xuất file XML chuẩn để nộp trực tiếp lên hệ thống eTax của Tổng cục Thuế, giúp giảm thiểu thời gian tự quyết toán từ 8 giờ xuống dưới 15 phút, tăng tỷ lệ nộp hồ sơ thành công ngay lần đầu từ 15% lên 95%, và tiết kiệm tối thiểu 700.000 VNĐ chi phí thuê kế toán dịch vụ cho mỗi cá nhân làm công ăn lương hoặc freelancer có nhiều nguồn thu nhập.
```

- **Công cụ lớn này phục vụ ai** (học viên / coach / instructor / admin): Cá nhân người làm công ăn lương có nhiều nguồn thu nhập và Freelancers tự do tại Việt Nam.
- **2 Red Flag đáng lo nhất (chép từ track card)**:
  1. **Legal & Accuracy Risk**: Rủi ro ảo giác pháp lý (AI dẫn sai luật thuế hoặc tính sai tiền thuế dẫn đến phạt hành chính từ 1.000.000đ - 12.500.000đ theo Nghị định 310/2025/NĐ-CP).
  2. **Data Privacy & Security**: E ngại về an toàn thông tin khi tải dữ liệu nhạy cảm (Ảnh chứng từ thuế, mã số thuế, số CCCD) lên AI.

---

## 3. Ràng buộc mọi track phải tôn trọng (đọc, không sửa)

- **Privacy** — data học viên/submission/Discord nhạy cảm; trong lab dùng data mẫu/giả định, nói rõ dùng cái gì.
- **Human review** — output rủi ro cao phải có người review, AI không tự quyết việc quan trọng.
- **Citation** — trả lời dựa trên tài liệu khóa thì phải có nguồn; thiếu nguồn thì nói "không biết", không bịa.
- **Budget nhỏ** — ưu tiên tool/API có sẵn, prototype nhanh, không xây platform lớn.
- **Formative ≠ summative** — feedback/chấm bằng AI là formative, chưa phải điểm chính thức nếu chưa có người calibrate.
- **Adoption** — tool không ai dùng = $0 dù accuracy 99%.
- **Pilot đủ nhỏ** — chạy được trong bối cảnh khóa hiện tại.

---

## 4. Ghi chú thêm (tùy nhóm)

- **Hạn chót triển khai**: Trước mùa quyết toán thuế TNCN cao điểm (tháng 3 và tháng 4 hàng năm).
- **Quy mô data pilot**: Thử nghiệm trên 50-100 người dùng thật (Freelancer, lập trình viên tự do, nhân viên văn phòng).
- **Mô hình chính**: Gemini 2.5 Pro (Primary - tối ưu chi phí RAG) & GPT-4o (Fallback - tối ưu OCR ảnh mờ/nghiêng).
- **Ngân sách tối đa**: 10.000.000 VNĐ trọn gói cho giai đoạn pilot 14 ngày.


---

## Cách dùng

```text
1. Đầu buổi: điền mục 2 (+ mục 4 nếu cần). Mục 1 và 3 chỉ để đọc.
2. Mỗi lần mở AI ở một bước: paste nguyên file này vào đầu chat trước.
3. Chọn prompt trong ../prompts/ hợp bước đang làm, chỉnh lại theo track.
4. Đọc kỹ bản nháp AI ra → sửa cho đúng context nhóm → lưu vào đúng file worksheet/.
```

Chỗ `[...]` là chỗ cần điền; điền xong xóa ngoặc nếu muốn.
