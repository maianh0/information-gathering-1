# Discovering Sensitive Files – united.com

**Thực hiện**: Mai Anh  
**Cập nhật lần cuối**: 24/07/2025


## Mục lục

1. [Mục tiêu](#1-mục-tiêu)  
2. [Phương pháp thực hiện](#2-phương-pháp-thực-hiện)  
    - [2.1 Công cụ sử dụng](#21-công-cụ-sử-dụng)  
3. [Phân tích Google Dork](#3-phân-tích-google-dork)  
4. [Phân tích Fuzzing với ffuf, dirsearch và wfuzz](#4-phân-tích-fuzzing-với-ffuf-dirsearch-và-wfuzz)    
5. [Đánh giá bảo mật](#5-đánh-giá-bảo-mật)  
6. [Kết luận](#6-kết-luận)


## 1. Mục tiêu

Xác định xem website `united.com` có vô tình để lộ **các file nhạy cảm** như log, mã nguồn, backup, cấu hình,... ra Internet hay không.


## 2. Phương pháp thực hiện

### 2.1 Công cụ sử dụng

- **Google Dorking** – Tìm kiếm các file bị lập chỉ mục công khai  
- **ffuf** – Fuzz các đường dẫn phổ biến để dò file trực tiếp  
- **dirsearch** – Dò tìm cấu trúc thư mục và file dựa trên danh sách mở rộng  
- **wfuzz** – Fuzz các endpoint hoặc URL để phát hiện file/đường dẫn ẩn  
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


## 4. Phân tích Fuzzing với ffuf, dirsearch và wfuzz

### 4.1 ffuf

```bash
ffuf -u https://united.com/FUZZ -w ~/Desktop/mylist.txt -e .php,.bak,.zip,.env,.log,.sql -mc 200,403 -t 50
```

**Kết quả:**
- **Số truy vấn thực hiện**: 268  
- **Mã phản hồi**: 403 hoặc 404  
- **Kết luận**: Không có file khả nghi được công khai


### 4.2 dirsearch

```bash
python3 dirsearch.py -u https://united.com -e php,env,log,zip
```

**Kết quả nổi bật:**
- Phát hiện nhiều URL trả về mã `302`, bao gồm:
  - `/cgi-bin/.%2E/%2E/.../etc/passwd`
  - `/engine/classes/swfupload/swfupload_f9.swf`
  - `/axis2-web/HappyAxis.jsp`
- Đây là dấu hiệu tiềm năng cho thấy có thể tồn tại lỗ hổng **LFI**, hoặc file cũ không được bảo vệ.

### 4.3 wfuzz

```bash
wfuzz -c -w wordlist.txt --hc 404 https://united.com/FUZZ
```

**Kết quả:**
- Tất cả truy vấn trả về mã `302`, nghĩa là:
  - Các đường dẫn như `/password123`, `/admin123`, `/maianh` đều tồn tại hoặc bị chuyển hướng
- Sử dụng wordlist đơn giản để kiểm tra các endpoint phổ biến (đăng nhập, cấu hình, ...)


## 5. Đánh giá bảo mật

| Tiêu chí                              | Đánh giá         |
|---------------------------------------|------------------|
| File nhạy cảm bị index qua Google     | Không phát hiện  |
| File ẩn qua Fuzzing (ffuf)            | Không phát hiện  |
| Dò file với dirsearch                 | Có endpoint đáng nghi (cần kiểm tra thêm) |
| Fuzz endpoint với wfuzz               | Có phản hồi chuyển hướng (302) cho payload nhạy cảm |
| Cấu hình bảo vệ tài nguyên web        | Tốt              |
| Nguy cơ rò rỉ file từ bên ngoài       | Thấp đến trung bình (nếu không cấu hình lại redirect hợp lý) |

## 6. Kết luận

Tại thời điểm kiểm tra, `united.com` **không để lộ các file nhạy cảm** ra bên ngoài thông qua các phương pháp phổ biến như Google Search hay fuzzing với `ffuf`.

