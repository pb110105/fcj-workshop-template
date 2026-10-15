---
title: "Worklog Tuần 1"
date: 2026-10-05
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1

- Làm quen với AWS Management Console và các công cụ quản lý tài nguyên AWS.
- Tìm hiểu các dịch vụ cơ bản về quản lý chi phí, quản lý truy cập và mạng.
- Thực hành xây dựng mạng VPC, triển khai EC2 và thiết lập kết nối VPN Site-to-Site.

### Công việc thực hiện

| Thứ | Nội dung công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| Thứ Hai | Tìm hiểu cách sử dụng AWS Management Console.<br>Tạo tài khoản AWS và tìm hiểu AWS Budgets, AWS Support, IAM, VPC và Subnet. | 05/10/2026 | 05/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Thứ Ba | Tạo Internet Gateway, Route Table và Security Group.<br>Kích hoạt VPC Flow Logs để ghi nhận thông tin lưu lượng mạng. | 06/10/2026 | 06/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| Thứ Tư | Triển khai EC2 và kiểm tra kết nối.<br>Tạo NAT Gateway, sử dụng Reachability Analyzer và EC2 Instance Connect Endpoint.<br>Thực hành truy cập EC2 bằng AWS Systems Manager Session Manager. | 07/10/2026 | 07/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| Thứ Năm | Tạo môi trường VPN và thiết lập kết nối AWS Site-to-Site VPN.<br>Cấu hình Customer Gateway và tùy chỉnh VPN Tunnel. | 08/10/2026 | 08/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| Thứ Sáu | Tìm hiểu cấu hình VPN thay thế và giao thức IKEv2.<br>Nghiên cứu các ý tưởng cho đề tài cá nhân. | 09/10/2026 | 09/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |

### Kết quả đạt được

#### 1. Tài khoản AWS và quản lý chi phí

- Tạo tài khoản AWS và đăng nhập thành công vào AWS Management Console.
- Làm quen với giao diện Console Home và chức năng tìm kiếm dịch vụ.
- Tạo **My Zero-Spend Budget** để theo dõi chi phí.
- Tại thời điểm kiểm tra, Budget hiển thị trạng thái **OK**, chi phí **0 USD**; email nhận thông báo vẫn đang chờ xác minh.
- Gửi AWS Support case về lỗi xác minh email nhận thông báo Budget.

**Minh họa AWS Budget:**

![AWS Budget đã tạo; email nhận thông báo đang chờ xác minh](/fcj-workshop-template/images/week1/budget.png)

**Minh họa AWS Support case:**

![Gửi yêu cầu hỗ trợ đến AWS Support](/fcj-workshop-template/images/week1/support.png)

#### 2. Quản lý truy cập với IAM

- Thực hành cấp quyền bằng policy **AdministratorAccess**.

![Thực hành cấp quyền với AWS IAM](/fcj-workshop-template/images/week1/iam.png)

#### 3. Xây dựng mạng VPC

Thực hành các thành phần mạng trong bài lab **Networking Essentials with Amazon VPC**:

- Tạo VPC và các Subnet.
- Tạo Internet Gateway và gắn vào VPC.
- Cấu hình Route Table.
- Tạo Security Group.
- Kích hoạt VPC Flow Logs.

**Tạo VPC:**

![Tạo VPC](/fcj-workshop-template/images/week1/createVPC.png)

**Tạo Subnet:**

![Tạo Subnet](/fcj-workshop-template/images/week1/subnet.png)

**Tạo Internet Gateway:**

![Tạo Internet Gateway](/fcj-workshop-template/images/week1/ig.png)

**Cấu hình Route Table:**

![Cấu hình Route Table](/fcj-workshop-template/images/week1/route.png)

**Tạo Security Group:**

![Tạo Security Group](/fcj-workshop-template/images/week1/sg.png)

**Kích hoạt VPC Flow Logs:**

![Kích hoạt VPC Flow Logs](/fcj-workshop-template/images/week1/flowlog.png)

#### 4. Triển khai EC2 và kiểm tra kết nối

- Triển khai EC2 Public và EC2 Private.
- Thực hành kết nối SSH và kiểm tra kết nối giữa các máy.
- Tạo NAT Gateway để EC2 Private có thể truy cập Internet.
- Thực hành sử dụng Reachability Analyzer.
- Thực hành truy cập EC2 Private bằng EC2 Instance Connect Endpoint và AWS Systems Manager Session Manager.

**Triển khai EC2:**

![Triển khai EC2](/fcj-workshop-template/images/week1/ec2.png)

**Kiểm tra kết nối:**

![Kiểm tra kết nối EC2](/fcj-workshop-template/images/week1/testConnection.png)

**Tạo NAT Gateway:**

![Tạo NAT Gateway](/fcj-workshop-template/images/week1/nat.png)

**Sử dụng Reachability Analyzer:**

![Sử dụng Reachability Analyzer](/fcj-workshop-template/images/week1/ra.png)

**Truy cập bằng Session Manager:**

![Truy cập EC2 bằng AWS Systems Manager Session Manager](/fcj-workshop-template/images/week1/manager.png)

#### 5. Thiết lập VPN Site-to-Site

- Tạo VPC mô phỏng môi trường on-premises và EC2 làm Customer Gateway.
- Tạo Virtual Private Gateway, Customer Gateway và VPN Connection.
- Cấu hình Libreswan trên máy Customer Gateway.
- Tùy chỉnh VPN Tunnel và tìm hiểu cấu hình IKEv2.

**Tạo môi trường VPN:**

![Tạo VPC cho môi trường VPN](/fcj-workshop-template/images/week1/vpcvpn.png)

![Tạo EC2 làm Customer Gateway](/fcj-workshop-template/images/week1/ec2vpn.png)

**Tạo các thành phần kết nối:**
![Tạo Virtual Private Gateway](/fcj-workshop-template/images/week1/vpg.png)

![Tạo Customer Gateway](/fcj-workshop-template/images/week1/customergateway.png)

![Tạo VPN Connection](/fcj-workshop-template/images/week1/createVPNconnection.png)

**Cấu hình và kiểm tra VPN:**

![Cấu hình Customer Gateway](/fcj-workshop-template/images/week1/customerGatewayConfiguration.png)

![Tùy chỉnh AWS VPN Tunnel](/fcj-workshop-template/images/week1/vpntunnel.png)

![Thực hành cấu hình IKEv2](/fcj-workshop-template/images/week1/ikiev2.png)

### Khó khăn và cách xử lý

| Vấn đề gặp phải | Cách xử lý |
| --- | --- |
| Liên kết xác minh email nhận thông báo Budget hiển thị “Page not found”. | Kiểm tra tài khoản, thử gửi lại email xác minh và gửi AWS Support case. Chưa xác nhận lỗi đã được giải quyết. |
| Kết nối SSH bị “Connection timed out”. | Kiểm tra Security Group và cập nhật nguồn của rule SSH thành địa chỉ My IP hiện tại. |
| EC2 Private không phản hồi ping từ mạng Customer Gateway. | Bổ sung rule ICMP cho nguồn `10.11.0.0/16` trong Security Group của EC2 Private, sau đó kiểm tra lại. |
| Không tìm thấy gói StrongSwan trong kho phần mềm đang sử dụng trên Amazon Linux 2023. | Thực hành IKEv2 bằng Libreswan đã cài đặt; chưa thực hành triển khai StrongSwan. |

### Kiến thức rút ra

- Hiểu vai trò của VPC, Subnet, Route Table, Internet Gateway và NAT Gateway.
- Biết kiểm tra kết nối dựa trên Security Group, cấu hình định tuyến và trạng thái VPN Tunnel.
- Phân biệt các phương thức truy cập EC2: SSH, EC2 Instance Connect Endpoint và Session Manager.
- Hiểu rằng AWS Budget là công cụ cảnh báo chi phí, không tự động dừng toàn bộ tài nguyên.
- Nhận thức được việc bảo vệ khóa SSH và khóa PSK, tránh đưa thông tin bí mật vào báo cáo hoặc repository.