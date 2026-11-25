---
title: "Worklog Tuần 8"
date: 2026-11-23
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

- Tìm hiểu cách tổ chức dữ liệu sạch phục vụ truy vấn.
- Làm rõ vai trò của AWS Glue Data Catalog và Amazon Athena.
- Chuẩn bị các truy vấn phân tích và kế hoạch kiểm thử trên AWS.

### Các công việc trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu định dạng Parquet và lợi ích khi truy vấn dữ liệu trên S3.<br>- Xác định các trường cần giữ trong dữ liệu sạch của project. | 23/11/2026 | — | [Columnar Storage Formats in Athena](https://docs.aws.amazon.com/athena/latest/ug/columnar-storage.html) |
| 3 | - Tìm hiểu cách phân vùng dữ liệu theo khu vực và ngày.<br>- Phác thảo cấu trúc đường dẫn cho vùng `clean/` trên S3. | 24/11/2026 | — | [Partitioning Data in Athena](https://docs.aws.amazon.com/athena/latest/ug/partitions.html) |
| 4 | - Tìm hiểu vai trò của AWS Glue Data Catalog đối với Athena.<br>- Phác thảo schema bảng dữ liệu điện năng. | 25/11/2026 | — | [AWS Glue Data Catalog](https://docs.aws.amazon.com/glue/latest/dg/catalog-and-crawler.html) |
| 5 | **Kế hoạch:** Tìm hiểu cách viết truy vấn Athena để xác định giờ có nhu cầu điện cao và so sánh nhu cầu thực tế với dự báo. | 26/11/2026 (dự kiến) | — | [Amazon Athena SELECT](https://docs.aws.amazon.com/athena/latest/ug/select.html) |
| 6 | **Kế hoạch:** Tổng hợp các trường hợp cần kiểm thử khi triển khai AWS và rà soát nội dung workshop tương ứng. | 27/11/2026 (dự kiến) | — | [Testing Lambda Functions](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html) |

### Kết quả dự kiến của tuần 8

- Hiểu lợi ích của Parquet trong việc giảm lượng dữ liệu cần quét khi truy vấn.
- Đề xuất cấu trúc phân vùng dữ liệu sạch theo respondent và ngày UTC.
- Xác định schema dữ liệu gồm các trường chính:
  - `period`: Thời điểm ghi nhận dữ liệu.
  - `respondent`: Mã khu vực.
  - `type`: Chỉ số D, DF hoặc NG.
  - `value`: Giá trị điện năng.
  - `value_units`: Đơn vị dữ liệu.
- Phân biệt vai trò của S3, Glue Data Catalog và Athena:
  - **S3:** Lưu dữ liệu.
  - **Glue Data Catalog:** Lưu schema và metadata.
  - **Athena:** Truy vấn dữ liệu.
- Chuẩn bị hướng truy vấn nhu cầu điện cao nhất và sai lệch dự báo.
- Lập danh sách kiểm thử dữ liệu hợp lệ, thiếu, trùng và chạy lại pipeline.

### Khó khăn và hướng xử lý

- Cần thống nhất schema và cấu trúc phân vùng trước khi tạo bảng Athena.
- Dự kiến thử nghiệm với một khoảng dữ liệu nhỏ trước, sau đó mới mở rộng phạm vi.

### Trạng thái trong tuần

Đang chuẩn bị thiết kế dữ liệu và phương án truy vấn trên AWS. Ngày hoàn thành và kết quả sẽ được cập nhật sau khi thực hiện từng công việc.