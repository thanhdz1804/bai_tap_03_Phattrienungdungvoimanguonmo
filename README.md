# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421

Lớp: 58KTPM

**Bài tập 03:**  

# SỬ DỤNG WORDPRESS ĐỂ TẠO WEB SITE
## deadline : 23h59 ngày 12 tháng 5 năm 2026.

   
## 1. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ TẠO docker ccompose chứa: 
- Mariadb: sử dụng **image: mariadb:latest** để làm hệ quản trị csdl cho wordpress
- Phpmyadmin: sư dụng **image: phpmyadmin:latest** để đăng nhập vào mariadb rồi tạo csdl trống (chỉ để xem, ko cần tạo bảng từ đây, wordpress sẽ làm hết)
- WordPress: Sử dụng **image: wordpress:latest**, truyền các tham số môi trường cho wordpress là các thông tin truy cập csdl mariadb, tạo bởi Phpmyadmin
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/1c6d97dd-e818-4321-b313-ce6694bd7765" />

## khởi dộng dịch vụ
lệnh :docker-compose up -d
<img width="1910" height="1080" alt="image" src="https://github.com/user-attachments/assets/82886ccc-dabc-421e-a890-dd345c11b43a" />

## Truy cập dịch vụ
<img width="1920" height="1079" alt="image" src="https://github.com/user-attachments/assets/cb7aff3d-bb26-4617-89ce-6aa1f4e53bc5" />

## 2. Yêu cầu: sau khi có 3 service này trong file docker-compose.yml :
- Cấu hình để hệ thống chạy
## a. Sử dụng cloudflare tunnel để public web này lên 1 sub-domain

### 1. Đăng nhập lại Cloudflare
<img width="1920" height="1074" alt="image" src="https://github.com/user-attachments/assets/3ea8220d-a329-4861-a0c3-194ba74fa52d" />

### 2. Tạo tunnel mới
<img width="1918" height="1080" alt="image" src="https://github.com/user-attachments/assets/4de3c2a5-d038-477b-b512-543bc2ff37f7" />

### 3. Tạo config mới
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/320c31d0-ceb1-4e17-9f3e-96a5e16c8a30" />

### 4. Tạo DNS route
<img width="1917" height="1080" alt="image" src="https://github.com/user-attachments/assets/9124b72c-4f24-436c-877f-41516d9b03d6" />

### 5. Vào container WordPress chỉnh sửa file wp-config.php
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e5797de8-6bb8-45b4-9645-9804432e3bf9" />

## Truy cập
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7fe6fe74-2beb-4016-b103-ee9c77b795f8" />

## b. Tạo 1 bài viết trong wordpress giới thiệu về bản thân sinh viên: thông tin cá nhân, sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, ...
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b11e0bfd-d7ce-4805-9694-a7f07d49b854" />

## c. Tạo 1 bài viết trong wordpress giới thiệu về ngành học mà em yêu thích trong trường TNUT. bài viết phải chứa hình ảnh, video, ...
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7a48d253-340b-4093-8921-34ca32b988e6" />

## d. Nhận xét việc sử dụng mã nguồn mở wordpress để tạo website (tốn công sức thế nào, dễ/khó dùng ra sao, tốn kém tài nguyên(ssh/ram) của máy chủ ra sao,....)
Lần đầu em sử dụng WordPress để tạo website nên lúc đầu thấy khá khó, đặc biệt là phần Docker và Cloudflare Tunnel vì em gặp nhiều lỗi như không kết nối được domain, bị redirect localhost và tunnel bị down. Em phải sửa khá nhiều lần mới chạy được 😅
Tuy nhiên sau khi làm xong thì em thấy WordPress khá dễ dùng, giao diện trực quan và tạo bài viết rất nhanh. Chỉ cần vài thao tác là có thể tạo được website cơ bản mà không cần code quá nhiều.
Về tài nguyên máy chủ thì theo em thấy WordPress và MariaDB dùng RAM ở mức vừa phải, Ubuntu vẫn chạy ổn định. Cloudflare Tunnel thì khá nhẹ và tiện vì không cần mở port modem mà vẫn public được website lên Internet.
