# Test Cases - Video Call Monitoring Screen

Tài liệu này chứa danh sách các test case chi tiết cho màn hình **Video Call Monitoring** trên Backend (BE), được thiết kế theo đúng quy chuẩn dự án và cấu trúc Click-by-Click.

---

## I. Quy chuẩn viết Test Case

- **Bảng Test Case 9 cột:** `Classification I` | `Classification II` | `Classification III` | `Test case name` | `Priority` | `Test case ID` | `Pre-condition` | `Step` | `Expected result`
- **Bước 1 của Step:** Luôn bắt đầu bằng `1. Trên BE, tại màn hình Video call monitoring,`
- **Các bước tiếp theo:** Click-by-Click chi tiết từng thao tác của Tester.
- **Đối tượng cụ thể:** 
  - **Performer A** / **Viewer B**: Tài khoản **nằm trong** danh sách cấu hình tự động ghi hình (Video call record setting).
  - **Performer C** / **Viewer D**: Tài khoản **không nằm trong** danh sách cấu hình tự động ghi hình.
- **Tính độc lập:** Không ghi số mục của Spec (như mục số 1, mục 4...) và không dùng các ký hiệu toán học đại số trừu tượng (như X, Y...) để đảm bảo bất kỳ ai cũng có thể đọc và hiểu để test được ngay mà không cần đối chiếu Spec.
- **Classification III chi tiết:** Ghi rõ ràng tên hiển thị đầy đủ của nhãn (label), ô nhập (input box) hay nút bấm (button), không viết tắt hoặc sử dụng dấu ba chấm (...).
- **Tuần tự nhóm:** Các test case được gom nhóm hoàn chỉnh theo từng Control ở Classification III trước khi chuyển sang Control tiếp theo.

---

## II. Bảng Test Cases - Nghiệp vụ thay đổi (Business Rules)

| Classification I | Classification II | Classification III | Test case name | Priority | Test case ID | Pre-condition | Step | Expected result |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Video Call Monitoring** | Theo dõi cuộc gọi | BR01 | Kiểm tra tự động vô hiệu hóa cả hai nút Start record và End record đối với cuộc gọi của user nằm trong danh sách ghi hình tự động | High | **TC-VCM-001** | **Performer A** (hoặc **Viewer B**) đã được cấu hình trong danh sách tự động ghi hình (ở màn hình Video Call Setting). Performer A (hoặc Viewer B) đang tham gia một cuộc gọi video đang hoạt động. | 1. Trên BE, tại màn hình Video call monitoring,<br>2. Nhập User ID của Performer A (hoặc Viewer B) vào ô tìm kiếm và click nút `Search`.<br>3. Quan sát trạng thái hiển thị của hai nút `Start record` và `End record` tại dòng hiển thị cuộc gọi tương ứng. | Cả hai nút `Start record` và `End record` đều hiển thị ở trạng thái vô hiệu hóa (disable - mờ đi) và admin hoàn toàn không thể click tương tác. |
| **Video Call Monitoring** | Theo dõi cuộc gọi | BR01 | Kiểm tra trạng thái hiển thị của hai nút đối với cuộc gọi của user không nằm trong danh sách ghi hình tự động | High | **TC-VCM-002** | **Performer C** đang tham gia cuộc gọi video và **không** nằm trong danh sách tự động ghi hình. | 1. Trên BE, tại màn hình Video call monitoring,<br>2. Nhập User ID của Performer C vào ô tìm kiếm và click nút `Search`.<br>3. Quan sát trạng thái hiển thị mặc định của hai nút `Start record` và `End record` tại dòng hiển thị cuộc gọi tương ứng. | - Nút `Start record` hiển thị ở trạng thái hoạt động bình thường (enable - sáng lên) cho phép click.<br>- Nút `End record` mặc định hiển thị ở trạng thái vô hiệu hóa (disable - mờ đi) vì cuộc gọi chưa bắt đầu ghi hình. |
| **Video Call Monitoring** | Theo dõi cuộc gọi | BR01 | Kiểm tra cập nhật thời gian thực (realtime) trạng thái các nút bấm khi cuộc gọi mới phát sinh | High | **TC-VCM-003** | **Performer A** (hoặc **Viewer B**) đã được cấu hình trong danh sách tự động ghi hình (ở màn hình Video Call Setting). Admin đang mở và quan sát màn hình Video call monitoring trên Backend. | 1. Cho Performer A (hoặc Viewer B) thực hiện cuộc gọi video để cuộc gọi bắt đầu hoạt động.<br>2. Tại màn hình Video call monitoring trên Backend, quan sát bảng danh sách cuộc gọi đang diễn ra mà không thực hiện tải lại trang (reload). | Cuộc gọi mới của Performer A (hoặc Viewer B) tự động xuất hiện trong danh sách hiển thị trên màn hình Backend (realtime). Tại dòng tương ứng của cuộc gọi này, hai nút `Start record` và `End record` tự động hiển thị ở trạng thái vô hiệu hóa (disable - mờ đi) ngay lập tức mà không cần reload trang. |
