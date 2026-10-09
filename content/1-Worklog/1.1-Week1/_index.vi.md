---
title: "Worklog Tuần 1"
date: 2026-10-05
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---


### Mục tiêu tuần 1:

* Tìm hiểu về các công cụ của AWS
* Hiểu dịch vụ AWS cơ bản, cách dùng console & CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   |- Tìm hiểu về quy trình, cách làm việc, vận hành của AWS <br>&emsp; + Tạo tài khoản AWS <br>&emsp; + Thao tác với AWS Budget, AWS Support, AWS IAM, VPC, Subnet | 05/10/2026   | 05/10/2026| <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tiếp tục tìm hiểu các dịch vụ: <br>&emsp; + Tạo Internet Gateway <br>&emsp; + Tạo Route Table <br>&emsp; + Tạo Security Group <br>&emsp; + Kích hoạt Flow Logs <br>&emsp;             | 06/10/2026   | 06/10/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Trển khai EC2 <br> - Kiểm tra kết nối EC2 <br> - Tạo NAT Gateway<br> - Sử dụng Reachability Analyzer <br> - Tạo EC2 kết nối Endpoint<br> - Thực hành System Manager Session Manager<br>| 7/10/2026   | 7/10/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Thiết lập kết nối VPN Site-to-site trong AWS <br>&emsp; + Tạo môi trường VPN <br>&emsp; + ... <br> - Các cách remote SSH vào EC2 <br> - Tìm hiểu Elastic IP   <br>                  | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:** <br>&emsp; + Tạo EC2 instance <br>&emsp; + Kết nối SSH <br>&emsp; + Gắn EBS volume                                                                                         | 15/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 1:

* Đã tạo tài khoản AWS và đăng nhập thành công vào AWS Management Console.
* Đã làm quen với giao diện Console Home và vị trí tìm kiếm dịch vụ.
* Đã tạo Budget
![Đã tạo AWS Budget, email đang chờ xác minh](/images/week1/budget.png)
* Đã thực hành AWS Support, các case hỗ trợ.
![Đã sử dụng AWS Support](/images/week1/support.png)
* Đã thực hành cấp quyền AdministratorAccess trên tài khoản
![Đã thực hành cấp quyền AWS IAM](/images/week1/support.png)
* Đã thực hành với Networking Essentials with Amazon Virtual Private Cloud (VPC)
![Tạo VPC](/images/week1/createVPC.png)
![Tạo Subnet](/images/week1/subnet.png)
![Tạo Internet Gateway](/images/week1/ig.png)
![Tạo Route Table](/images/week1/rt.png)
![Tạo Security Group](/images/week1/sg.png)
![Kích hoạt Flow Logs](/images/week1/flowlog.png)
* Đã thực hành triển khai EC2
![Tạo EC2 Server](/images/week1/ec2.png)
![Kiểm tra kết nối](/images/week1/testConnection.png)
![Tạo NAT Gateway](/images/week1/nat.png)
![Sử dụng Reachability Analyzer](/images/week1/ra.png)
![Tạo EC2 kết nối Endpoint](/images/week1/endpoint.png)
* Thiết lập kết nối VPN Site-to-site trong AWS
  * Tạo môi trường VPN
  
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


