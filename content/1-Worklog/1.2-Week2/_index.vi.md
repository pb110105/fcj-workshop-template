---
title: "Worklog Tuần 2"
date: 2026-10-12
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Kiểm tra lại hệ thống AWS
* Tìm hiểu các đề tài và lên kế hoạch

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu một số ý tưởng và đề tài project trên AWS.<br>- Đọc tài liệu về triển khai ứng dụng serverless bằng AWS SAM. | 12/10/2026 | 12/10/2026 | [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| 3 | - Tiếp tục khảo sát các đề tài phù hợp.<br>- Tìm hiểu xu hướng năng lượng điện và khả năng sử dụng dữ liệu cho project. | 13/10/2026 | 13/10/2026 | [IEA Electricity 2026](https://www.iea.org/reports/electricity-2026) |
| 4 | - Rà soát các tài nguyên AWS đang hoạt động.<br>- Xác định các tài nguyên không còn sử dụng và phương án dọn dẹp để hạn chế chi phí. | 14/10/2026 | 14/10/2026 | [AWS Free Tier](https://aws.amazon.com/free/) |
| 5 | - Tìm hiểu, so sánh các đề tài về pipeline dữ liệu và xử lý file tự động.<br>- Xác định chức năng chính và các dịch vụ AWS dự kiến sử dụng. | 15/10/2026 | 15/10/2026 | [Amazon Athena](https://docs.aws.amazon.com/athena/latest/ug/what-is.html), [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| 6 | - Chọn hướng dữ liệu năng lượng điện; tìm hiểu EIA Open Data, tài liệu API và Grid Monitor.<br>- Phác thảo kế hoạch thực hiện project và các dịch vụ AWS dự kiến.<br>- Dọn dẹp tài nguyên lab cũ và kiểm tra lượng credit còn lại. | 16/10/2026 | 16/10/2026 | [EIA Open Data](https://www.eia.gov/opendata/), [EIA API](https://www.eia.gov/opendata/documentation.php), [Grid Monitor](https://www.eia.gov/electricity/gridmonitor/) |


### Kết quả đạt được

- Khảo sát và so sánh các hướng đề tài về pipeline dữ liệu, xử lý file tự động, giám sát và sao lưu.
- Lựa chọn hướng project: xây dựng pipeline thu thập, kiểm tra chất lượng và phân tích dữ liệu năng lượng điện từ API trên AWS, kết hợp triển khai tự động.
- Xác định phạm vi chức năng dự kiến: thu thập theo lịch, lưu dữ liệu gốc và dữ liệu sạch, kiểm tra chất lượng, chống trùng, xử lý lỗi, phân tích và giám sát.
- Bước đầu tìm hiểu nguồn dữ liệu EIA Open Data, tài liệu API và Electric Grid Monitor.
- Tìm hiểu vai trò của các dịch vụ AWS dự kiến sử dụng và công cụ AWS SAM cho triển khai bằng mã cấu hình.
- Rà soát chi phí và tài nguyên AWS của các bài lab cũ; dừng 3 EC2, xóa kết nối VPN, NAT Gateway, 3 Interface Endpoint và cấu hình VPC Flow Logs; giải phóng Elastic IP.
- Điều chỉnh thời hạn lưu CloudWatch Logs xuống 1 ngày; giữ lại 3 ổ EBS để bảo toàn dữ liệu và cấu hình lab.
- Phác thảo hướng thực hiện project với ưu tiên kiểm soát chi phí.


