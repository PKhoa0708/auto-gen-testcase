---
name: gen-testcase
description: >-
  Kích hoạt khi người dùng muốn viết test case, tạo test case từ spec hoặc dùng cú pháp 'TC:', 'Gen TC:', 'Viết TC:'.
---

# Skill Viết Test Case Từ Spec (Quy Chuẩn Dự Án)

Skill này hướng dẫn AI phân tích Spec (đặc tả yêu cầu) và tạo bộ Test Cases chuẩn hóa, chi tiết theo đúng quy chuẩn dự án tại `Skill/skill.md`.

---

## 📌 CÚ PHÁP KÍCH HOẠT (TRIGGER SYNTAX)

Người dùng có thể kích hoạt bằng các cú pháp sau:
* `Gen TC: [Tên tính năng / Tên màn hình] kèm spec`
* `Viết test case: [Tên tính năng / Tệp spec]`
* `TC: [Tên màn hình] ...`
* Hoặc cung cấp nội dung đặc tả (Spec/BR) và yêu cầu viết kịch bản kiểm thử.

---

## 1. Cấu Trúc Bảng Test Cases Bắt Buộc (9 Cột)

```markdown
| Classification I | Classification II | Classification III | Test case name | Priority | Test case ID | Pre-condition | Step | Expected result |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
```

- **Classification I:** Tên phân hệ hoặc màn hình chính (Ví dụ: `Màn Moments`, `User Management`).
- **Classification II:** Tab, chức năng hoặc phân vùng nghiệp vụ (Ví dụ: `Tab All`, `Search Filters`).
- **Classification III:** Phần tử cụ thể trên UI (Button, Input, Cột dữ liệu...) theo thứ tự từ trên xuống dưới, trái qua phải.
- **Priority:** Sử dụng 4 mức `Critical` | `High` | `Medium` | `Low`, đánh giá dựa trên mức độ ưu tiên và ảnh hưởng thực tế đối với ticket.
- **Step (Click-by-Click):**
  1. Luôn xác định vị trí bắt đầu: `1. Tại màn hình [Tên màn hình],`
  2. Thao tác Click-by-Click: `2. Chạm/Click chuột vào [Tên Button/Trường]...`
  3. Ghi rõ giá trị nhập liệu và đối tượng cụ thể (User A, Performer B).
- **Tuyệt đối không tham chiếu số mục spec** như `(mục 1)`, `(theo spec)`.

---

## 2. Bảng Description & Objective (Ticket Header)

Khi được yêu cầu viết mô tả cho ticket/subtask kiểm thử, tạo bảng 2 cột:

```markdown
| Description (Phạm vi kiểm thử) | Objective (Mục tiêu kiểm thử) |
| :--- | :--- |
| - Phạm vi ứng dụng, màn hình...<br>- Luồng nghiệp vụ cốt lõi...<br>- Kiểm thử ngoại lệ & nâng cao... | - Xác thực đặc tả spec...<br>- Tính ổn định và đồng bộ...<br>- Trải nghiệm người dùng & ngoại lệ... |
```
