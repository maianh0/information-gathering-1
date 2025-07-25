# Discovering Subdomains – united.com

**Thực hiện**: Mai Anh  
**Cập nhật lần cuối**: 25/07/2025


## Mục lục

1. [Mục tiêu](#1-mục-tiêu)  
2. [Phương pháp](#2-phương-pháp)  
    - [2.1 Công cụ sử dụng](#21-công-cụ-sử-dụng)  
    - [2.2 Truy vấn thực hiện](#22-truy-vấn-thực-hiện)  
    - [2.3 Mục tiêu tìm kiếm](#23-mục-tiêu-tìm-kiếm)  
3. [Kết quả phát hiện](#3-kết-quả-phát-hiện)  


## 1. Mục tiêu

Xác định các subdomain (tên miền phụ) thuộc `united.com` nhằm mở rộng phạm vi kiểm thử, phát hiện thêm các tài nguyên tiềm năng có thể bị khai thác và tăng độ bao phủ trong quá trình đánh giá bảo mật.

## 2. Phương pháp

### 2.1 Công cụ sử dụng

- **Google Dorking** – thông qua Google Search
- **Sublist3r** – công cụ Python thu thập subdomain từ nhiều nguồn OSINT
- **dnsenum** - công cụ Perl hỗ trợ dò DNS, subdomain, MX record, brute-force và zone transfer.

### 2.2 Truy vấn thực hiện
- **GoogLe Dorking**
```plaintext
site:*.united.com
```
- **Sublist3r**
> Cài đặt Sublist3r:
```bash
sudo apt install python3-pip
pip3 install -r requirements.txt --break-system-packages
```

> Chạy thu thập subdomain:
```bash
python3 sublist3r.py -d united.com -o subdomains.txt
```
- **Dnsenum**
```bash
dnsenum united.com
```
### 2.3 Mục tiêu tìm kiếm

Tìm kiếm tất cả các subdomain có đuôi `.united.com` đã được Google lập chỉ mục (indexed), đồng thời kết hợp với công cụ Sublist3r để thu thập sâu hơn từ nhiều nguồn.

## 3. Kết quả phát hiện

| STT | Subdomain                          | Mô tả chức năng                         |
|-----|------------------------------------|------------------------------------------|
| 1   | `cruises.united.com`               | Đặt tour du lịch bằng tàu                |
| 2   | `vacations.united.com`             | Gói nghỉ dưỡng từ United Airlines        |
| 3   | `cars.united.com`                  | Dịch vụ đặt thuê xe                      |
| 4   | `gofly.united.com`                 | Dịch vụ liên quan đến vé máy bay         |
| 5   | `us.hotels.united.com`             | Đặt phòng khách sạn tại Mỹ               |
| 6   | `corporateimpact.united.com`       | Báo cáo tác động doanh nghiệp            |
| 7   | `fly.united.com`                   | Ứng dụng MileagePlus X                   |

> *Các subdomain này cho thấy sự phân chia hệ thống theo dịch vụ – có thể chứa các điểm yếu bảo mật riêng biệt.*

Sublist3r phát hiện thêm hơn 30 subdomain khác như:

```
api.prd.aws.united.com
cloud.enews.united.com
notification.united.com
booking.vacations.united.com
wifigroundportal.united.com
...
```

> *Danh sách đầy đủ được lưu trong file `subdomains.txt`. Việc kết hợp nhiều công cụ đã giúp thu được tập subdomain phong phú và chính xác hơn.*

Kết quả nhận được khi dùng Dnsenum
#### 1. Host's Address:
- united.com → **23.207.182.77**

#### 2. Name Servers:
Sử dụng DNS của **Akamai CDN**:
- a18-67.akam.net → 95.101.36.67  
- a11-66.akam.net → 84.53.139.66  
- a5-65.akam.net → 95.100.168.65  
- a10-65.akam.net → 96.7.50.65  
- a26-64.akam.net → 23.74.25.64  

#### 3. Mail Servers (MX):
- mxb-00212602.gslb.pphosted.com → 67.231.145.22  
- mxa-00212602.gslb.pphosted.com → 67.231.145.22  

Cho thấy hệ thống email được quản lý bởi bên thứ ba, có thể là Proofpoint hoặc dịch vụ tương tự.

#### 4. Zone Transfer:
- Tất cả truy vấn AXFR bị từ chối (REFUSED) → Cấu hình DNS an toàn.

#### 5. Một số subdomain và bản ghi:
| Subdomain                  | Loại bản ghi | Trỏ đến |
|----------------------------|---------------|-----------------------------|
| a.united.com               | A             | 3.110.204.15                |
| mail.united.com            | A             | 209.87.119.172              |
| shop.united.com            | A             | 209.87.113.108              |
| www.united.com             | CNAME         | www-cdn.united.com.edgekey.net |
| dev.united.com.edgekey.net | CNAME         | CDN Akamai                  |

#### 6. Class C Netranges:
- 3.110.204.0/24  
- 23.207.182.0/24  
- 161.215.209.0/24
  
 Có thể sử dụng để **quét thêm IP trong cùng mạng**, xác định hệ thống liên quan đến united.com.


