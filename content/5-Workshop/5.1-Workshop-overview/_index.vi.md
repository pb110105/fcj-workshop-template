---
title: "Tổng quan giải pháp"
date: 2026-10-23
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

## Giới thiệu

Workshop xây dựng pipeline thu thập, kiểm tra chất lượng và phân tích dữ liệu điện năng từ EIA Open Data API.

Phiên bản chạy trên máy cá nhân đã được thực hiện bằng PowerShell. Giai đoạn tiếp theo dự kiến chuyển logic sang Python và triển khai trên AWS bằng AWS SAM.

## Bài toán

Dữ liệu điện năng được cung cấp theo giờ, bao gồm nhu cầu thực tế, dự báo nhu cầu và sản lượng phát điện ròng.

Nếu thu thập và xử lý thủ công, người thực hiện phải lặp lại các thao tác gọi API, lưu file, kiểm tra và tổng hợp kết quả. Dữ liệu thiếu hoặc trùng có thể làm sai lệch phân tích.

Pipeline được xây dựng để thống nhất quy trình:

1. Đọc cấu hình.
2. Thu thập dữ liệu.
3. Kiểm tra chất lượng.
4. Phân tích dữ liệu đạt yêu cầu.
5. Xuất dữ liệu và báo cáo.

Nếu một bước thất bại, pipeline dừng và trả về mã lỗi.

## Phạm vi dữ liệu

| Thuộc tính | Giá trị |
| --- | --- |
| Nguồn | EIA Open Data API |
| API route | `electricity/rto/region-data/data/` |
| Khu vực ban đầu | CISO — California Independent System Operator |
| Tần suất | Theo giờ |
| Múi giờ | UTC |
| Đơn vị | Megawatthours — MWh |
| Khóa nghiệp vụ | `period + respondent + type` |

Các chỉ số sử dụng:

| Mã | Ý nghĩa |
| --- | --- |
| D | Nhu cầu điện thực tế |
| DF | Dự báo nhu cầu điện ngày hôm trước |
| NG | Sản lượng phát điện ròng |

Dữ liệu phản ánh hoạt động điện năng của khu vực CISO tại Hoa Kỳ. Dự báo DF được lấy từ EIA, không phải mô hình do project huấn luyện.

## Phiên bản chạy trên máy

### Các thành phần

| Thành phần | Chức năng |
| --- | --- |
| `collect_data.ps1` | Gọi API và lưu dữ liệu JSON/CSV |
| `check_data.ps1` | Kiểm tra chất lượng và tính đầy đủ |
| `analyze_data.ps1` | So sánh D với DF, tính MAE và WAPE |
| `run_pipeline.ps1` | Điều phối các bước và dừng khi lỗi |
| File cấu hình JSON | Xác định khu vực, chỉ số, thời gian và tiền tố tên file |

Tham số `-ConfigPath` cho phép chọn cấu hình khi chạy mà không cần sửa mã nguồn.

### Kiểm tra chất lượng

- Kiểm tra các trường bắt buộc.
- Kiểm tra giá trị số hữu hạn.
- Kiểm tra khu vực, chỉ số và đơn vị.
- Phát hiện khóa trùng.
- Phát hiện tổ hợp giờ–khu vực–chỉ số bị thiếu.
- Phát hiện dữ liệu ngoài phạm vi.

### Phân tích

- Xác định các giờ có nhu cầu điện cao.
- Ghép nhu cầu thực tế và dự báo theo cùng mốc giờ.
- Tính sai số và sai số tuyệt đối.
- Tổng hợp MAE và WAPE.
- Xuất bảng so sánh CSV và báo cáo JSON.

## Kết quả đã kiểm chứng

| Phạm vi | Bản ghi | Giờ so sánh | Kiểm tra chất lượng |
| --- | --- | --- | --- |
| 01–30/09/2026 | 2.160 | 720 | PASS |
| 01–07/09/2026 | 504 | 168 | PASS |

Các trường hợp lỗi đã kiểm thử gồm dữ liệu trùng, dữ liệu thiếu, không nhập API key và chọn file cấu hình không tồn tại.

Pipeline hợp lệ kết thúc với exit code `0`; các trường hợp lỗi được kiểm thử trả về exit code `1`.

## Thiết kế AWS dự kiến

| Thành phần | Dịch vụ dự kiến |
| --- | --- |
| Kích hoạt theo lịch | Amazon EventBridge Scheduler |
| Thu thập và xử lý | AWS Lambda |
| Lưu trữ dữ liệu | Amazon S3 |
| Metadata bảng | AWS Glue Data Catalog |
| Truy vấn phân tích | Amazon Athena |
| Log và giám sát | Amazon CloudWatch |
| Lưu API key | AWS Systems Manager Parameter Store — SecureString |
| Phân quyền | AWS IAM |
| Triển khai hạ tầng | AWS SAM / AWS CloudFormation |

Dữ liệu trên S3 dự kiến được tổ chức thành các vùng:

- `raw/`: Dữ liệu gốc nhận từ API.
- `clean/`: Dữ liệu đã chuẩn hóa và đạt kiểm tra.
- `quarantine/`: Dữ liệu không đạt, cần kiểm tra lại.
- `reports/`: Báo cáo chất lượng và kết quả phân tích.

Region dự kiến là Singapore (`ap-southeast-1`). Sơ đồ kiến trúc sẽ được bổ sung sau khi chốt thiết kế.

## Trạng thái thực hiện

Đã hoàn thành phiên bản xử lý trên máy và quản lý mã nguồn bằng GitHub.

Phần triển khai AWS, phân trang API, retry có giới hạn, lịch chạy, truy vấn Athena và giám sát chưa được thực hiện.

## Mã nguồn

[Repository electricity-data-pipeline](https://github.com/pb110105/electricity-data-pipeline)