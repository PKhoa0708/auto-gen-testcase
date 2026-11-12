# Hướng Dẫn Viết Test Case Từ Spec (Quy chuẩn Chung cho Dự án Backend)

Tài liệu này đóng vai trò như một skill/guideline hướng dẫn AI Assistant và Tester cách phân tích Spec (đặc tả) và sinh ra (generate) bộ Test Cases chuẩn hóa, chi tiết, đảm bảo bao phủ 100% nội dung yêu cầu nghiệp vụ của bất kỳ màn hình nào.

---

## 1. Cấu Trúc Bảng Test Cases (Template)

Mỗi bộ Test Cases được viết dưới dạng bảng Markdown với 9 cột bắt buộc như sau:

| Classification I | Classification II | Classification III | Test case name | Priority | Test case ID | Pre-condition | Step | Expected result |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |

*   **Classification I:** Tên phân hệ hoặc màn hình chính trên hệ thống (Ví dụ: `User Management`, `Video Call Setting`).
*   **Classification II:** Chức năng, tab hoặc phân vùng nghiệp vụ chính trong màn hình đó (Ví dụ: `Search Filters`, `Cấu hình ghi hình`).
*   **Classification III:** Tên cụ thể của phần tử giao diện như nhãn (label), ô nhập (input box), button hoặc cột dữ liệu hiển thị (Ví dụ: `Button Save`, `Ô nhập UserID`, `Cột Delete`, `Cột No (STT)`).
*   **Test case name:** Tên test case viết bằng tiếng Việt rõ ràng, ngắn gọn nhưng đầy đủ mục đích kiểm thử (không dùng từ kỹ thuật trừu tượng).
*   **Priority:** Độ ưu tiên kiểm thử đối với ticket gồm 4 mức tiêu chuẩn (đánh giá dựa trên mức độ quan trọng và ảnh hưởng thực tế đối với phạm vi ticket):
    *   `Critical`: Các kịch bản sống còn của ticket (crash/treo app, hỏng dữ liệu nghiêm trọng, sai lệch thanh toán/bảo mật, tắc hoàn toàn luồng cốt lõi).
    *   `High`: Các trường hợp kiểm thử luồng nghiệp vụ chính (Core flow), điều kiện rẽ nhánh trọng tâm, validate logic quan trọng, phân quyền.
    *   `Medium`: Các trường hợp kiểm thử hiển thị giao diện, căn lề dữ liệu, định dạng hiển thị ngày/giờ/tiền tệ, tìm kiếm, phân trang, validate biên/ngoại lệ và thông báo lỗi thông thường.
    *   `Low`: Các trường hợp kiểm thử giao diện phụ, trải nghiệm người dùng nhỏ (UI/UX minor), hủy thao tác, các kịch bản hiếm gặp ít tác động đến mục tiêu ticket.
*   **Test case ID:** Mã test case định dạng chuẩn và duy nhất (Ví dụ: `TC-[MÃ MÀN HÌNH]-[SỐ THỨ TỰ]`).
*   **Pre-condition:** Điều kiện tiên quyết trước khi thực hiện test.
*   **Step:** Các bước thực hiện chi tiết theo quy tắc Click-by-Click.
*   **Expected result:** Kết quả mong đợi sau khi thực hiện các bước trên.

---

## 2. Quy Tắc Viết Cột "Step" (Click-by-Click)

Để bất kỳ ai không hiểu về logic của hệ thống vẫn có thể đọc và thực hiện test chính xác, cột **Step** phải tuân thủ nghiêm ngặt định dạng sau:

1.  **Bước 1 luôn là xác định vị trí bắt đầu:** 
    *   Bắt buộc phải ghi rõ: `1. Tại màn hình nào [Tên màn hình cụ thể],`
    *   *Không được phép viết chung chung* như "tại màn hình danh sách bất kỳ" hoặc "tại trang quản trị".
2.  **Bước 2 bắt đầu bằng hành động click hoặc quan sát tại chỗ:**
    *   Định dạng: `2. Click chuột vào [Tên trường/Button]...` hoặc `2. Quan sát [Khu vực/Bảng]...`
3.  **Các bước tiếp theo:** 
    *   Mô tả chi tiết hành vi gõ bàn phím (nhập giá trị cụ thể), click chuột, hoặc các thao tác ngoại vi (ví dụ: ngắt kết nối mạng).
    *   Viết theo dạng *Click-by-Click* (hướng dẫn từng bước nhấn chuột).

**Ví dụ minh họa:**
> 1. Trên BE, tại màn hình Video call setting,
> 2. Click chuột vào ô nhập Start recording from the start of the call [ ] seconds.
> 3. Nhập số âm -10.
> 4. Click chuột trái vào button Save.
> 5. Quan sát dòng chữ báo lỗi hiển thị dưới ô nhập.

---

## 3. Quy Tắc Viết "Test Case Name" và Sử Dụng Đối Tượng Cụ Thể

*   **Không viết chung chung:** Thay vì viết *"Kiểm tra thêm thành công User"*, phải viết rõ hành động cụ thể *"Kiểm tra khi thêm thành công tài khoản [Vai trò A] vào [Tính năng X]"*.
*   **Sử dụng đối tượng/danh từ cụ thể để phân biệt vai trò:**
    *   Khi viết case kiểm thử **thành công**, sử dụng danh từ cụ thể kèm vai trò đại diện (Ví dụ: Performer A, User A, Admin A...).
    *   Khi viết case kiểm thử **báo lỗi/ngăn chặn**, sử dụng danh từ cụ thể đại diện cho vai trò bị chặn/lỗi (Ví dụ: Viewer B, User B, Member B...).
    *   Việc chỉ rõ tên giả lập giúp người test hình dung ngay loại tài khoản cần chuẩn bị trong cơ sở dữ liệu để test.

---

## 4. Quy Tắc Chuyển Đổi Quy Định Chung (Common Specs)

*   Các tài liệu quy định chung (Common Specs) chứa các quy định chung về căn lề bảng, định dạng ngày tháng, phân trang, thông báo lỗi hệ thống, xuất file...
*   Khi viết Test Cases cho một màn hình cụ thể, **không được bê nguyên văn các câu chữ chung chung** của Common Specs vào.
*   **Bắt buộc phải ánh xạ (map) các quy định đó lên các trường, cột, hoặc phần tử cụ thể của màn hình đang viết test**:
    *   *Ví dụ Common Spec:* "Các cột chữ viết thường căn trái".
    *   *Ánh xạ vào Test Case:* "1. Tại màn hình [Tên màn hình], 2. Quan sát cách căn lề của các dữ liệu hiển thị trong cột [Cột A], [Cột B]... trong bảng danh sách."
    *   *Ví dụ Common Spec:* "Nhập số âm thì báo lỗi lớn hơn hoặc bằng 1".
    *   *Ánh xạ vào Test Case:* "1. Tại màn hình [Tên màn hình], 2. Click chuột vào ô nhập [Tên ô nhập] và điền số âm -5. 3. Click chuột trái vào nút Save." (Điều chỉnh thông báo lỗi và mốc validate tương ứng với nghiệp vụ của màn hình đó).

---

## 5. Quy Tắc Độc Lập và Rõ Ràng (Không Tham Chiếu Spec)

Để bất kỳ Tester nào khi đọc bộ Test Cases cũng có thể hiểu, chuẩn bị data và thực hiện kiểm thử độc lập mà không cần mở tài liệu đặc tả (Spec) để đối chiếu, cần tuân thủ:
1.  **Không ghi số mục của Spec:** Tuyệt đối không viết những cụm từ như `(mục số 1)`, `(mục 4)`, `(mục số 10)` hay `(C)` trong cột Step và Expected result. Chỉ sử dụng tên hiển thị thực tế của phần tử giao diện (Ví dụ: `button Save`, `button Add`, `bảng danh sách`).
2.  **Tránh các ký hiệu trừu tượng và biến số:** Không sử dụng các ký hiệu toán học hoặc biến đại số như `X`, `Y` hay các công thức `Y > X` trong mô tả các bước hay kết quả mong đợi. Bắt buộc phải thay thế bằng các ví dụ số nguyên cụ thể hoặc diễn đạt bằng chữ rõ ràng (Ví dụ: thay vì ghi *"thời lượng từ giây X đến giây Y"*, hãy ghi rõ *"giây thứ 10 đến giây thứ 40"*).
3.  **Mô tả rõ ràng vị trí và đối tượng:** Mô tả chi tiết hành động dựa trên nhãn button/ô nhập hiển thị trên màn hình.
4.  **Gom nhóm test case theo Classification III tuần tự:** Gom tất cả các test case kiểm thử liên quan đến cùng một phần tử (ví dụ: kiểm tra chặn chữ, nhập số âm, số thập phân, giới hạn ký tự, để trống) lại với nhau trước khi chuyển sang phần tử tiếp theo. Thứ tự các phần tử kiểm thử đi từ trên xuống dưới, từ trái sang phải theo bố cục giao diện.

---

## 6. Quy Tắc Xác Định Phạm Vi (Scope) Kiểm Thử

Để tối ưu hóa thời gian viết và kiểm thử của dự án, cần xác định đúng phạm vi thay đổi của spec:
1.  **Đối với màn hình/phân vùng mới thêm hoàn toàn:** 
    *   Viết đầy đủ tất cả các trường hợp kiểm thử (giao diện hiển thị, validate đầu vào, hoạt động button, bộ phân trang, tìm kiếm và các quy tắc nghiệp vụ liên quan đến phần được thêm mới).
2.  **Đối với màn hình cũ đã tồn tại sẵn và chỉ thay đổi logic (Business Rule):**
    *   Chỉ viết các test case kiểm thử trực tiếp cho logic nghiệp vụ mới thay đổi.
    *   **Tuyệt đối không** viết lại toàn bộ các test case liên quan đến giao diện cũ, thanh tìm kiếm cũ, phân trang cũ... đã chạy ổn định để tránh gây loãng bộ test case và lãng phí thời gian.

---

## 7. Quy Tắc Thiết Lập Classification III Cho Bảng Danh Sách

Khi thiết lập giá trị cột `Classification III` cho các bảng hiển thị dữ liệu:
1.  **Không đặt nhãn tự do:** Bắt buộc phải chia nhãn trùng khớp chính xác 100% với tên hiển thị đầy đủ của **các cột thực tế hiển thị trên giao diện**.
2.  **Gom các thành phần bổ trợ:** Các thành phần như **Total item** (tổng số bản ghi hiển thị) và **Paging / Bộ phân trang** (First, Previous, Next, Last) bắt buộc phải được gom chung vào cột đầu tiên của bảng danh sách (thường là cột số thứ tự `No` hoặc `STT`), không tách riêng thành các dòng nghiệp vụ độc lập ngoài cấu trúc bảng.

---

## 8. Quy Tắc Viết Test Case Cho Business Rules (Quy Tắc Nghiệp Vụ)

Khi kiểm thử các quy tắc nghiệp vụ (Business Rules - BR), để đảm bảo bao phủ 100% các kịch bản thực tế, cần tuân thủ:
1.  **Mô phỏng luồng hoạt động thực tế:** Phải viết các test case thực hiện các hành động thực tế trên hệ thống (Ví dụ: thực hiện cuộc gọi video call, tiến hành giao dịch thanh toán) và kiểm tra kết quả lưu trữ ngầm, lưu record hoặc ghi log trên Backend (BE).
2.  **Bao phủ mọi vai trò đối tượng:** Kiểm thử đầy đủ với tất cả các vai trò người dùng có trong spec (Ví dụ: cả Viewer và Performer khi được thêm vào danh sách thì cuộc gọi đều phải được tự động ghi hình).
3.  **Kiểm thử các mốc biên và giá trị nằm ngoài cấu hình:** 
    *   Kiểm thử trường hợp thời lượng hoặc giá trị thực tế nằm ngoài mốc cấu hình (Ví dụ: cuộc gọi kết thúc trước giây bắt đầu cấu hình, hoặc cuộc gọi kết thúc trước giây kết thúc cấu hình) xem hệ thống có xử lý chính xác hay không.
    *   Kiểm thử các chu kỳ lưu trữ (Ví dụ: dữ liệu tự động xóa sau 7 ngày - kiểm tra trong vòng 7 ngày và sau khi kết thúc 7 ngày).
4.  **Kiểm thử tính độc lập (Tránh xung đột logic):** Đảm bảo tính năng hoạt động độc lập và không bị ảnh hưởng hay bị đè bởi các cấu hình/cài đặt khác của hệ thống (Ví dụ: tính năng tự động ghi hình vẫn hoạt động bình thường bất kể cài đặt Merit của user được tick hay không).
5.  **Kiểm thử tính đồng bộ và cập nhật thời gian thực (Realtime):** 
    *   Đối với các tính năng có yêu cầu thời gian thực, cần viết case kiểm tra xem dữ liệu/trạng thái trên giao diện Backend có được cập nhật tức thời (realtime) mà không cần tải lại trang (reload) khi có sự kiện thay đổi từ phía client hoặc thiết bị khác phát sinh.
    *   Kiểm tra tính nhất quán và độ ổn định của dữ liệu thời gian thực khi người dùng chuyển đổi liên tục giữa các Tab chính/các trang hoặc khi xảy ra gián đoạn mạng và tự động khôi phục kết nối.

---

## 9. Quy Trình Phân Tích Spec Để Viết Test Cases

Mỗi khi nhận được file spec mới:
1.  **Đọc kỹ cấu trúc giao diện (UI Mockup) & Logic Validate:** Liệt kê tất cả các ô nhập liệu, button và các điều kiện validate (rỗng, số âm, số thập phân, ký tự chữ, độ dài tối đa). Đọc kỹ xem spec cho phép/chặn những vai trò/quyền nào để thiết lập case thành công/thất bại chính xác.
2.  **Đọc kỹ các Quy tắc Nghiệp vụ (Business Rules - BR):** Liệt kê các logic xử lý ngầm dưới Backend, logic phân quyền, trạng thái đè (override) và logic lưu trữ dữ liệu.
3.  **Kết hợp với Common Specs:** Đưa các test cases về căn lề tiêu đề, căn lề dữ liệu, định dạng hiển thị ngày/giờ, phân trang (ví dụ 25 dòng/trang), và các thông báo lỗi chuẩn hóa vào bộ test case của màn hình đó.
4.  **Chuyển đổi toàn bộ thành bảng Test Cases** theo đúng cấu trúc Click-by-Click và cụ thể hóa đối tượng đại diện (User A, User B).

---

## 10. Cách Viết Test Case Chi Tiết (Không Tóm Tắt)

*   **Đảm bảo tính chi tiết:** Viết test case phải đủ chi tiết để người không đọc spec hoặc không tham gia dự án vẫn biết mình phải thực hiện các bước như thế nào để test.
*   **Kiểm tra theo thứ tự hợp lý:** Kiểm tra theo thứ tự từ tổng thể màn hình -> các mục trong spec yêu cầu theo thứ tự từ trên xuống dưới, từ trái sang phải (tuyệt đối không ghi các số thứ tự được đánh kèm trong spec vào test case).
*   **Không tóm tắt gộp bước:** Chỉ viết rõ ràng các hành động cần thực hiện ở Step và Expected result tương ứng, không gộp nhiều hành động validate độc lập vào cùng một bước.

---

## 11. Quy Chuẩn Viết Description & Objective Cho Ticket Kiểm Thử (Jira/Redmine Ticket)

Khi được yêu cầu viết mô tả phạm vi và mục tiêu kiểm thử cho một ticket/subtask của dự án, tester cần xây dựng một bảng Markdown 2 cột: `Description` | `Objective` với quy chuẩn nội dung như sau:

### 11.1. Cột "Description" (Mô tả Phạm vi kiểm thử)
*   **Khái quát hóa phạm vi:** Sử dụng các đầu dòng `-` để tóm tắt các khu vực/phần hệ/màn hình cần thực hiện rà soát và kiểm thử (ví dụ: Backend Dashboard, các ứng dụng Client Viewer cụ thể).
*   **Các luồng nghiệp vụ cần kiểm chứng:** Nêu rõ các hành vi, logic nghiệp vụ cốt lõi cần xác thực (ví dụ: đọc cấu hình từ BE để tự động áp dụng bật/tắt camera trước khi bắt đầu cuộc gọi).
*   **Kiểm thử ngoại lệ & nâng cao:** Đề cập cụ thể các kịch bản nâng cao cần rà soát như kiểm thử gián đoạn (GSM call, chạy ngầm background), kiểm thử mạng (mất mạng, chuyển mạng Wifi/4G), stress test thao tác liên tục, cô lập cấu hình (isolation test) giữa các app.

### 11.2. Cột "Objective" (Mục tiêu kiểm thử)
*   **Xác thực đặc tả (Spec):** Nêu rõ mục tiêu đảm bảo hệ thống tính toán, lưu trữ, xử lý logic nghiệp vụ và hiển thị giao diện song ngữ (Anh/Nhật), nhãn trạng thái chính xác theo tài liệu đặc tả (Spec).
*   **Tính ổn định và đồng bộ:** Đảm bảo dữ liệu thời gian thực được đồng bộ nhất quán, hệ thống hoạt động mượt mà, không xảy ra hiện tượng đứng màn hình, lỗi luồng hoặc crash ứng dụng.
*   **Trải nghiệm người dùng & Ngoại lệ:** Đảm bảo luồng xử lý lỗi/hướng dẫn người dùng khi gặp sự cố ngoại lệ (ví dụ: mất kết nối mạng đột ngột, từ chối cấp quyền thiết bị) hoạt động đúng chuẩn và thân thiện với người dùng.

---

## 12. Quy Tắc Hỏi Rõ Thông Tin & Không Tự Ý Đoán Mò (Dành cho AI Assistant / Tester)

*   **Hỏi rõ trước khi thực hiện:** Trước khi bắt đầu làm việc, phải hỏi rõ tất cả các điều còn chưa rõ, không được tự ý đoán mò hay tự suy diễn.
*   **Không tự bịa nội dung dữ liệu:** Khi có tin nhắn hệ thống gửi về hoặc các thông tin chưa đầy đủ, bắt buộc phải hỏi lại nội dung tin nhắn/thông tin đó như thế nào, tuyệt đối không được tự bịa ra nội dung.