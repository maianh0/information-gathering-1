# Discovering Subdomains – united.com

**Thực hiện**: Mai Anh  
**Cập nhật lần cuối**: 24/07/2025


## Mục lục

1. [Mục tiêu](#1-mục-tiêu)  
2. [Phương pháp](#2-phương-pháp)  
    - [2.1 Công cụ sử dụng](#21-công-cụ-sử-dụng)  
    - [2.2 Truy vấn thực hiện](#22-truy-vấn-thực-hiện)  
    - [2.3 Mục tiêu tìm kiếm](#23-mục-tiêu-tìm-kiếm)  
3. [Kết quả phát hiện](#3-kết-quả-phát-hiện)  
4. [Kết luận](#4-kết-luận)


## 1. Mục tiêu

Xác định các subdomain (tên miền phụ) thuộc `united.com` nhằm mở rộng phạm vi kiểm thử, phát hiện thêm các tài nguyên tiềm năng có thể bị khai thác và tăng độ bao phủ trong quá trình đánh giá bảo mật.

## 2. Phương pháp

### 2.1 Công cụ sử dụng

- **Google Dorking** – thông qua Google Search
- **Sublist3r** – công cụ Python thu thập subdomain từ nhiều nguồn OSINT

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

---

## 4. Kết luận

Việc kết hợp Google Dorking và Sublist3r giúp phát hiện nhiều subdomain của `united.com`.

