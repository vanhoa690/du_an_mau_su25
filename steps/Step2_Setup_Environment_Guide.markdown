# Hướng dẫn triển khai thực hành dự án PolyShop với PHP

Hướng dẫn này cung cấp các bước chi tiết để sinh viên thiết lập môi trường phát triển, tạo repository trên GitHub, sử dụng GitHub Flow để quản lý mã nguồn, và kết nối cơ sở dữ liệu cho dự án PolyShop sử dụng PHP.

## 1. Cài đặt môi trường phát triển

### 1.1. Cài đặt Laragon hoặc XAMPP
#### **Laragon (Ưu tiên vì nhẹ và dễ sử dụng)**
- **Tải và cài đặt**:
  1. Truy cập https://laragon.org/download/ và tải phiên bản phù hợp (Windows).
  2. Cài đặt Laragon với các tùy chọn mặc định.
  3. Sau khi cài đặt, khởi động Laragon và đảm bảo Apache, MySQL được bật (nút **Start All**).
- **Kiểm tra**:
  - Mở trình duyệt, truy cập `http://localhost`. Nếu thấy trang Laragon, cài đặt thành công.
  - Thư mục gốc của website nằm tại `C:\laragon\www`.

#### **XAMPP (Tùy chọn thay thế)**
- **Tải và cài đặt**:
  1. Truy cập https://www.apachefriends.org/download.html và tải XAMPP cho Windows.
  2. Cài đặt với các thành phần: Apache, MySQL, PHP, phpMyAdmin.
  3. Khởi động XAMPP Control Panel, bật Apache và MySQL.
- **Kiểm tra**:
  - Truy cập `http://localhost` trên trình duyệt. Nếu thấy trang XAMPP, cài đặt thành công.
  - Thư mục gốc của website nằm tại `C:\xampp\htdocs`.

### 1.2. Cài đặt Visual Studio Code (VSCode)
- **Tải và cài đặt**:
  1. Truy cập https://code.visualstudio.com/ và tải phiên bản cho Windows.
  2. Cài đặt VSCode với các tùy chọn mặc định.
- **Cài đặt tiện ích mở rộng (Extensions)**:
  - PHP Intelephense: Hỗ trợ gợi ý và kiểm tra lỗi code PHP.
  - Prettier: Định dạng code HTML/CSS/JavaScript.
  - GitLens: Hỗ trợ quản lý Git trong VSCode.
  - MySQL: Hỗ trợ quản lý cơ sở dữ liệu (tùy chọn).
- **Cấu hình**:
  - Mở VSCode, vào **File > Open Folder** và chọn thư mục dự án (ví dụ: `C:\laragon\www\polyshop` hoặc `C:\xampp\htdocs\polyshop`).

## 2. Tạo repository trên GitHub
- **Tạo tài khoản GitHub**:
  1. Truy cập https://github.com/ và đăng ký tài khoản nếu chưa có.
- **Tạo repository**:
  1. Đăng nhập GitHub, nhấp vào **New Repository**.
  2. Đặt tên repository (ví dụ: `polyshop`).
  3. Chọn **Private** (nếu muốn giới hạn quyền truy cập) hoặc **Public**.
  4. Tích chọn **Add a README file** và **Add .gitignore** (chọn template `PHP`).
  5. Nhấn **Create Repository**.
- **Cài đặt Git**:
  1. Tải và cài đặt Git từ https://git-scm.com/downloads.
  2. Kiểm tra cài đặt: Mở terminal (Command Prompt hoặc VSCode Terminal) và chạy:
     ```bash
     git --version
     ```

## 3. Sử dụng GitHub Flow (1 người - 1 project)
- **Khởi tạo dự án cục bộ**:
  1. Mở terminal trong VSCode (hoặc Command Prompt).
  2. Di chuyển đến thư mục dự án:
     ```bash
     cd C:\laragon\www\polyshop
     ```
  3. Khởi tạo Git:
     ```bash
     git init
     ```
  4. Liên kết với repository GitHub:
     ```bash
     git remote add origin <repository_url>
     ```
     (Thay `<repository_url>` bằng URL từ GitHub, ví dụ: `https://github.com/username/polyshop.git`).
- **Quy trình GitHub Flow**:
  1. **Tạo nhánh mới** cho mỗi tính năng hoặc sửa lỗi:
     ```bash
     git checkout -b feature/<tên-tính-năng>
     ```
     Ví dụ: `git checkout -b feature/add-product-page`.
  2. **Thực hiện thay đổi**:
     - Thêm/sửa file trong thư mục dự án.
     - Kiểm tra trạng thái:
       ```bash
       git status
       ```
     - Thêm các file đã thay đổi:
       ```bash
       git add .
       ```
     - Commit thay đổi:
       ```bash
       git commit -m "Mô tả thay đổi, ví dụ: Thêm trang sản phẩm"
       ```
  3. **Đẩy code lên GitHub**:
     ```bash
     git push origin feature/<tên-tính-năng>
     ```
  4. **Tạo Pull Request (PR)**:
     - Truy cập repository trên GitHub.
     - Nhấp vào **Compare & pull request** cho nhánh vừa đẩy.
     - Mô tả thay đổi trong PR, sau đó nhấp **Create Pull Request**.
     - Merge PR vào nhánh chính (`main` hoặc `master`) sau khi kiểm tra.
  5. **Cập nhật nhánh chính**:
     ```bash
     git checkout main
     git pull origin main
     ```
- **Lưu ý**:
  - Mỗi tính năng nên được thực hiện trên một nhánh riêng.
  - Commit thường xuyên với thông điệp rõ ràng.
  - Kiểm tra code trước khi đẩy lên GitHub.

## 4. Setup môi trường chạy code
- **Tạo thư mục dự án**:
  1. Tạo thư mục `polyshop` trong:
     - Laragon: `C:\laragon\www\polyshop`
     - XAMPP: `C:\xampp\htdocs\polyshop`
  2. Tạo cấu trúc thư mục cơ bản:
     ```
     polyshop/
     ├── assets/           # CSS, JS, hình ảnh
     ├── includes/         # File cấu hình và kết nối
     ├── models/           # File model (connect.php, categories.php, products.php)
     ├── views/            # File giao diện (HTML/PHP)
     ├── admin/            # Trang quản trị
     └── index.php         # Trang chủ
     ```
- **Tạo file kiểm tra PHP**:
  - Trong thư mục `polyshop`, tạo file `index.php`:
    ```php
    <?php
    phpinfo();
    ?>
    ```
  - Truy cập `http://localhost/polyshop` trên trình duyệt. Nếu thấy thông tin PHP, môi trường đã hoạt động.

## 5. Kết nối cơ sở dữ liệu
- **Tạo database**:
  1. Mở phpMyAdmin:
     - Laragon: Truy cập `http://localhost/phpmyadmin`.
     - XAMPP: Truy cập `http://localhost/phpmyadmin`.
  2. Tạo database mới:
     ```sql
     CREATE DATABASE polyshop;
     ```
  3. Tạo các bảng (theo sơ đồ ERD đã thiết kế):
     ```sql
     CREATE TABLE categories (
         category_id INT PRIMARY KEY AUTO_INCREMENT,
         name VARCHAR(100) NOT NULL,
         description TEXT
     );

     CREATE TABLE products (
         product_id INT PRIMARY KEY AUTO_INCREMENT,
         category_id INT,
         name VARCHAR(100) NOT NULL,
         description TEXT,
         price DECIMAL(10,2),
         image VARCHAR(255),
         FOREIGN KEY (category_id) REFERENCES categories(category_id)
     );

     CREATE TABLE feedback (
         feedback_id INT PRIMARY KEY AUTO_INCREMENT,
         product_id INT,
         customer_name VARCHAR(100),
         comment TEXT,
         created_at DATETIME,
         FOREIGN KEY (product_id) REFERENCES products(product_id)
     );

     CREATE TABLE admins (
         admin_id INT PRIMARY KEY AUTO_INCREMENT,
         username VARCHAR(50) NOT NULL,
         password VARCHAR(255) NOT NULL
     );
     ```
- **Tạo file kết nối database**:
  - Trong thư mục `includes`, tạo file `config.php`:
    ```php
    <?php
    define('DB_HOST', 'localhost');
    define('DB_USER', 'root'); // Mặc định Laragon/XAMPP
    define('DB_PASS', '');     // Mặc định không có mật khẩu
    define('DB_NAME', 'polyshop');

    try {
        $conn = new PDO("mysql:host=" . DB_HOST . ";dbname=" . DB_NAME, DB_USER, DB_PASS);
        $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    } catch(PDOException $e) {
        echo "Connection failed: " . $e->getMessage();
    }
    ?>
    ```
- **Kiểm tra kết nối**:
  - Tạo file `test_db.php` trong thư mục `polyshop`:
    ```php
    <?php
    require_once 'includes/config.php';
    echo "Database connected successfully!";
    ?>
    ```
  - Truy cập `http://localhost/polyshop/test_db.php`. Nếu thấy thông báo "Database connected successfully!", kết nối thành công.

## Lưu ý
- Luôn sao lưu mã nguồn và cơ sở dữ liệu trước khi thực hiện thay đổi lớn.
- Đảm bảo .gitignore bao gồm các file nhạy cảm như `config.php` để tránh đẩy thông tin database lên GitHub.
- Kiểm tra định kỳ Apache và MySQL trong Laragon/XAMPP để đảm bảo server đang chạy.

## Tài liệu tham khảo
- Laragon: https://laragon.org/docs/
- XAMPP: https://www.apachefriends.org/docs/
- GitHub Flow: https://guides.github.com/introduction/flow/
- PDO PHP: https://www.php.net/manual/en/book.pdo.php