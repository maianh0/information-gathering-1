# Discovering Websites on the Same Server – united.com

## Mục tiêu
Mục tiêu của bước này là kiểm tra xem website `united.com` có vô tình để lộ **các file nhạy cảm** (log, backup, mã nguồn, cấu hình,...) ra Internet không.

## Phương pháp thực hiện

### Công cụ sử dụng:
- **Google Dorking**: Dò tìm file index bởi công cụ tìm kiếm
- **ffuf**: Fuzz các tệp/đường dẫn trực tiếp trên máy chủ
- **Wordlist tự tạo**: Chứa các tên file/thư mục phổ biến

---

## 1. Google Dork – Tìm file nhạy cảm index công khai

### Truy vấn sử dụng:
```plaintext
site:united.com ext:log | ext:bak | ext:zip | ext:tar.gz | ext:env | ext:sql
```

### Kết quả:
- **Không phát hiện** file nào có các định dạng `.log`, `.bak`, `.zip`, `.env`, `.sql`,...
- Google trả về thông báo: `Không tìm thấy tài liệu nào`

> `united.com` có khả năng đã **ẩn hoặc bảo vệ** các tệp tin khỏi bị index công khai.

---

## 2. Fuzzing ẩn file bằng ffuf

### Câu lệnh đã chạy:
```bash
ffuf -u https://united.com/FUZZ -w ~/Desktop/mylist.txt -e .php,.bak,.zip,.env,.log,.sql -mc 200,403 -t 50
```

### Thông tin wordlist sử dụng:
File `mylist.txt` chứa 45 từ khóa phổ biến như:
```
admin
config
backup
database
.env
error_log
index
.htaccess
upload
test
...
```

### Kết quả thực thi:
- **Số truy vấn**: 268
- **Trạng thái phản hồi**: Chỉ trả về mã lỗi 403 hoặc 404
- **Không phát hiện file khả nghi** tồn tại công khai

> Kết quả cho thấy website `united.com` không tiết lộ các file nội bộ thông qua đường dẫn dễ đoán.


## Đánh giá bảo mật

| Tiêu chí                              | Đánh giá         |
|---------------------------------------|------------------|
| File nhạy cảm bị index qua Google     | Không phát hiện |
| File ẩn qua Fuzzing (ffuf)            | Không phát hiện |
| Cấu hình bảo vệ tài nguyên web        | Tốt            |
| Nguy cơ rò rỉ file từ bên ngoài       | Thấp           |


## Kết luận

Tại thời điểm kiểm tra, `united.com` **không để lộ các file nhạy cảm** ra bên ngoài thông qua các công cụ phổ biến như Google Search hay fuzzing với `ffuf`.

Trang web đã có cấu hình bảo mật tốt, ngăn chặn truy cập trái phép vào các tài nguyên nội bộ.
