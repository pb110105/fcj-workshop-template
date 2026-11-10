---
title: "Worklog Tuần 5"
date: 2026-11-02
weight: 1
chapter: false
pre: "<b>1.5.</b>"
---

### Mục tiêu tuần 5:

- Tìm hiểu các dịch vụ AWS phục vụ giám sát, tự động hóa và quản lý tài nguyên trên nền tảng điện toán đám mây.
- Nắm được chức năng và cách sử dụng Amazon EventBridge Scheduler, AWS Lambda và Amazon CloudWatch.
- Tìm hiểu các dịch vụ hỗ trợ quản lý cấu hình, bảo mật và lưu trữ như AWS Systems Manager Parameter Store, AWS Key Management Service (KMS) và Amazon S3.
- Thực hành giám sát hệ thống bằng Amazon CloudWatch thông qua Metrics, Logs, Alarms và Dashboards.
- Tìm hiểu các nguyên tắc bảo mật Access Key, tối ưu hiệu năng, sử dụng tài nguyên hiệu quả và ước tính chi phí trên AWS.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|---|---|---|---|---|
| Thứ Hai | Tìm hiểu các dịch vụ AWS phục vụ tự động hóa và giám sát hệ thống: Amazon EventBridge Scheduler, AWS Lambda và Amazon CloudWatch. | 02/11/2026 | 02/11/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Thứ Ba | Nghiên cứu các dịch vụ hỗ trợ quản lý cấu hình, bảo mật và lưu trữ: AWS Systems Manager Parameter Store, AWS KMS và Amazon S3. | 03/11/2026 | 03/11/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Thứ Tư | Tìm hiểu kiến trúc và chức năng của Amazon CloudWatch. Thực hành theo dõi CloudWatch Metrics và thu thập, kiểm tra dữ liệu bằng CloudWatch Logs. | 04/11/2026 | 04/11/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Thứ Năm | Thực hành cấu hình CloudWatch Alarms, tìm hiểu CloudWatch Dashboards và dọn dẹp các tài nguyên AWS sau khi hoàn thành bài thực hành. | 05/11/2026 | 05/11/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Thứ Sáu | Tìm hiểu các lưu ý khi sử dụng AWS Access Key, cách quản lý và xóa Access Key an toàn. Nghiên cứu Performance Efficiency trong AWS Well-Architected Framework và phương pháp ước tính chi phí AWS. | 06/11/2026 | 06/11/2026 | [AWS Learning Resources](https://www.youtube.com/watch?v=2cRLnzu3kYc) |

### Kết quả đạt được tuần 5:

**1. Tìm hiểu các dịch vụ tự động hóa và giám sát AWS**

- Tìm hiểu Amazon EventBridge Scheduler và cách lên lịch thực hiện tác vụ tự động trên AWS.
- Nắm được khái niệm AWS Lambda và mô hình điện toán Serverless, cho phép thực thi mã nguồn mà không cần trực tiếp quản lý máy chủ.
- Hiểu chức năng của Amazon CloudWatch trong việc giám sát tài nguyên, thu thập dữ liệu và theo dõi hoạt động của hệ thống.
- Nhận biết cách kết hợp EventBridge Scheduler, Lambda và CloudWatch trong các giải pháp tự động hóa và giám sát.

**2. Quản lý cấu hình, bảo mật và lưu trữ**

- Tìm hiểu AWS Systems Manager Parameter Store để quản lý các tham số cấu hình ứng dụng.
- Hiểu vai trò của AWS Key Management Service (KMS) trong quản lý khóa mã hóa và bảo vệ dữ liệu.
- Tìm hiểu Amazon S3 và các khái niệm cơ bản như Bucket, Object và Storage Class.
- Nắm được tầm quan trọng của việc quản lý thông tin nhạy cảm, phân quyền truy cập và bảo mật dữ liệu trên AWS.

**3. Thực hành Amazon CloudWatch Metrics và Logs**

- Làm quen với giao diện quản lý Amazon CloudWatch.
- Tìm hiểu CloudWatch Metrics và cách theo dõi các chỉ số hoạt động của tài nguyên AWS.
- Thực hành kiểm tra và phân tích dữ liệu giám sát thông qua CloudWatch Metrics.
- Tìm hiểu CloudWatch Logs, Log Groups và Log Streams.
- Thực hành xem dữ liệu nhật ký để phục vụ giám sát và xử lý sự cố hệ thống.
- Hiểu sự khác nhau giữa Metrics và Logs trong quá trình giám sát hạ tầng.

**4. Thực hành CloudWatch Alarms và Dashboards**

- Tìm hiểu cách thiết lập CloudWatch Alarms dựa trên các chỉ số giám sát.
- Thực hành cấu hình ngưỡng cảnh báo để theo dõi trạng thái tài nguyên AWS.
- Làm quen với CloudWatch Dashboards và cách trực quan hóa dữ liệu giám sát.
- Hiểu cách sử dụng Dashboard để tổng hợp các chỉ số quan trọng trên cùng một giao diện.
- Thực hiện kiểm tra và dọn dẹp tài nguyên AWS sau khi hoàn thành bài thực hành nhằm hạn chế phát sinh chi phí không cần thiết.

**5. Tìm hiểu bảo mật Access Key và tối ưu kiến trúc AWS**

- Hiểu vai trò của Access Key ID và Secret Access Key trong việc truy cập AWS thông qua công cụ lập trình và AWS CLI.
- Tìm hiểu các rủi ro bảo mật khi lưu trữ Access Key không đúng cách.
- Nắm được các nguyên tắc quản lý Access Key an toàn, bao gồm hạn chế tạo khóa dài hạn, kiểm soát quyền truy cập và xóa khóa không còn sử dụng.
- Tìm hiểu trụ cột Performance Efficiency trong AWS Well-Architected Framework.
- Hiểu sự khác nhau giữa tối ưu hiệu năng và sử dụng tài nguyên hiệu quả.
- Tìm hiểu các yếu tố ảnh hưởng đến chi phí AWS và phương pháp ước tính chi phí khi triển khai dịch vụ.

**6. Kiến thức và kinh nghiệm tích lũy**

- Hiểu rõ hơn vai trò của các dịch vụ giám sát và tự động hóa trong hệ thống AWS Cloud.
- Có kiến thức cơ bản về CloudWatch Metrics, Logs, Alarms và Dashboards.
- Nắm được cách sử dụng các dịch vụ AWS để hỗ trợ quản lý cấu hình, bảo mật và lưu trữ dữ liệu.
- Nâng cao nhận thức về bảo mật thông tin truy cập và quản lý tài nguyên AWS.
- Hiểu được tầm quan trọng của giám sát hệ thống, tối ưu hiệu năng và kiểm soát chi phí trong quá trình vận hành hạ tầng đám mây.
