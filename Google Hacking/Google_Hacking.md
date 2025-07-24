# Google Hacking – united.com

**Thực hiện**: Mai Anh  
**Cập nhật lần cuối**: 24/07/2025

---

## Mục lục

1. [Mục tiêu](#1-mục-tiêu)  
2. [Phương pháp](#2-phương-pháp)  
    - [2.1 Các truy vấn Google Dork](#21-các-truy-vấn-google-dork)  
3. [Kết quả phân tích](#3-kết-quả-phân-tích)  
4. [Đánh giá bảo mật](#4-đánh-giá-bảo-mật)  
5. [Kết luận](#5-kết-luận)


## 1. Mục tiêu

Sử dụng kỹ thuật **Google Hacking (Google Dorking)** để phát hiện các tài nguyên công khai hoặc nhạy cảm có thể bị rò rỉ trên domain `united.com`.  
Mục tiêu gồm:

- Phát hiện file cấu hình, cơ sở dữ liệu bị lộ
- Phát hiện trang quản trị hoặc backup bị bỏ quên
- Phát hiện thư mục index công khai


## 2. Phương pháp

### 2.1 Các truy vấn Google Dork

| STT | Truy vấn Google Dork                 | Mục đích tìm kiếm                              |
|-----|--------------------------------------|------------------------------------------------|
| 1   | `site:united.com ext:env`           | Tìm file `.env` chứa thông tin cấu hình        |
| 2   | `site:united.com ext:sql`           | Tìm file `.sql` chứa dữ liệu cơ sở             |
| 3   | `site:united.com inurl:admin`       | Tìm trang quản trị có đường dẫn `/admin`       |
| 4   | `site:united.com intitle:"index of"`| Tìm thư mục lộ cấu trúc thư mục (index)         |


## 3. Kết quả phân tích

- **Tất cả truy vấn đều không trả về kết quả**
- Google phản hồi: `Không tìm thấy tài liệu nào thỏa mãn điều kiện tìm kiếm`

> `united.com` dường như đã chặn index cho các tài nguyên quan trọng thông qua cấu hình `robots.txt`, phân quyền truy cập hoặc biện pháp bảo vệ thư mục.


## 4. Đánh giá bảo mật

| Yếu tố kiểm tra                        | Kết quả           |
|----------------------------------------|--------------------|
| File `.env` bị lộ                      | Không phát hiện    |
| File `.sql` công khai                  | Không phát hiện    |
| Trang admin qua đường dẫn `/admin`    | Không phát hiện    |
| Directory indexing                     | Không phát hiện    |


## 5. Kết luận

Website `united.com` **không để lộ các tài nguyên nhạy cảm** qua Google Search.  
Không có chỉ mục `.env`, `.sql`, thư mục mở hay trang quản trị hiển thị công khai.

