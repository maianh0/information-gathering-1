# Google Hacking – united.com

## Mục tiêu
Sử dụng kỹ thuật **Google Hacking (Google Dorking)** để phát hiện các tài nguyên công khai hoặc nhạy cảm có thể bị rò rỉ trên domain `united.com` giúp phát hiện:
- File cấu hình bị lộ
- Thư mục hoặc file nhạy cảm bị index bởi Google
- Các trang quản trị hoặc backup bị bỏ quên


## Các truy vấn đã sử dụng

| STT | Truy vấn Google Dork                            | Mục đích tìm kiếm                                   |
|-----|--------------------------------------------------|-----------------------------------------------------|
| 1   | `site:united.com ext:env`                       | Tìm file cấu hình `.env` chứa thông tin nhạy cảm    |
| 2   | `site:united.com ext:sql`                       | Tìm file cơ sở dữ liệu `.sql`                       |
| 3   | `site:united.com inurl:admin`                   | Tìm đường dẫn có chứa `/admin` (trang quản trị)     |
| 4   | `site:united.com intitle:"index of"`            | Tìm thư mục lộ index directory                      |

## Kết quả quan sát được

Tất cả các truy vấn đều **không trả về kết quả nào**.  
> Google phản hồi: **"Không tìm thấy tài liệu nào thỏa mãn"**


## Đánh giá bảo mật

| Yếu tố kiểm tra                        | Kết quả                 |
|----------------------------------------|--------------------------|
| File cấu hình `.env` bị lộ             | Không phát hiện       |
| File cơ sở dữ liệu `.sql` công khai    | Không phát hiện       |
| Trang admin lộ qua đường dẫn           | Không phát hiện       |
| Directory indexing bị bật              | Không phát hiện       |

> Website `united.com` hiện **không bị lộ tài nguyên thông qua Google Search**. Điều này cho thấy họ đã cấu hình khá tốt các biện pháp chặn index (robots.txt, bảo mật thư mục, phân quyền truy cập...).


## Kết luận

Website `united.com` không trả về kết quả nào cho các truy vấn Google Hacking phổ biến. Điều này cho thấy:
- Tài nguyên nhạy cảm không bị Google lập chỉ mục
- Không phát hiện lỗ hổng OSINT ở bước này

