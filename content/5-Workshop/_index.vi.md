---
title: "Workshop"
date: 2026-10-23
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Pipeline thu thập, kiểm tra chất lượng và phân tích dữ liệu điện năng trên AWS

## Giới thiệu

Workshop hướng dẫn xây dựng pipeline thu thập dữ liệu từ EIA Open Data API, kiểm tra chất lượng và phân tích dữ liệu điện năng.

Dự án bắt đầu bằng phiên bản PowerShell chạy trên máy cá nhân để kiểm chứng nguồn dữ liệu và logic xử lý. Giai đoạn tiếp theo dự kiến chuyển logic sang Python, triển khai trên AWS bằng AWS SAM và bổ sung lịch chạy tự động.

## Mục tiêu

- Thu thập dữ liệu điện năng theo khu vực, chỉ số và khoảng thời gian.
- Quản lý thông số bằng file cấu hình JSON.
- Kiểm tra chất lượng trước khi phân tích.
- Phát hiện bản ghi trùng, thiếu và giá trị không hợp lệ.
- So sánh nhu cầu thực tế với dự báo ngày hôm trước.
- Chạy các bước thu thập, kiểm tra và phân tích bằng một lệnh.
- Triển khai pipeline trên AWS bằng mã cấu hình.
- Theo dõi thực thi và kiểm soát chi phí.

## Nguồn dữ liệu

Dữ liệu được lấy từ EIA Open Data API:

`electricity/rto/region-data/data/`

Phạm vi ban đầu:

| Thuộc tính | Giá trị |
| --- | --- |
| Khu vực | CISO — California Independent System Operator |
| Tần suất | Theo giờ |
| Múi giờ | UTC |
| Đơn vị nguồn | Megawatthours — MWh |
| D | Nhu cầu điện thực tế |
| DF | Dự báo nhu cầu điện ngày hôm trước |
| NG | Sản lượng phát điện ròng |

DF là dự báo do EIA cung cấp. Workshop chưa xây dựng mô hình dự báo riêng.

## Các phần của workshop

| Phần | Nội dung | Trạng thái |
| --- | --- | --- |
| 1 | Tổng quan, phạm vi và thiết kế giải pháp | Đã xác định phạm vi ban đầu; kiến trúc AWS đang hoàn thiện |
| 2 | Chuẩn bị môi trường và EIA API key | Đã có môi trường PowerShell, Git, Python, AWS CLI và SAM CLI; chưa xác nhận đăng nhập AWS CLI |
| 3 | Thu thập dữ liệu từ EIA API | Đã thực hiện trên máy |
| 4 | Kiểm tra chất lượng dữ liệu | Đã thực hiện trên máy |
| 5 | Phân tích nhu cầu điện và sai lệch dự báo | Đã thực hiện trên máy |
| 6 | Cấu hình và điều phối pipeline | Đã thực hiện trên máy |
| 7 | Triển khai trên AWS bằng SAM | Chưa thực hiện |
| 8 | Lịch chạy, giám sát và truy vấn Athena | Chưa thực hiện |
| 9 | Kiểm thử trên AWS và dọn dẹp tài nguyên | Chưa thực hiện |

Các trang hướng dẫn chi tiết sẽ được cập nhật theo từng phần thực hiện.

## Phiên bản chạy trên máy

### Thành phần

| File | Chức năng |
| --- | --- |
| `collect_data.ps1` | Gọi EIA API, lưu dữ liệu JSON và CSV |
| `check_data.ps1` | Kiểm tra chất lượng và tính đầy đủ |
| `analyze_data.ps1` | So sánh nhu cầu thực tế với dự báo |
| `run_pipeline.ps1` | Chạy các bước theo thứ tự, dừng khi có lỗi |
| `config_week1.json` | Cấu hình dữ liệu một tuần |
| `config_month.json` | Cấu hình dữ liệu một tháng |

### Cách chạy

Thực hiện tại thư mục gốc repository mã nguồn.

**Dữ liệu một tuần:**

    powershell -NoProfile -ExecutionPolicy Bypass -File .\run_pipeline.ps1 -ConfigPath .\config_week1.json

**Dữ liệu một tháng:**

    powershell -NoProfile -ExecutionPolicy Bypass -File .\run_pipeline.ps1 -ConfigPath .\config_month.json

Nhập EIA API key khi được hỏi. Không lưu API key trong mã nguồn hoặc đưa vào GitHub.

## Kiểm tra chất lượng

Khóa nghiệp vụ:

`period + respondent + type`

Các kiểm tra đã triển khai:

- Trường bắt buộc không bị thiếu.
- Giá trị là số hữu hạn.
- Khu vực, chỉ số và đơn vị phù hợp.
- Thời gian nằm trong phạm vi cấu hình.
- Không trùng khóa nghiệp vụ.
- Đủ từng tổ hợp giờ, khu vực và chỉ số.
- Không có tổ hợp ngoài phạm vi.

Kết quả kiểm tra được xuất thành báo cáo JSON.

## Kết quả kiểm thử trên máy

| Phạm vi | Số bản ghi | Số giờ phân tích | Chất lượng | MAE — MWh | WAPE |
| --- | --- | --- | --- | --- | --- |
| 01–30/09/2026 | 2.160 | 720 | PASS | 2.580,79 | 8,53% |
| 01–07/09/2026 | 504 | 168 | PASS | 2.567,07 | 8,92% |

Các chỉ số trên được tính từ dữ liệu tại thời điểm thực hiện. Kết quả có thể thay đổi nếu nguồn EIA điều chỉnh dữ liệu.

### Các trường hợp lỗi đã kiểm chứng

| Trường hợp | Kết quả |
| --- | --- |
| Thêm một bản ghi trùng | Phát hiện một nhóm trùng, trả về FAIL |
| Bỏ một bản ghi | Phát hiện một tổ hợp giờ–chỉ số bị thiếu, trả về FAIL |
| Chọn file cấu hình không tồn tại | Pipeline dừng trước khi thu thập |
| Không nhập API key | Bước thu thập dừng, các bước sau không chạy |

Các lần chạy pipeline hợp lệ kết thúc với exit code `0`. Các trường hợp lỗi được kiểm thử trả về exit code `1`.

## Giai đoạn AWS dự kiến

Các dịch vụ dự kiến sử dụng:

- Amazon EventBridge Scheduler: kích hoạt theo lịch.
- AWS Lambda: thu thập, kiểm tra và chuẩn hóa dữ liệu.
- Amazon S3: lưu dữ liệu gốc, dữ liệu sạch và báo cáo.
- AWS Glue Data Catalog: quản lý metadata bảng.
- Amazon Athena: truy vấn dữ liệu.
- Amazon CloudWatch: log, chỉ số và cảnh báo.
- AWS Systems Manager Parameter Store: lưu API key dạng SecureString.
- AWS IAM: phân quyền truy cập.

Hạ tầng dự kiến được khai báo bằng AWS SAM và triển khai tại Singapore (`ap-southeast-1`).

Phần triển khai AWS chưa hoàn thành. Sơ đồ kiến trúc, ước tính chi phí và bằng chứng thực thi sẽ được bổ sung trong quá trình triển khai.

## Mã nguồn và tài liệu

- [Repository mã nguồn](https://github.com/pb110105/electricity-data-pipeline)
- [EIA Open Data](https://www.eia.gov/opendata/)
- [EIA API Documentation](https://www.eia.gov/opendata/documentation.php)
- [EIA Electric Grid Monitor](https://www.eia.gov/electricity/gridmonitor/)
- [AWS SAM Documentation](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html)