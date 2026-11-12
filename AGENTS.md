# Quy Tắc Định Tuyến Công Việc (Testing & Bug Workflow)

Khi làm việc trong dự án này, trợ lý AI phải tự động phân biệt và điều hướng giữa hai nghiệp vụ chính: **Tạo Bug Ticket (Log Bug)** và **Viết Test Case (Gen TC)** theo các cú pháp và quy chuẩn dưới đây.

---

## 1. Nghiệp Vụ 1: Tạo Bug Ticket (Log Bug)

### Dấu hiệu nhận biết / Cú pháp kích hoạt:
* Có từ khóa tiền tố: `Bug:`, `Log bug:`, `Báo lỗi:`.
* Hoặc người dùng mô tả một hành vi lỗi, sự cố hệ thống, hiển thị sai, crash, popup lỗi kèm hoặc chưa kèm Tên App & Màn hình.
* Ví dụ:
  - `Bug: Không lưu được setting | App: OneLive | Màn: Setting`
  - `Log bug: Màn chat detail bị lặp tin nhắn`
  - `Màn moments của FunnyTalk bị crash khi bấm like`

### Quy tắc thực hiện:
1. **Hỏi Tên App nếu chưa có:** Nếu người dùng chưa ghi rõ app nào (`FunnyTalk`, `OneLive`, `GlobaLive`, `TabbyBobby`, `Yaknik`, `OneLiver`, `BE`), **bắt buộc phải hỏi lại**, tuyệt đối không đoán mò.
2. **Phong cách viết:** Ngắn gọn, súc tích, đi thẳng vào vấn đề kỹ thuật, không rườm rà.
3. **Template bắt buộc:**
   - `Tên bug:` `[Tên App][Tên Màn] - [Mô tả ngắn gọn]`
   - `- Overview:` (1 câu)
   - `- App:`
   - `- Steps:` (1, 2, 3 ngắn gọn)
   - `- Expected result:`
   - `- Actual Result:`
   - `- Priority:` (Critical / Highest / High / Medium / Low / Lowest)
   - `- Severity:` (Critical / Major / Moderate / Minor / Cosmetic)
   - `- Defect type:` (Functional / Non-Functional / GUI / Others)

---

## 2. Nghiệp Vụ 2: Viết Test Case Từ Spec (Gen TC)

### Dấu hiệu nhận biết / Cú pháp kích hoạt:
* Có từ khóa tiền tố: `TC:`, `Gen TC:`, `Viết TC:`, `Viết test case:`.
* Hoặc người dùng cung cấp tài liệu đặc tả (Spec), yêu cầu nghiệp vụ (Business Rules) và yêu cầu sinh bảng kiểm thử.
* Ví dụ:
  - `Gen TC: Màn hình Login của FunnyTalk kèm spec...`
  - `Viết test case cho tính năng chuyển đổi ngôn ngữ comment`

### Quy tắc thực hiện:
1. **Tuân thủ [Skill/skill.md](file:///c:/test%20spec/Skill/skill.md):**
   - Bảng Markdown chuẩn 9 cột: `Classification I | Classification II | Classification III | Test case name | Priority | Test case ID | Pre-condition | Step | Expected result`.
   - Đánh giá `Priority` (4 mức: `Critical` / `High` / `Medium` / `Low`) dựa trên mức độ ảnh hưởng thực tế đối với ticket.
   - Cột `Step` theo chuẩn Click-by-Click rõ ràng (1. Tại màn hình..., 2. Chạm vào..., 3. Nhập...).
   - Bao phủ 100% UI Mockup, Validate, Business Rules và Common Specs.
   - Tuyệt đối không tham chiếu số mục spec (ví dụ: không viết `theo mục 1`).
2. **Bảng Description & Objective:** Cung cấp bảng 2 cột tổng quan khi được yêu cầu tạo ticket kiểm thử.
