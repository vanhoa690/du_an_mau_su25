# Hướng dẫn Dự án mẫu (TKTW) - WEB2041 - Hoadv SU25

# PolyShop Website sử dụng PHP cơ bản

## Giới thiệu

PolyShop là một cửa hàng kinh doanh đa dạng sản phẩm thuộc nhiều danh mục khác nhau. Dự án này nhằm xây dựng một website giới thiệu sản phẩm và thu nhận phản hồi từ khách hàng để cải tiến chất lượng. Dự án được thực hiện trong khuôn khổ môn học, tập trung vào việc phát triển website sử dụng PHP cơ bản.

## Yêu cầu dự án

Dự án được chia thành 2 giai đoạn với các yêu cầu cụ thể như sau:

### Giai đoạn 1

1. **Nghiên cứu yêu cầu khách hàng**: Tìm hiểu nhu cầu của PolyShop và khách hàng mục tiêu.
2. **Phân tích yêu cầu khách hàng**: Xác định các chức năng cần thiết cho website.
3. **Thiết kế layout website với Figma**: Tạo giao diện website trực quan, thân thiện với người dùng.
4. **Xây dựng layout website**: Chuyển đổi thiết kế Figma thành mã HTML/CSS, đảm bảo đồng bộ với thiết kế.
5. **Thiết kế database**: Thiết kế cơ sở dữ liệu cho các bảng `categories`, `products`, và các bảng liên quan.
6. **Xây dựng model**: Tạo các model PHP để xử lý kết nối cơ sở dữ liệu (`connect`), quản lý danh mục (`categories`) và sản phẩm (`products`).

### Giai đoạn 2

1. **Hoàn thiện website dành cho khách hàng**: Đảm bảo website có giao diện đẹp, dễ sử dụng, hiển thị danh mục và sản phẩm, hỗ trợ phản hồi từ khách hàng.
2. **Hoàn thiện website dành cho trang quản trị**: Xây dựng giao diện quản trị để quản lý danh mục, sản phẩm và phản hồi.
3. **Hoàn thiện document báo cáo dự án**: Viết tài liệu chi tiết mô tả quá trình phát triển dự án.
4. **Hoàn thiện slide báo cáo dự án**: Chuẩn bị slide thuyết trình tóm tắt dự án.

## Hướng dẫn cài đặt và chạy dự án

### Yêu cầu môi trường

- PHP >= 7.4
- MySQL >= 5.7
- Web server (Apache/Nginx)
- Composer (tùy chọn, nếu sử dụng thư viện PHP)

### Cài đặt

1. **Tải mã nguồn**:
   - Clone repository từ GitHub hoặc giải nén file mã nguồn.
   ```bash
   git clone <repository_url>
   ```
2. **Cấu hình cơ sở dữ liệu**:
   - Tạo database MySQL:
     ```sql
     CREATE DATABASE polyshop;
     ```
   - Import file SQL (`database.sql`) để tạo các bảng `categories`, `products`, v.v.
   - Cập nhật thông tin kết nối trong file `config.php`:
     ```php
     <?php
     define('DB_HOST', 'localhost');
     define('DB_USER', 'your_username');
     define('DB_PASS', 'your_password');
     define('DB_NAME', 'polyshop');
     ?>
     ```
3. **Cấu hình web server**:
   - Copy mã nguồn vào thư mục web server (ví dụ: `/var/www/html/polyshop`).
   - Đảm bảo thư mục có quyền ghi cho các file log hoặc upload (nếu có).
4. **Chạy dự án**:
   - Truy cập website qua trình duyệt: `http://localhost/polyshop`.
   - Trang quản trị: `http://localhost/polyshop/admin`.

### Cấu trúc thư mục

```
polyshop/
├── assets/                # CSS, JS, hình ảnh
├── includes/              # File cấu hình và kết nối
│   └── config.php        # Cấu hình database
├── models/                # Các file model (connect.php, categories.php, products.php)
├── views/                 # Các file giao diện (HTML/PHP)
├── admin/                 # Thư mục trang quản trị
└── database.sql           # File SQL để tạo database
```

### Một số lưu ý

- Đảm bảo kiểm tra tính tương thích của PHP và MySQL trước khi triển khai.
- Tính năng đặt hàng không bắt buộc, nhưng sinh viên có thể nghiên cứu thêm để mở rộng dự án.
- Sử dụng các thư viện PHP cơ bản như PDO để kết nối cơ sở dữ liệu.
- Đảm bảo giao diện website đồng bộ với thiết kế Figma.

## Hướng dẫn sử dụng

1. **Trang khách hàng**:
   - Xem danh mục sản phẩm.
   - Tìm kiếm sản phẩm.
   - Gửi phản hồi qua form liên hệ.
2. **Trang quản trị**:
   - Đăng nhập bằng tài khoản admin.
   - Quản lý danh mục và sản phẩm (thêm, sửa, xóa).
   - Xem và xử lý phản hồi từ khách hàng.

## Tài liệu tham khảo

- PHP: https://www.php.net/manual/en/
- MySQL: https://dev.mysql.com/doc/
- Figma: https://www.figma.com/
