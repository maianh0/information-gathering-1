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

---

## 2. Phương pháp

### 2.1 Công cụ sử dụng

- **Google Dorking** – thông qua Google Search


### 2.2 Truy vấn thực hiện

```plaintext
site:*.united.com
```


### 2.3 Mục tiêu tìm kiếm

Tìm kiếm tất cả các subdomain có đuôi `.united.com` đã được Google lập chỉ mục (indexed).


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


## 4. Kết luận

Quá trình dò tìm subdomain bằng Google Dorking đã giúp phát hiện nhiều tên miền phụ thuộc `united.com`. Những subdomain này đại diện cho các dịch vụ khác nhau, từ đặt tour, thuê xe đến theo dõi doanh nghiệp.

