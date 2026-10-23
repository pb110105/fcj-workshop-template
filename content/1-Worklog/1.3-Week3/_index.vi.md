---
title: "Worklog Tuần 3"
date: 2026-10-19
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3

- Khảo sát nguồn dữ liệu điện năng từ EIA Open Data.
- Xây dựng pipeline thu thập, kiểm tra chất lượng và phân tích dữ liệu bằng PowerShell.
- Tách cấu hình để thay đổi phạm vi dữ liệu mà không cần sửa mã nguồn.
- Tìm hiểu kiến trúc serverless và phác thảo phương án triển khai trên AWS.
- Lập dự toán chi phí cho project.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Khảo sát EIA API Dashboard, lựa chọn dữ liệu nhu cầu điện theo giờ của California Independent System Operator (CISO).<br>- Gọi API bằng PowerShell và thu thập 25 bản ghi Demand (D).<br>- Kiểm tra trường bắt buộc, dữ liệu trùng, kiểu dữ liệu số và tính đầy đủ của các mốc giờ.<br>- Tạo và chạy script `check_data.ps1`, xuất báo cáo `data_quality_summary.json`. | 19/10/2026 | 19/10/2026 | [EIA Open Data](https://www.eia.gov/opendata/), [EIA API Documentation](https://www.eia.gov/opendata/documentation.php) |
| 3 | - Xây dựng và kiểm thử pipeline dữ liệu EIA bằng PowerShell trên máy cá nhân.<br>- Thu thập 2.160 bản ghi CISO tháng 9/2026 với ba chỉ số D, DF và NG.<br>- Kiểm tra chất lượng và kiểm thử khả năng phát hiện dữ liệu trùng, thiếu.<br>- Xây dựng script phân tích sai lệch giữa nhu cầu thực tế và dự báo có sẵn của EIA.<br>- Tích hợp các bước vào pipeline chạy bằng một lệnh; hoàn thành với exit code `0`. | 20/10/2026 | 20/10/2026 | [EIA API Documentation](https://www.eia.gov/opendata/documentation.php), [EIA Electric Grid Monitor](https://www.eia.gov/electricity/gridmonitor/) |
| 4 | - Tìm hiểu kiến trúc pipeline phân tích dữ liệu serverless trên AWS và cách kiểm tra chất lượng dữ liệu trong pipeline.<br>- Tham khảo ứng dụng data lake trong phân tích dữ liệu điện năng để định hướng kiến trúc project. | 21/10/2026 | 21/10/2026 | [AWS Serverless Data Analytics Pipeline](https://aws.amazon.com/blogs/big-data/aws-serverless-data-analytics-pipeline-reference-architecture/), [AWS Smart Meter Data Analytics](https://aws.amazon.com/blogs/industries/aws-releases-smart-meter-data-analytics-platform/) |
| 5 | - Sao lưu phiên bản pipeline hiện tại.<br>- Tách thông số thu thập và xử lý dữ liệu sang file cấu hình JSON.<br>- Cập nhật các script thu thập, kiểm tra chất lượng và phân tích để sử dụng chung cấu hình.<br>- Kiểm thử thành công với dữ liệu một tháng và một tuần, xác nhận có thể thay đổi phạm vi thời gian mà không sửa mã nguồn. | 22/10/2026 | 22/10/2026 | [EIA API Documentation](https://www.eia.gov/opendata/documentation.php) |
| 6 | - Tạo cấu hình riêng cho dữ liệu một tuần và một tháng; kiểm thử tham số `-ConfigPath` và trường hợp không tìm thấy file cấu hình.<br>- Đưa mã nguồn và README lên GitHub, thiết lập `.gitignore`.<br>- Cài đặt và kiểm tra phiên bản AWS CLI, AWS SAM CLI.<br>- Phác thảo kiến trúc AWS cho project.<br>- Lập dự toán tại Singapore cho Lambda, S3, Athena, CloudWatch, Glue Data Catalog, EventBridge Scheduler, Parameter Store và KMS.<br>- Xác định giả định về lưu trữ, số lượt chạy, truy vấn và giám sát; lưu link chia sẻ dự toán. | 23/10/2026 | 23/10/2026 | [Repository project](https://github.com/pb110105/electricity-data-pipeline), [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html), [Dự toán AWS](https://calculator.aws/#/estimate?id=b15d336bada5c522a1ed6521fac734952eeb4469) |

### Kết quả đạt được tuần 3

#### Thu thập và kiểm tra chất lượng dữ liệu

- Gọi thành công EIA API và lưu dữ liệu dưới dạng JSON, CSV.
- Thu thập dữ liệu điện năng CISO theo giờ UTC với ba chỉ số:
  - **D — Demand:** Nhu cầu điện thực tế.
  - **DF — Day-ahead demand forecast:** Dự báo nhu cầu điện ngày hôm trước.
  - **NG — Net generation:** Sản lượng điện phát ròng.
- Xây dựng các kiểm tra về trường bắt buộc, khóa trùng, giá trị số hợp lệ, respondent, chỉ số, đơn vị và tính đầy đủ theo giờ.
- Kiểm thử dữ liệu trùng và thiếu; chương trình phát hiện lỗi, trả về trạng thái `FAIL` và exit code `1`.

#### Xây dựng pipeline có thể cấu hình

- Hoàn thiện bốn script:
  - `collect_data.ps1`: Thu thập dữ liệu.
  - `check_data.ps1`: Kiểm tra chất lượng dữ liệu.
  - `analyze_data.ps1`: Phân tích sai lệch dự báo.
  - `run_pipeline.ps1`: Điều phối các bước xử lý.
- Tích hợp toàn bộ quy trình vào một lệnh chạy.
- Pipeline dừng khi một bước thất bại và trả về exit code `0` khi hoàn thành thành công.
- Tách thông số sang cấu hình JSON và hỗ trợ chọn file bằng `-ConfigPath`.
- Kiểm thử thành công với phạm vi một tháng và một tuần mà không cần sửa mã nguồn.

#### Kết quả phân tích

| Phạm vi dữ liệu | Số bản ghi | Số giờ so sánh D và DF | Kiểm tra chất lượng | MAE (MWh) | WAPE |
| --- | ---: | ---: | --- | ---: | ---: |
| 01–30/09/2026 | 2.160 | 720 | PASS | 2.580,79 | 8,53% |
| 01–07/09/2026 | 504 | 168 | PASS | 2.567,07 | 8,92% |

- Xuất bảng so sánh nhu cầu thực tế và dự báo theo giờ.
- Xác định các mốc giờ có sai số tuyệt đối lớn nhất.
- Xuất báo cáo tổng hợp các chỉ số MAE và WAPE.
- Sử dụng dự báo có sẵn từ EIA để đánh giá; chưa xây dựng mô hình dự báo riêng.

#### Chuẩn bị triển khai trên AWS

- Quản lý mã nguồn bằng Git và lưu trên GitHub.
- Thiết lập `.gitignore` để loại trừ dữ liệu đầu ra, bản sao lưu và các file nhạy cảm.
- Cài đặt và kiểm tra phiên bản AWS CLI, AWS SAM CLI.
- Phác thảo kiến trúc serverless và xác định vai trò của các dịch vụ AWS.
- Lập dự toán chi phí khoảng **0,32 USD/tháng**, tương đương **3,84 USD/12 tháng**, theo cấu hình đã nhập và Free Tier được Calculator áp dụng.
- Lưu [đường dẫn dự toán](https://calculator.aws/#/estimate?id=b15d336bada5c522a1ed6521fac734952eeb4469) để tham chiếu trong proposal.

### Trạng thái cuối tuần

Pipeline đã chạy thành công trên máy cá nhân. Kiến trúc AWS và dự toán chi phí đã được chuẩn bị; chưa triển khai tài nguyên AWS cho project.