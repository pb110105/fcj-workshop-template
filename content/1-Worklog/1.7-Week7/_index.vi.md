---
title: "Worklog Tuần 7"
date: 2026-11-16
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7

- Tìm hiểu cách đưa pipeline Python lên AWS Lambda.
- Xác định phương án quản lý API key và lập lịch thu thập dữ liệu.
- Chuẩn bị cấu trúc triển khai bằng AWS SAM.

### Các công việc trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu cấu trúc hàm Lambda bằng Python.<br>- Xác định những điểm cần thay đổi khi chuyển script chạy trên máy sang Lambda handler. | 16/11/2026 | 16/11/2026 | [Lambda Handler in Python](https://docs.aws.amazon.com/lambda/latest/dg/python-handler.html) |
| 3 | - Tìm hiểu cách lưu API key bằng Parameter Store SecureString.<br>- Ghi chú cách ứng dụng đọc tham số và tránh đưa API key vào mã nguồn hoặc log. | 17/11/2026 | 17/11/2026 | [Parameter Store SecureString](https://docs.aws.amazon.com/systems-manager/latest/userguide/secure-string-parameter-kms-encryption.html) |
| 4 | - Đọc tài liệu về EventBridge Scheduler.<br>- Xác định phương án kích hoạt pipeline hằng ngày và giữ lịch ở trạng thái tắt trong giai đoạn kiểm thử. | 18/11/2026 | 18/11/2026 | [EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html) |
| 5 | - Tìm hiểu cách Lambda gửi log tới CloudWatch Logs.<br>- Xác định thông tin cần ghi nhận: thời gian chạy, số bản ghi, kết quả kiểm tra và lỗi. | 19/11/2026 | 19/11/2026 | [Lambda Logging with Python](https://docs.aws.amazon.com/lambda/latest/dg/python-logging.html) |
| 6 | - Đọc cấu trúc cơ bản của AWS SAM template.<br>- Tổng hợp danh sách tài nguyên và thông số cần khai báo cho lần triển khai đầu tiên. | 20/11/2026 | 20/11/2026 | [AWS SAM Template Anatomy](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification-template-anatomy.html) |

### Kết quả đạt được tuần 7

- Hiểu vai trò của Lambda handler và hai tham số `event`, `context`.
- Xác định các điểm cần điều chỉnh trong pipeline Python:
  - Thay thao tác nhập API key thủ công bằng đọc tham số được cấp quyền.
  - Thay đường dẫn file trên máy cá nhân bằng phương án lưu trữ phù hợp trên AWS.
  - Trả về kết quả thực thi và ghi log để theo dõi.
- Xác định phương án lưu EIA API key bằng Parameter Store SecureString.
- Hiểu cách EventBridge Scheduler kích hoạt Lambda theo lịch.
- Lập danh sách thông tin cần theo dõi trong CloudWatch Logs.
- Bước đầu nắm được các phần chính của SAM template, gồm `Parameters`, `Globals`, `Resources` và `Outputs`.

### Khó khăn và hướng xử lý

- Pipeline hiện tại sử dụng file cục bộ và nhập API key thủ công, cần điều chỉnh trước khi chạy tự động.
- Dự kiến chuyển từng chức năng sang Lambda và kiểm thử từng bước trước khi bật lịch chạy.

### Trạng thái cuối tuần

Hoàn thiện thêm phương án chuyển pipeline Python lên AWS và chuẩn bị cấu trúc triển khai. Nội dung tuần này tập trung tìm hiểu và thiết kế; chưa ghi nhận triển khai thêm tài nguyên AWS cho project.