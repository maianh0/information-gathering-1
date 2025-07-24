
# Discovering Sensitive Files – united.com

## Mục tiêu

**"Discovering Sensitive Files"** nhằm kiểm tra xem website `united.com` có vô tình để lộ các tệp tin nhạy cảm như log, backup, file nén… lên Internet hay không. 

## Phương pháp thực hiện

### Công cụ sử dụng
- Google Dorking

### Truy vấn được sử dụng:
```plaintext
site:united.com ext:log | ext:bak | ext:zip | ext:tar.gz
site:united.com ext:env

Mục tiêu là tìm kiếm các tệp có phần mở rộng phổ biến thường được coi là nhạy cảm, ví dụ:
- `.log` – tệp nhật ký hệ thống
- `.bak` – bản sao lưu
- `.zip`, `.tar.gz` – tệp nén, có thể chứa mã nguồn hoặc thông tin cấu hình
- `.env` – File môi trường, thường chứa thông tin cấu hình, API keys, mật khẩu DB
- `.sql` – File export cơ sở dữ liệu, có thể chứa toàn bộ dữ liệu và cấu trúc DB

```
### Kết quả

> Không tìm thấy tài liệu nào thỏa mãn truy vấn trên Google.

Điều này có nghĩa là:
- `united.com` **không public các file nhạy cảm** dạng `.log`, `.bak`, `.zip`, `.tar.gz`
- hoặc các tệp này đã được **chặn index bởi Google** (qua cấu hình `robots.txt`, `.htaccess`, hoặc chính sách bảo mật nội bộ)


## Đánh giá bảo mật

| Tiêu chí                            | Đánh giá       |
|-------------------------------------|----------------|
| File nhạy cảm bị index công khai    | Không phát hiện |
| Cấu hình index Google               | Tốt          |
| Tiềm năng bị rò rỉ dữ liệu          | Thấp         |

> Việc không phát hiện được tệp tin nhạy cảm là dấu hiệu tích cực, cho thấy `united.com` đang có chính sách bảo mật hợp lý trong việc bảo vệ tài nguyên công khai.


## Kết luận

Tính đến thời điểm kiểm tra, `united.com` **không bị rò rỉ tệp tin nhạy cảm qua Google Search**. Đây là một tín hiệu tích cực cho thấy hệ thống đã có cấu hình bảo mật tốt về mặt dữ liệu công khai.
