# Hướng dẫn thực hiện bước 1 giai đoạn 1: Phân tích và thiết kế dự án PolyShop

## Mục tiêu
Hướng dẫn sinh viên thực hiện bước 1 của giai đoạn 1 trong dự án PolyShop, tập trung vào nghiên cứu, phân tích yêu cầu khách hàng và xây dựng các sơ đồ phân tích (Use Case Diagram và ERD).

## Ý 1.1: Nghiên cứu và phân tích yêu cầu khách hàng

### 1. Nghiên cứu yêu cầu khách hàng
- **Mục đích**: Hiểu rõ nhu cầu của PolyShop và khách hàng mục tiêu để xác định các chức năng cần thiết cho website.
- **Các bước thực hiện**:
  1. **Thu thập thông tin**:
     - Tìm hiểu về PolyShop: cửa hàng kinh doanh đa dạng sản phẩm thuộc nhiều danh mục.
     - Xác định đối tượng khách hàng: người tiêu dùng muốn xem thông tin sản phẩm và gửi phản hồi.
     - Ghi nhận các yêu cầu cụ thể: website giới thiệu sản phẩm, thu nhận phản hồi, quản lý danh mục và sản phẩm.
  2. **Liệt kê yêu cầu chức năng**:
     - **Khách hàng**:
       - Xem danh mục sản phẩm.
       - Xem chi tiết sản phẩm.
       - Gửi phản hồi về sản phẩm.
     - **Quản trị viên**:
       - Quản lý danh mục (thêm, sửa, xóa).
       - Quản lý sản phẩm (thêm, sửa, xóa).
       - Xem và xử lý phản hồi từ khách hàng.
  3. **Liệt kê yêu cầu phi chức năng**:
     - Giao diện thân thiện, dễ sử dụng.
     - Website tải nhanh, tương thích trên nhiều thiết bị.
     - Bảo mật thông tin phản hồi và dữ liệu quản trị.

### 2. Hoàn thiện sơ đồ phân tích Use Case
- **Mục đích**: Minh họa các tương tác giữa người dùng (actors) và hệ thống website PolyShop.
- **Các bước thực hiện**:
  1. **Xác định actors**:
     - **Khách hàng**: Người truy cập website để xem sản phẩm và gửi phản hồi.
     - **Quản trị viên**: Người quản lý danh mục, sản phẩm và phản hồi.
  2. **Xác định use case**:
     - **Khách hàng**:
       - Xem danh mục sản phẩm.
       - Xem chi tiết sản phẩm.
       - Gửi phản hồi.
     - **Quản trị viên**:
       - Đăng nhập hệ thống.
       - Quản lý danh mục (thêm, sửa, xóa).
       - Quản lý sản phẩm (thêm, sửa, xóa).
       - Xem và xử lý phản hồi.
  3. **Vẽ sơ đồ Use Case**:
     - Sử dụng công cụ như Draw.io, Lucidchart hoặc Microsoft Visio.
     - Đảm bảo sơ đồ bao gồm:
       - Các actors (Khách hàng, Quản trị viên).
       - Các use case được liệt kê ở trên.
       - Mối quan hệ giữa actors và use case (association).
       - Mối quan hệ giữa các use case (nếu có, ví dụ: "Đăng nhập" là điều kiện tiên quyết cho các tác vụ quản trị).
  4. **Mô tả chi tiết từng Use Case**:
     - Ví dụ: **Use Case: Xem danh mục sản phẩm**
       - **Actor**: Khách hàng.
       - **Mô tả**: Khách hàng truy cập trang chủ để xem danh sách các danh mục sản phẩm.
       - **Điều kiện tiên quyết**: Website đang hoạt động.
       - **Kết quả**: Hiển thị danh sách danh mục sản phẩm.

### 3. Hoàn thiện sơ đồ phân tích ERD (Level 1, ER)
- **Mục đích**: Thiết kế sơ đồ thực thể - quan hệ (ERD) để mô tả cấu trúc cơ sở dữ liệu cho website PolyShop.
- **Các bước thực hiện**:
  1. **Xác định các thực thể (Entities)**:
     - **Category**: Danh mục sản phẩm (ví dụ: điện tử, thời trang).
     - **Product**: Sản phẩm thuộc danh mục.
     - **Feedback**: Phản hồi từ khách hàng.
     - **Admin**: Tài khoản quản trị viên.
  2. **Xác định thuộc tính (Attributes)**:
     - **Category**:
       - `category_id` (khóa chính, số nguyên).
       - `name` (tên danh mục, chuỗi).
       - `description` (mô tả, chuỗi, tùy chọn).
     - **Product**:
       - `product_id` (khóa chính, số nguyên).
       - `category_id` (khóa ngoại, liên kết với Category).
       - `name` (tên sản phẩm, chuỗi).
       - `description` (mô tả, chuỗi).
       - `price` (giá, số thực).
       - `image` (đường dẫn hình ảnh, chuỗi, tùy chọn).
     - **Feedback**:
       - `feedback_id` (khóa chính, số nguyên).
       - `product_id` (khóa ngoại, liên kết với Product).
       - `customer_name` (tên khách hàng, chuỗi).
       - `comment` (nội dung phản hồi, chuỗi).
       - `created_at` (thời gian gửi, ngày giờ).
     - **Admin**:
       - `admin_id` (khóa chính, số nguyên).
       - `username` (tên đăng nhập, chuỗi).
       - `password` (mật khẩu, chuỗi, mã hóa).
  3. **Xác định quan hệ (Relationships)**:
     - Một **Category** có nhiều **Product** (quan hệ 1-n).
     - Một **Product** có nhiều **Feedback** (quan hệ 1-n).
     - **Admin** quản lý **Category**, **Product**, và **Feedback** (quan hệ quản lý).
  4. **Vẽ sơ đồ ERD**:
     - Sử dụng công cụ như Draw.io, Lucidchart hoặc MySQL Workbench.
     - Đảm bảo sơ đồ bao gồm:
       - Các thực thể với thuộc tính.
       - Khóa chính và khóa ngoại.
       - Mối quan hệ giữa các thực thể (dùng ký hiệu như mũi tên hoặc đường nối với chú thích 1-n, 1-1).
  5. **Kiểm tra tính hợp lệ**:
     - Đảm bảo không có thực thể hoặc thuộc tính dư thừa.
     - Kiểm tra tính toàn vẹn tham chiếu (referential integrity) giữa các khóa ngoại.

## Hướng dẫn nộp sản phẩm
- **Tài liệu nộp**:
  - Báo cáo phân tích yêu cầu khách hàng (file Word hoặc PDF).
  - Sơ đồ Use Case (file hình ảnh PNG/JPG hoặc PDF).
  - Sơ đồ ERD (file hình ảnh PNG/JPG hoặc PDF).
- **Định dạng**:
  - Báo cáo: Font Times New Roman, cỡ chữ 12, cách dòng 1.5.
  - Sơ đồ: Đảm bảo rõ ràng, dễ đọc, có chú thích đầy đủ.
- **Nộp bài**: Nộp qua hệ thống quản lý học tập (nếu có) hoặc theo hướng dẫn của giảng viên.

## Tài liệu tham khảo
- Hướng dẫn vẽ sơ đồ Use Case: https://www.lucidchart.com/pages/uml-use-case-diagram
- Hướng dẫn vẽ sơ đồ ERD: https://www.visual-paradigm.com/guide/data-modeling/what-is-entity-relationship-diagram/
- Công cụ hỗ trợ: Draw.io (https://app.diagrams.net/), Lucidchart, MySQL Workbench.