# Hướng Dẫn & Quy Chuẩn Log Bug Ticket (Dành Cho Dự Án)

Tài liệu này quy định cấu trúc và nguyên tắc chuẩn hóa khi ghi nhận (log) lỗi (Defect / Bug) lên hệ thống quản lý công việc của dự án. 

---

## 📌 Cú Pháp Kích Hoạt Nhanh

Để AI hoặc Tester tạo bug ticket chuẩn ngay lập tức, sử dụng một trong các cú pháp sau:
* `Bug: [Mô tả lỗi] | App: [Tên App] | Màn: [Tên Màn]`
* `Log bug: [Mô tả lỗi]`
* Hoặc miêu tả trực tiếp hiện tượng lỗi tại màn hình nào của ứng dụng nào.

> **Quy tắc bắt buộc:** Nếu chưa có Tên App, bắt buộc phải hỏi lại người test trước khi sinh ticket. Không được tự ý đoán app.


---

## 1. Mẫu Template Chuẩn

```markdown
### Tên bug:
[Tên App][Tên Màn Hình] - [Mô tả ngắn gọn lỗi xảy ra]

- **Overview:**
  [1 câu ngắn gọn mô tả hiện tượng lỗi]

- **App:** [Tên App chính xác]

- **Steps:**
  1. Tại màn hình chính của ứng dụng [Tên App], chạm vào [icon/mục].
  2. Thực hiện [thao tác cụ thể: vuốt/click/nhập].
  3. Quan sát [khu vực/phần tử lỗi].

- **Expected result:**
  1. [Kết quả mong đợi 1]
  2. [Không xuất hiện popup/lỗi]

- **Actual Result:**
  1. [Hiện tượng lỗi thực tế 1]
  2. [Hiện tượng lỗi thực tế 2: popup thông báo lỗi]

- **Priority:** [Critical | Highest | High | Medium | Low | Lowest]
- **Severity:** [Critical | Major | Moderate | Minor | Cosmetic]
- **Defect type:** [Functional | Non-Functional | GUI | Others]
```

---

## 2. Tiêu Chí Phân Loại (Dropdown Options)

### 2.1. Priority
*   **Critical:** Crash app, treo ứng dụng (ANR), mất mát dữ liệu.
*   **Highest:** Chức năng cốt lõi không hoạt động.
*   **High:** Lỗi luồng chính, sai lệch trạng thái quan trọng.
*   **Medium:** Lỗi chức năng phụ, phân trang, bộ lọc.
*   **Low:** Lỗi trải nghiệm người dùng nhỏ (UX minor).
*   **Lowest:** Lỗi chính tả, thẩm mỹ rất nhỏ.

### 2.2. Severity
*   **Critical:** Crash, freeze, mất dữ liệu.
*   **Major:** Tính năng lớn bị hỏng, không có workaround.
*   **Moderate:** Có giải pháp thay thế tạm thời (workaround).
*   **Minor:** Lỗi nhỏ ở chức năng phụ.
*   **Cosmetic:** Lỗi giao diện thuần túy: lệch màu, sai font, sai icon.

### 2.3. Defect Type
*   **Functional:** Lỗi tính năng, logic xử lý, dữ liệu sai.
*   **Non-Functional:** Lỗi hiệu năng, tải chậm, timeout, mạng.
*   **GUI:** Lỗi giao diện, vỡ layout, lệch lề.
*   **Others:** Lỗi cấu hình, dịch thuật.
