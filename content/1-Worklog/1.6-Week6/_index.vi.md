---
title: "Worklog Tuần 6"
date: 2026-11-09
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6

- Củng cố kiến thức về hạ tầng AWS và cấu hình AWS CLI.
- Tìm hiểu cách lưu trữ dữ liệu và phân quyền cho project pipeline điện năng.
- Rà soát kiến trúc trước khi triển khai.

### Các công việc trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu sự khác nhau giữa AWS Region và Availability Zone.<br>- Rà soát lý do lựa chọn Singapore cho project. | 09/11/2026 | 09/11/2026 | [AWS Regions and Availability Zones](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html) |
| 3 | - Ôn lại cách sử dụng nhiều profile trong AWS CLI.<br>- Tìm hiểu cách chỉ định profile và region khi chạy lệnh. | 10/11/2026 | 10/11/2026 | [AWS CLI Configuration Files](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html) |
| 4 | - Tìm hiểu cách tổ chức dữ liệu bằng prefix trong Amazon S3.<br>- Rà soát cách chia các vùng `raw/`, `clean/` và `quarantine/` cho project. | 11/11/2026 | 11/11/2026 | [Organizing Objects Using Prefixes](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-prefixes.html) |
| 5 | - Đọc tài liệu về execution role của AWS Lambda.<br>- Xác định các quyền Lambda dự kiến cần để ghi dữ liệu S3 và gửi log. | 12/11/2026 | 12/11/2026 | [AWS Lambda Execution Role](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html) |
| 6 | - Rà soát sơ đồ kiến trúc và ghi chú lại vai trò của các dịch vụ.<br>- Tổng hợp các bước cần chuẩn bị trước khi triển khai bằng AWS SAM. | 13/11/2026 | 13/11/2026 | [AWS SAM Developer Guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |

### Kết quả đạt được tuần 6

- Phân biệt được Region và Availability Zone; hiểu cách lựa chọn khu vực triển khai cho project.
- Củng cố cách sử dụng profile và region trong AWS CLI.
- Xác định cách tổ chức dữ liệu S3 theo các vùng:
  - `raw/`: Dữ liệu gốc từ EIA API.
  - `clean/`: Dữ liệu đã kiểm tra và chuẩn hóa.
  - `quarantine/`: Dữ liệu không đạt kiểm tra.
- Hiểu vai trò của Lambda execution role và nguyên tắc cấp quyền theo nhu cầu.
- Rà soát kiến trúc và xác định những phần cần chuẩn bị trước khi triển khai AWS.

### Khó khăn và hướng xử lý

- Cần phân biệt quyền của người triển khai với quyền thực thi của Lambda.
- Tiếp tục đọc tài liệu và lập danh sách quyền cần thiết cho từng thành phần trước khi viết cấu hình hạ tầng.

### Trạng thái cuối tuần

Tập trung củng cố kiến thức và rà soát thiết kế. Chưa ghi nhận triển khai thêm tài nguyên AWS cho project trong tuần này.