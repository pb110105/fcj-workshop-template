
---
title: "Worklog Tuần 1"
date: 2026-10-05
weight: 1
chapter: false
pre: "<b>1.1.</b>"
---

### Mục tiêu tuần 1:

- Làm quen với AWS Management Console và các dịch vụ cơ bản của AWS.
- Tìm hiểu về quản lý chi phí, quản lý danh tính và quyền truy cập (IAM), cũng như hệ thống mạng trên AWS.
- Hiểu các thành phần chính của Amazon VPC, bao gồm Subnet, Route Table, Internet Gateway, NAT Gateway và Security Group.
- Thực hành triển khai Amazon EC2 và xử lý các sự cố kết nối mạng.
- Tìm hiểu AWS Site-to-Site VPN và phương thức kết nối an toàn giữa các hệ thống mạng.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|---|---|---|---|---|
| 2 | Làm quen với AWS Management Console. Tạo tài khoản AWS và tìm hiểu AWS Budgets, AWS Support, IAM, VPC và Subnet. | 05/10/2026 | 05/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | Tạo Internet Gateway, cấu hình Route Table và Security Group. Kích hoạt VPC Flow Logs để ghi nhận thông tin lưu lượng mạng. | 06/10/2026 | 06/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| 4 | Triển khai EC2 Public và EC2 Private, cấu hình NAT Gateway, kiểm tra kết nối và tìm hiểu Reachability Analyzer, EC2 Instance Connect Endpoint và Session Manager. | 07/10/2026 | 07/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| 5 | Xây dựng môi trường mạng mô phỏng On-Premises, cấu hình AWS Site-to-Site VPN, Virtual Private Gateway, Customer Gateway và VPN Tunnel. | 08/10/2026 | 08/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| 6 | Tìm hiểu giao thức IKEv2 và các phương án cấu hình VPN. Nghiên cứu ý tưởng cho dự án cá nhân. | 09/10/2026 | 09/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |

### Kết quả đạt được trong tuần 1:

**1. Thiết lập tài khoản AWS và quản lý chi phí**

- Tạo tài khoản AWS và đăng nhập thành công vào AWS Management Console.
- Làm quen với giao diện quản lý và cách tìm kiếm các dịch vụ AWS.
- Tạo ngân sách **My Zero-Spend Budget** để theo dõi chi phí sử dụng tài nguyên.
- Kiểm tra trạng thái ngân sách hiển thị **OK**, với chi phí ghi nhận tại thời điểm kiểm tra là **0 USD**.
- Gửi yêu cầu hỗ trợ đến AWS Support để xử lý sự cố xác minh email nhận thông báo ngân sách.

**2. Quản lý danh tính và quyền truy cập (IAM)**

- Tìm hiểu về IAM User, IAM Role và IAM Policy.
- Thực hành phân quyền thông qua chính sách **AdministratorAccess**.
- Hiểu được vai trò của IAM trong quản lý quyền truy cập và bảo mật tài nguyên AWS.

**3. Xây dựng hệ thống mạng Amazon VPC**

- Tạo VPC và các Public Subnet, Private Subnet.
- Tạo và gắn Internet Gateway vào VPC.
- Cấu hình Route Table để điều hướng lưu lượng mạng.
- Thiết lập Security Group nhằm kiểm soát kết nối đến các tài nguyên.
- Kích hoạt VPC Flow Logs để ghi nhận thông tin lưu lượng mạng.
- Hiểu được vai trò và nguyên lý hoạt động của các thành phần mạng trong AWS.

**4. Triển khai Amazon EC2 và kiểm tra kết nối**

- Khởi tạo các EC2 Instance trong Public Subnet và Private Subnet.
- Thực hành kết nối đến EC2 thông qua giao thức SSH.
- Cấu hình NAT Gateway để cho phép EC2 Private truy cập Internet theo chiều đi ra.
- Sử dụng Reachability Analyzer để kiểm tra và phân tích khả năng kết nối mạng.
- Thực hành truy cập EC2 Private thông qua EC2 Instance Connect Endpoint.
- Tìm hiểu và sử dụng AWS Systems Manager Session Manager để truy cập EC2.
- Khắc phục lỗi **SSH Connection timed out** bằng cách điều chỉnh quy tắc truy cập trong Security Group.

**5. Thiết lập AWS Site-to-Site VPN**

- Xây dựng môi trường mạng mô phỏng hệ thống On-Premises.
- Tạo VPC và EC2 Instance đóng vai trò Customer Gateway.
- Cấu hình Virtual Private Gateway và Customer Gateway.
- Tạo kết nối AWS Site-to-Site VPN.
- Cài đặt và cấu hình Libreswan trên EC2 Customer Gateway.
- Tìm hiểu các tùy chọn cấu hình VPN Tunnel và giao thức IKEv2.
- Thực hành xử lý sự cố kết nối ICMP bằng cách điều chỉnh Security Group.

**6. Kiến thức và kinh nghiệm tích lũy**

- Nắm được kiến thức nền tảng về điện toán đám mây và kiến trúc mạng trên AWS.
- Hiểu cách triển khai và quản lý các tài nguyên cơ bản trong môi trường AWS.
- Nâng cao kỹ năng cấu hình VPC, EC2, NAT Gateway và các thành phần mạng.
- Biết cách kiểm tra và xử lý các sự cố liên quan đến kết nối mạng, định tuyến và Security Group.
- Hiểu tầm quan trọng của việc giám sát chi phí và bảo mật tài nguyên AWS.
- Có thêm kinh nghiệm thực hành về các phương thức truy cập EC2 và cấu hình kết nối VPN.
