# Discovering Sensitive Files – united.com

**Thực hiện**: Mai Anh  
**Cập nhật lần cuối**: 24/07/2025


## Mục lục

1. [Mục tiêu](#1-mục-tiêu)  
2. [Phương pháp thực hiện](#2-phương-pháp-thực-hiện)  
    - [2.1 Công cụ sử dụng](#21-công-cụ-sử-dụng)  
3. [Phân tích Google Dork](#3-phân-tích-google-dork)  
4. [Phân tích Fuzzing với ffuf](#4-phân-tích-fuzzing-với-ffuf)  
5. [Đánh giá bảo mật](#5-đánh-giá-bảo-mật)  
6. [Kết luận](#6-kết-luận)


## 1. Mục tiêu

Xác định xem website `united.com` có vô tình để lộ **các file nhạy cảm** như log, mã nguồn, backup, cấu hình,... ra Internet hay không.


## 2. Phương pháp thực hiện

### 2.1 Công cụ sử dụng

- **Google Dorking** – Tìm kiếm các file bị lập chỉ mục công khai  
- **ffuf** – Fuzz các đường dẫn phổ biến để dò file trực tiếp  
- **Wordlist tự tạo** – Danh sách 45 tên file và thư mục phổ biến như:  
  `admin`, `config`, `backup`, `database`, `.env`, `error_log`, `.htaccess`, `upload`, `test`, ...


## 3. Phân tích Google Dork

### Truy vấn thực hiện

```plaintext
site:united.com ext:log | ext:bak | ext:zip | ext:tar.gz | ext:env | ext:sql
```

### Kết quả

- Không phát hiện file `.log`, `.bak`, `.zip`, `.env`, `.sql`, v.v.
- Google trả về thông báo: *Không tìm thấy tài liệu nào*

> `united.com` có khả năng đã ẩn hoặc cấu hình chặn index cho các tệp tin nhạy cảm.


## 4. Phân tích Fuzzing với ffuf

### Câu lệnh thực thi

```bash
ffuf -u https://united.com/FUZZ -w ~/Desktop/mylist.txt -e .php,.bak,.zip,.env,.log,.sql -mc 200,403 -t 50
```

### Kết quả

- **Số truy vấn thực hiện**: 268  
- **Mã trạng thái phản hồi**: Chỉ có 403 (forbidden) hoặc 404 (not found)  
- **Không có file khả nghi** hoặc tài nguyên công khai bị lộ

> Fuzzing không phát hiện tài nguyên nội bộ bị lộ qua các tên file phổ biến.


## 5. Đánh giá bảo mật

| Tiêu chí                              | Đánh giá         |
|---------------------------------------|------------------|
| File nhạy cảm bị index qua Google     | Không phát hiện  |
| File ẩn qua Fuzzing (ffuf)            | Không phát hiện  |
| Cấu hình bảo vệ tài nguyên web        | Tốt              |
| Nguy cơ rò rỉ file từ bên ngoài       | Thấp             |


## 6. Kết luận

Tại thời điểm kiểm tra, `united.com` **không để lộ các file nhạy cảm** ra bên ngoài thông qua các phương pháp phổ biến như Google Search hay fuzzing với `ffuf`.

> 🔐 Trang web đã cấu hình bảo mật tốt để ngăn chặn truy cập trái phép vào các tài nguyên nhạy cảm.

