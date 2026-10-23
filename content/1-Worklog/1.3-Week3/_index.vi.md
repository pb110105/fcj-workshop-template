---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 3:

* Kết nối, làm quen với các thành viên trong First Cloud AI Journey.
* Hiểu dịch vụ AWS cơ bản, cách dùng console & CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Kiểm tra nguồn dữ liệu EIA cho đề tài về điện năng <br> - Khảo sát EIA API Dashboard, chọn dữ liệu nhu cầu điện theo giờ của California Independent System Operator <br> - Gọi API thành công bằng PowerShell, lấy 25 bản ghi Demand (D) <br> - Kiểm tra dữ liệu: không thiếu trường bắt buộc, không trùng khóa, không có giá trị sai kiểu số, không thiếu giờ và không có giờ ngoài phạm vi <br> - Tạo và chạy thành công script check_data.ps1, xuất báo cáo data_quality_summary.json.| 19/10/2026  | 19/10/2026      | <https://www.eia.gov/opendata/index.php>
| 3   | - Xây dựng và kiểm thử pipeline dữ liệu EIA bằng PowerShell trên máy cá nhân  <br> - Thu thập 2.160 bản ghi điện năng CISO tháng 9/2026 với ba chỉ số D, DF và NG; kiểm tra chất lượng và xác nhận khả năng phát hiện dữ liệu trùng, thiếu <br> - Xây dựng script phân tích sai lệch dự báo và tích hợp các bước thành pipeline chạy bằng một lệnh, hoàn thành với exit code 0   | 20/10/2026   | 20/10/2026     | <https://www.eia.gov/opendata/index.php> |
| 4   | - Tìm hiểu kiến trúc pipeline phân tích dữ liệu serverless trên AWS và cách kiểm tra chất lượng dữ liệu trong pipeline. <br> - Tham khảo ứng dụng data lake trong phân tích dữ liệu điện năng để định hướng kiến trúc project. | 21/10/2026   | 21/10/2026      | <https://www.eia.gov/opendata/index.php> |
| 5   | - Sao lưu phiên bản pipeline hiện tại <br> - Tách các thông số thu thập và xử lý dữ liệu sang file cấu hình JSON. <br> - Cập nhật các script thu thập <br> - kiểm tra chất lượng và phân tích để sử dụng chung cấu hình <br> - Kiểm thử thành công với dữ liệu một tháng và một tuần, xác nhận có thể thay đổi phạm vi thời gian mà không sửa code    | 22/10/2026   | 22/10/2026      | https://aws.amazon.com/blogs/big-data/build-event-driven-data-quality-pipelines-with-aws-glue-databrew/ |
| 6   | - **Thực hành:** <br>&emsp; + Tạo EC2 instance <br>&emsp; + Kết nối SSH <br>&emsp; + Gắn EBS volume         | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 3:

* Hiểu AWS là gì và nắm được các nhóm dịch vụ cơ bản: 
  * Compute
  * Storage
  * Networking 
  * Database
  * ...

* Đã tạo và cấu hình AWS Free Tier account thành công.

* Làm quen với AWS Management Console và biết cách tìm, truy cập, sử dụng dịch vụ từ giao diện web.

* Cài đặt và cấu hình AWS CLI trên máy tính bao gồm:
  * Access Key
  * Secret Key
  * Region mặc định
  * ...

* Sử dụng AWS CLI để thực hiện các thao tác cơ bản như:

  * Kiểm tra thông tin tài khoản & cấu hình
  * Lấy danh sách region
  * Xem dịch vụ EC2
  * Tạo và quản lý key pair
  * Kiểm tra thông tin dịch vụ đang chạy
  * ...

* Có khả năng kết nối giữa giao diện web và CLI để quản lý tài nguyên AWS song song.
* ...


