# Premium beef selling system

<p align="center">
  <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="300" alt="Laravel Logo">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Laravel-10.x-red?logo=laravel" alt="Laravel 10">
  <img src="https://img.shields.io/badge/PHP-8.1+-blue?logo=php" alt="PHP 8.1">
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License MIT">
</p>

---

## Giới thiệu

**Premium beef selling system** là ứng dụng web bán hàng trực tuyến được xây dựng bằng **Laravel 10**, phục vụ cho hệ thống cửa hàng **Đông A**. Ứng dụng cung cấp đầy đủ chức năng cho khách hàng mua sắm, quản lý đơn hàng, viết blog, liên hệ, cũng như bảng điều khiển quản trị để quản lý toàn bộ hoạt động của cửa hàng.

---

## Tính năng chính

### 👤 Khách hàng
- Đăng ký, đăng nhập, đăng xuất, xác minh email
- Xem và cập nhật hồ sơ cá nhân, đổi mật khẩu
- Quên mật khẩu / đặt lại mật khẩu qua email
- Duyệt sản phẩm theo danh mục, tìm kiếm, lọc và sắp xếp
- Thêm sản phẩm vào giỏ hàng, cập nhật số lượng, xóa sản phẩm
- Yêu thích sản phẩm (danh sách wishlist)
- Đặt hàng (checkout) và xác nhận đơn hàng qua email
- Xem lịch sử đơn hàng và chi tiết từng đơn

### 📝 Blog & Liên hệ
- Đọc bài viết blog, xem chi tiết bài viết
- Bình luận, chỉnh sửa và xóa bình luận trên bài viết
- Gửi form liên hệ đến cửa hàng

### 🛠️ Quản trị (Admin)
- Đăng nhập riêng cho quản trị viên
- Quản lý **danh mục sản phẩm** (CRUD)
- Quản lý **sản phẩm** với nhiều ảnh (CRUD)
- Quản lý **banner** quảng cáo (CRUD)
- Quản lý **đơn hàng**: xem danh sách, chi tiết, cập nhật trạng thái
- Quản lý **khách hàng** (CRUD)
- Quản lý **người dùng** (CRUD)
- Quản lý **bình luận** (CRUD)
- Quản lý **liên hệ** (xem, xóa)
- Quản lý **bài viết blog** (CRUD)

### 🔌 REST API
- API danh mục sản phẩm (xác thực bằng Laravel Sanctum)
- API đăng nhập
- Tích hợp thanh toán qua **SePay**

---

## Công nghệ sử dụng

| Thành phần    | Công nghệ                  |
|---------------|----------------------------|
| Backend       | Laravel 10, PHP 8.1+       |
| Frontend      | Blade Templates, Vite 4    |
| Xác thực API  | Laravel Sanctum            |
| Database      | MySQL                      |
| Email         | Laravel Mail (SMTP)        |
| Thanh toán    | SePay                      |
| HTTP Client   | Guzzle HTTP                |

---

## Yêu cầu hệ thống

- PHP >= 8.1
- Composer
- Node.js >= 16 & npm
- MySQL >= 5.7 (hoặc MariaDB)
- Máy chủ web: Apache / Nginx (hoặc dùng `php artisan serve`)

---

## Hướng dẫn cài đặt

### 1. Clone dự án

```bash
git clone https://github.com/20222052/Laravel_DongA.git
cd Laravel_DongA
```

### 2. Cài đặt dependencies PHP

```bash
composer install
```

### 3. Cài đặt dependencies JavaScript

```bash
npm install
```

### 4. Tạo file cấu hình môi trường

```bash
cp .env.example .env
php artisan key:generate
```

### 5. Cấu hình cơ sở dữ liệu

Mở file `.env` và chỉnh sửa thông tin kết nối database:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=donga_shop
DB_USERNAME=root
DB_PASSWORD=your_password
```

### 6. Chạy migration và import dữ liệu mẫu

```bash
php artisan migrate
```

Hoặc import trực tiếp file SQL có sẵn trong thư mục gốc dự án:

```bash
mysql -u root -p donga_shop < "on_tap (1).sql"
```

### 7. Cấu hình email (tùy chọn)

```env
MAIL_MAILER=smtp
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=your_email@gmail.com
MAIL_PASSWORD=your_app_password
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=your_email@gmail.com
MAIL_FROM_NAME="DongA Shop"
```

### 8. Build assets frontend

```bash
npm run build
# Hoặc chạy ở chế độ phát triển:
npm run dev
```

### 9. Tạo symbolic link cho storage

```bash
php artisan storage:link
```

### 10. Khởi động server

```bash
php artisan serve
```

Truy cập ứng dụng tại: [http://localhost:8000](http://localhost:8000)

---

## Cấu trúc thư mục chính

```
app/
├── Http/
│   └── Controllers/
│       ├── Admin/          # Controllers quản trị
│       ├── Api/            # Controllers REST API
│       └── ...             # Controllers trang khách hàng
├── Models/                 # Eloquent Models
├── Mail/                   # Lớp gửi email
└── Policies/               # Phân quyền

resources/views/
├── admin/                  # Giao diện quản trị
├── home/                   # Giao diện khách hàng
├── emails/                 # Template email
└── master/                 # Layout chính

routes/
├── web.php                 # Routes web
└── api.php                 # Routes API

database/migrations/        # File migration database
public/                     # Tài nguyên công khai (ảnh, CSS, JS)
```

---

## Tài khoản mặc định

> Sau khi import dữ liệu mẫu từ file SQL:

| Vai trò       | Đường dẫn đăng nhập |
|---------------|----------------------|
| Quản trị viên | `/admin/login`       |
| Khách hàng    | `/account/login`     |

---

## Đóng góp

Mọi đóng góp đều được chào đón! Vui lòng tạo **Issue** hoặc **Pull Request** trên GitHub.

---

## Giấy phép

Dự án được phân phối theo giấy phép [MIT](https://opensource.org/licenses/MIT).
