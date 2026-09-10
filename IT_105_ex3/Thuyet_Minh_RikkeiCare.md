# BÁO CÁO THỰC HÀNH: TỔNG HỢP ACTIVITY & USE CASE DIAGRAM HỆ THỐNG RIKKEICARE

## 1. Mục tiêu và Bối cảnh
Tài liệu này là bản thuyết minh chi tiết cho bài thực hành mô hình hóa quy trình đặt lịch khám trực tuyến của hệ thống RikkeiCare. Báo cáo cung cấp các bảng phân rã chức năng và phân tích quan hệ logic dưới góc nhìn của một BA Lead.

---

## 2. PHẦN A — Phân tích Activity Diagram
Kịch bản nghiệp vụ: Bệnh nhân đặt lịch khám. Lễ tân kiểm tra khung giờ. Nếu Còn trống, Lễ tân thực hiện hai tác vụ song song: xác nhận lịch khám và gửi SMS nhắc lịch. Nếu Hết chỗ, Lễ tân báo chọn khung giờ khác và kết thúc luồng nghiệp vụ.

| Loại Node | Tên Node / Tác vụ | Swimlane phụ trách |
| :--- | :--- | :--- |
| Initial Node | Bắt đầu | — |
| Action | Đặt lịch khám | Bệnh nhân |
| Decision | Kiểm tra khung giờ (Còn trống / Hết chỗ) | Lễ tân |
| Fork | **Tách nhánh đồng thời (khi Còn trống)** | **Lễ tân** |
| Action | **Xác nhận lịch khám** | **Lễ tân** |
| Action | **Gửi SMS nhắc lịch** | **Lễ tân** |
| Join | **Gộp nhánh đồng thời (sau khi xử lý xong)** | **Lễ tân** |
| Action | **Báo chọn khung giờ khác (nhánh Hết chỗ)** | **Lễ tân** |
| Final Node | Kết thúc | — |

---

## 3. PHẦN B — Phân tích Use Case Diagram
Hệ thống yêu cầu Bệnh nhân phải Đăng nhập (bắt buộc) trước khi Đặt lịch khám. Khi đặt lịch, Bệnh nhân có thể tùy chọn Chọn bác sĩ chỉ định (không bắt buộc). Chức năng đặt lịch khám được chuyên biệt hóa thành hai dạng: Đặt lịch khám thường và Đặt lịch khám ưu tiên (phụ phí).

| Use Case A | Use Case B | Quan hệ | Giải thích logic |
| :--- | :--- | :--- | :--- |
| Đặt lịch khám | Đăng nhập | `<<include>>` | Phải đăng nhập trước khi đặt lịch khám (Bắt buộc). |
| Đặt lịch khám | Chọn bác sĩ chỉ định | `<<extend>>` | **Tính năng chọn bác sĩ là tùy chọn, bệnh nhân có thể yêu cầu thêm khi đặt lịch.** |
| Đặt lịch khám | Đặt lịch khám thường | `<<generalization>>` | Là một dạng chuyên biệt của Đặt lịch khám (Kế thừa). |
| Đặt lịch khám | **Đặt lịch khám ưu tiên** | `<<generalization>>` | **Là một dạng chuyên biệt của Đặt lịch khám (Kế thừa, có tính thêm phụ phí).** |

---
*Ghi chú: Sinh viên đính kèm file này cùng với hình ảnh xuất từ draw.io để nộp bài.*
