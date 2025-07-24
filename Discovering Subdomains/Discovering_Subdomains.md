
# Discovering Subdomains – united.com

## Mục tiêu

Xác định các subdomain (tên miền phụ) của `united.com` nhằm mở rộng phạm vi kiểm thử và nhận diện thêm các tài nguyên có thể bị tấn công (attack surface).


## Phương pháp

### Công cụ sử dụng
- **Google Dorking** (thông qua Google Search)

### Truy vấn thực hiện:
```plaintext
site:*.united.com
```

### Mục tiêu:
Tìm kiếm tất cả subdomain đã được Google lập chỉ mục (indexed) có đuôi `.united.com`.


## Kết quả phát hiện

| STT | Subdomain                          | Mô tả chức năng                         |
|-----|------------------------------------|------------------------------------------|
| 1   | `cruises.united.com`               | Đặt tour du lịch bằng tàu                |
| 2   | `vacations.united.com`            | Gói nghỉ dưỡng từ United Airlines       |
| 3   | `cars.united.com`                  | Dịch vụ đặt thuê xe                      |
| 4   | `gofly.united.com`                 | Dịch vụ liên quan đến vé máy bay         |
| 5   | `us.hotels.united.com`             | Đặt phòng khách sạn tại Mỹ               |
| 6   | `corporateimpact.united.com`       | Báo cáo tác động doanh nghiệp            |
| 7   | `fly.united.com`                   | Ứng dụng MileagePlus X                  |



## Kết luận

Việc dò subdomain thành công cho thấy `united.com` có nhiều hệ thống phụ trợ khác nhau đang được công khai. Đây là cơ hội để thực hiện kiểm thử bảo mật sâu hơn ở từng nhánh – giúp nâng cao mức độ bao phủ trong đánh giá tổng thể.

