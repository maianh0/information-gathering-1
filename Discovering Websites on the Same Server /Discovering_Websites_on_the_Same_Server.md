# Discovering Websites on the Same Server – united.com

## Mục tiêu
Phân tích các website đang được lưu trữ trên cùng một địa chỉ IP với `united.com`. Mục đích là để xác định xem có các hệ thống nào khác liên quan cùng chia sẻ hạ tầng – từ đó mở rộng phạm vi kiểm thử và thu thập thêm mục tiêu tiềm năng.


## Công cụ & nguồn dữ liệu
- **viewdns.info** – Reverse IP Lookup
- **dnslytics.com** – Domain hosting analysis

## Kết quả phân tích

### 1. viewdns.info
- **IP truy vấn**: `184.27.188.102`
- **Kết quả Reverse IP**:  
  - `united.com` là **domain duy nhất** được host trên IP này.
- **Ngày xác nhận**: 2025-07-22

> IP có vẻ được **dành riêng** hoặc là **IP CDN (Content Delivery Network)** của Akamai, dẫn đến ít hoặc không có website nào chia sẻ cùng IP.

### 2. dnslytics.com
- **Domain**: `united.com`
- **Địa chỉ IP phát hiện**: `23.32.214.9`  
  - Thuộc **Akamai Technologies, Inc.**
- **Name Server**: `a5-65.akam.net`
- **MX record** (Mail Server): `mxa-00212602.gslb.pphosted.com`
- **DomainRank**: `69/100`
- **Tổng số domain trên IP**: 1

> Tên miền dường như không chia sẻ hosting với domain nào khác – có thể do sử dụng CDN hoặc cấu hình riêng biệt.


## Phân tích & nhận định

| Yếu tố                         | Kết luận                        |
|--------------------------------|----------------------------------|
| IP chia sẻ hosting             | Không có domain khác được ghi nhận |
| Sử dụng CDN (Akamai)           | Có                           |
| Bảo mật qua phân tách tài nguyên | Ổn định và an toàn             |



## Kết luận
Dựa trên kết quả từ `viewdns.info` và `dnslytics.com`, không phát hiện domain nào khác cùng chia sẻ IP với `united.com`. Điều này cho thấy tên miền đang sử dụng **môi trường hạ tầng riêng biệt** hoặc **CDN cấu hình chuyên biệt**, giúp tăng cường bảo mật và chống phân tích ngược.


