---
name: log-bug
description: >-
  Kích hoạt khi người dùng muốn log bug, tạo bug ticket, báo lỗi hoặc dùng cú pháp 'Bug:', 'Log bug:', 'Báo lỗi:'.
---

# Skill Log Bug (Chuẩn Hóa Cho Dự Án)

Skill này hướng dẫn AI sinh nội dung Bug Ticket ngắn gọn, súc tích, đi thẳng vào trọng tâm vấn đề, tuân thủ đúng template của dự án.

---

## 📌 CÚ PHÁP KÍCH HOẠT (TRIGGER SYNTAX)

Người dùng có thể kích hoạt bằng các cú pháp sau:
* `Bug: [Mô tả lỗi] | App: [Tên App] | Màn: [Tên Màn]`
* `Log bug: [Mô tả lỗi]`
* Hoặc nói trực tiếp hiện tượng lỗi tại màn hình nào của app nào.

> **LƯU Ý:**
> - Nếu người dùng **đã cung cấp App**: Tạo ticket ngay lập tức.
> - Nếu người dùng **chưa cung cấp App**: **BẮT BUỘC DỪNG LẠI VÀ HỎI TÊN APP**, tuyệt đối không tự ý gán hay suy đoán tên app.

---

## ⚠️ NGUYÊN TẮC BẮT BUỘC

1. **TUYỆT ĐỐI KHÔNG TỰ Ý ĐOÁN TÊN APP:**
   - Dự án có nhiều app: `FunnyTalk`, `OneLive`, `GlobaLive`, `TabbyBobby`, `Yaknik`, `OneLiver`, `Backend Dashboard`.
   - Luôn hỏi lại nếu chưa rõ app nào.
2. **VIẾT NGẮN GỌN, ĐI THẲNG VÀO TRỌNG TÂM:**
   - Không viết văn rườm rà, giải thích lòng vòng.
   - Các mục `Overview`, `Steps`, `Expected result`, `Actual Result` phải gãy gọn, cụ thể.

---

## 1. Cấu Trúc Bug Ticket Chuẩn

```markdown
### Tên bug:
[Tên App][Tên Màn Hình] - [Mô tả ngắn gọn lỗi xảy ra]

- **Overview:**
  [1 câu ngắn gọn mô tả hiện tượng lỗi]

- **App:** [Tên App chính xác]

- **Steps:**
  1. Tại màn hình [Tên Màn Hình], chạm vào [icon/mục].
  2. Thực hiện [thao tác cụ thể: vuốt/click/nhập].
  3. Quan sát [khu vực/phần tử lỗi].

- **Expected result:**
  1. [Kết quả mong đợi 1]
  2. [Không xuất hiện popup/lỗi]

- **Actual Result:**
  1. [Hiện tượng lỗi thực tế 1]
  2. [Hiện tượng lỗi thực tế 2: popup/thông báo lỗi]

- **Priority:** [Critical | Highest | High | Medium | Low | Lowest]
- **Severity:** [Critical | Major | Moderate | Minor | Cosmetic]
- **Defect type:** [Functional | Non-Functional | GUI | Others]
```

---

## 2. Tiêu Chí Phân Loại (Dropdown Options)

### 2.1. Priority (Độ ưu tiên xử lý)
*   **Critical:** Crash app, treo ứng dụng (ANR), mất mát dữ liệu, chặn luồng test chính.
*   **Highest:** Chức năng cốt lõi không hoạt động, ảnh hưởng luồng nghiệp vụ lớn.
*   **High:** Lỗi luồng chính, sai lệch trạng thái quan trọng, tính năng lớn bị hỏng.
*   **Medium:** Lỗi chức năng phụ, phân trang, bộ lọc, tìm kiếm.
*   **Low:** Lỗi trải nghiệm người dùng nhỏ (UX minor), xoay màn hình.
*   **Lowest:** Lỗi chính tả, thẩm mỹ rất nhỏ.

### 2.2. Severity (Mức độ nghiêm trọng kỹ thuật)
*   **Critical:** Crash app, freeze màn hình, mất dữ liệu.
*   **Major:** Tính năng lớn bị hỏng, không có workaround.
*   **Moderate:** Tính năng bị lỗi nhưng có workaround hoặc phạm vi nhỏ.
*   **Minor:** Lỗi nhỏ ở chức năng phụ hoặc giao diện.
*   **Cosmetic:** Lỗi giao diện thuần túy: sai icon, màu sắc, font chữ.

### 2.3. Defect Type
*   **Functional:** Lỗi tính năng, logic xử lý, tính toán, luồng dữ liệu.
*   **Non-Functional:** Lỗi hiệu năng (load chậm, timeout), gián đoạn mạng, background/kill app.
*   **GUI:** Lỗi giao diện, vỡ layout, lệch lề, sai kích thước.
*   **Others:** Lỗi cấu hình, ngôn ngữ dịch thuật.
