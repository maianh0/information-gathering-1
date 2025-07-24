# Discovering Websites on the Same Server – united.com

**Thực hiện**: Mai Anh  
**Cập nhật lần cuối**: 24/07/2025

---

## Mục lục

1. [Mục tiêu](#1-mục-tiêu)  
2. [Công cụ & Nguồn dữ liệu](#2-công-cụ--nguồn-dữ-liệu)  
3. [Kết quả phân tích](#3-kết-quả-phân-tích)  
    - [3.1 viewdns.info](#31-viewdnsinfo)  
    - [3.2 dnslytics.com](#32-dnslyticscom)  
4. [Phân tích & Nhận định](#4-phân-tích--nhận-định)  
5. [Kết luận](#5-kết-luận)


## 1. Mục tiêu

Phân tích các website đang được lưu trữ trên cùng một địa chỉ IP với `united.com`.  
Mục tiêu là xác định có hệ thống nào khác chia sẻ cùng hạ tầng để mở rộng phạm vi kiểm thử và phát hiện mục tiêu tiềm năng.


## 2. Công cụ & Nguồn dữ liệu

- [viewdns.info](https://viewdns.info/reverseip/) – Reverse IP Lookup  
- [dnslytics.com](https://dnslytics.com/) – Domain hosting analysis


## 3. Kết quả phân tích

### 3.1 viewdns.info

- **IP truy vấn**: `184.27.188.102`  
- **Kết quả Reverse IP**:  
  - `united.com` là **domain duy nhất** được host trên IP này  
- **Ngày xác nhận**: 22/07/2025  

> *IP có thể là IP riêng hoặc thuộc hệ thống CDN (Akamai), hạn chế website đồng sở hữu.*


### 3.2 dnslytics.com

- **Domain**: `united.com`  
- **Địa chỉ IP phát hiện**: `23.32.214.9`  
- **Tổ chức sở hữu IP**: Akamai Technologies, Inc.  
- **Name Server**: `a5-65.akam.net`  
- **MX Record (Mail Server)**: `mxa-00212602.gslb.pphosted.com`  
- **DomainRank**: `69/100`  
- **Tổng số domain trên IP**: `1`  

> *Tên miền hoạt động đơn lẻ trên IP – khả năng sử dụng CDN hoặc cấu hình độc lập.*


## 4. Phân tích & Nhận định

| Yếu tố                           | Nhận xét                          |
|----------------------------------|------------------------------------|
| Số lượng domain trên IP          | Chỉ có `united.com`               |
| Hạ tầng CDN (Akamai)             | Được sử dụng                      |
| Mức độ chia sẻ tài nguyên        | Không chia sẻ                     |
| Mức độ bảo mật & phân tách       | Tốt, khó bị phân tích ngược       |


## 5. Kết luận

Dựa trên các nguồn phân tích từ `viewdns.info` và `dnslytics.com`, không phát hiện bất kỳ domain nào khác cùng chia sẻ IP với `united.com`.  
Tên miền nhiều khả năng đang sử dụng **môi trường CDN chuyên biệt** (Akamai) hoặc **hạ tầng được phân tách riêng biệt**, từ đó tăng cường tính bảo mật và chống bị phân tích ngược trong các cuộc đánh giá bảo mật hoặc thử nghiệm xâm nhập.

