---
title: "Worklog Tuần 4"
date: 2026-10-26
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4

- Rà soát tiến độ và các công việc đã thực hiện.
- Thiết lập IAM user, MFA và profile AWS CLI phục vụ project.
- Chuyển pipeline dữ liệu EIA từ PowerShell sang Python.
- Kiểm thử quy trình thu thập, kiểm tra chất lượng và phân tích dữ liệu.
- Thiết kế sơ đồ kiến trúc giải pháp trên AWS.
- Tìm hiểu và thực hiện các nhiệm vụ nhận AWS credit.

### Các công việc thực hiện trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đọc tài liệu và rà soát các công việc đã thực hiện.<br>- Kiểm tra tiến độ pipeline, tài liệu kiến trúc và các nội dung cần tiếp tục hoàn thiện. | 26/10/2026 | 26/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | - Tạo IAM user `fcaj-project-user`, thêm vào nhóm quản trị và thiết lập MFA.<br>- Đăng nhập AWS CLI bằng profile `fcaj-project`; xác nhận danh tính và region Singapore.<br>- Chuyển các chức năng thu thập, kiểm tra chất lượng và phân tích dữ liệu EIA từ PowerShell sang Python.<br>- Kiểm thử dữ liệu một tuần, một tháng và các trường hợp dữ liệu trùng, thiếu.<br>- Tích hợp các script Python thành pipeline chạy bằng một lệnh; xác nhận pipeline dừng khi không nhập API key.<br>- Cập nhật tài liệu kiến trúc lên GitHub và chuẩn bị commit các script Python. | 27/10/2026 | 27/10/2026 | [AWS CLI Sign-in](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sign-in.html), [EIA API Documentation](https://www.eia.gov/opendata/documentation.php) |
| 4 | - Rà soát và điều chỉnh thiết kế kiến trúc project trên AWS.<br>- Xác định các thành phần chính và mối liên hệ giữa các dịch vụ trong pipeline. | 28/10/2026 | 28/10/2026 | [AWS Architecture Center](https://aws.amazon.com/architecture/) |
| 5 | - Tìm hiểu và thực hiện các nhiệm vụ nhận thêm AWS credit, hướng tới mức tối đa 100 USD theo chương trình.<br>- Theo dõi tiến độ nhiệm vụ trên tài khoản AWS. | 29/10/2026 | 29/10/2026 | [AWS Free Tier](https://aws.amazon.com/free/) |
| 6 | - Xây dựng sơ đồ kiến trúc giải pháp bằng diagrams.net với các biểu tượng dịch vụ AWS.<br>- Thể hiện luồng thu thập dữ liệu EIA, xử lý bằng Lambda, lưu trữ S3 và truy vấn bằng Athena.<br>- Bổ sung các thành phần quản lý API key, mã hóa, lập lịch, giám sát và triển khai hạ tầng.<br>- Rà soát nhãn dịch vụ, hướng kết nối và bố cục sơ đồ; ghi nhận các điểm cần chỉnh sửa trước khi đưa vào báo cáo. | 30/10/2026 | 30/10/2026 | [AWS Architecture Icons](https://aws.amazon.com/architecture/icons/), [diagrams.net](https://app.diagrams.net/) |

### Kết quả đạt được tuần 4

#### 1. Thiết lập danh tính và môi trường AWS CLI

- Tạo IAM user `fcaj-project-user` và thiết lập MFA.
- Đăng nhập AWS Management Console bằng IAM user.
- Thiết lập profile AWS CLI riêng có tên `fcaj-project` bằng `aws login`.
- Xác nhận AWS CLI sử dụng đúng IAM user và region `ap-southeast-1`.
- Sử dụng thông tin đăng nhập tạm thời, không cần tạo Access Key và Secret Key dài hạn cho bước thiết lập này.

#### 2. Chuyển pipeline sang Python

- Xây dựng bốn script:
  - `collect_data.py`: Thu thập dữ liệu từ EIA API.
  - `check_data.py`: Kiểm tra chất lượng dữ liệu.
  - `analyze_data.py`: Phân tích sai lệch giữa nhu cầu điện thực tế và dự báo.
  - `run_pipeline.py`: Điều phối các bước xử lý.
- Sử dụng chung cấu hình JSON và hỗ trợ tham số `--config`.
- Chạy thành công toàn bộ pipeline Python với dữ liệu một tuần bằng một lệnh.
- Lưu dữ liệu và báo cáo Python riêng để thuận tiện đối chiếu với kết quả PowerShell.

#### 3. Kiểm thử và đối chiếu kết quả

| Trường hợp kiểm thử | Kết quả |
| --- | --- |
| Kiểm tra chất lượng dữ liệu một tháng: 2.160 bản ghi | PASS, exit code `0` |
| Kiểm tra chất lượng dữ liệu một tuần: 504 bản ghi | PASS, exit code `0` |
| Thêm một bản ghi trùng | Phát hiện 1 nhóm trùng, FAIL, exit code `1` |
| Loại bỏ một bản ghi | Phát hiện 1 khóa giờ/chỉ số bị thiếu, FAIL, exit code `1` |
| Không nhập EIA API key | Pipeline dừng tại bước thu thập, exit code `1` |
| Chạy pipeline Python với cấu hình một tuần | Thu thập, kiểm tra và phân tích thành công, exit code `0` |

Kết quả phân tích bằng Python khớp với bản PowerShell:

| Phạm vi dữ liệu | Số giờ so sánh D và DF | MAE (MWh) | WAPE |
| --- | ---: | ---: | ---: |
| 01–30/09/2026 | 720 | 2.580,79 | 8,53% |
| 01–07/09/2026 | 168 | 2.567,07 | 8,92% |

Các chỉ số trên đánh giá dự báo có sẵn từ EIA; project chưa xây dựng mô hình dự báo riêng.

#### 4. Thiết kế kiến trúc giải pháp

- Xây dựng bản sơ đồ kiến trúc cho khu vực Singapore.
- Xác định vai trò của các thành phần:
  - **EventBridge Scheduler:** Kích hoạt pipeline theo lịch.
  - **AWS Lambda:** Thu thập, kiểm tra và chuẩn hóa dữ liệu.
  - **Parameter Store và AWS KMS:** Lưu trữ và bảo vệ API key.
  - **Amazon S3:** Lưu dữ liệu gốc, dữ liệu sạch, dữ liệu không đạt kiểm tra và báo cáo.
  - **AWS Glue Data Catalog:** Quản lý schema và metadata.
  - **Amazon Athena:** Truy vấn và phân tích dữ liệu trên S3.
  - **Amazon CloudWatch:** Ghi log, theo dõi và cảnh báo.
  - **AWS SAM/CloudFormation:** Triển khai hạ tầng bằng mã cấu hình.
- Rà soát sơ đồ và xác định các điều chỉnh cần thiết trước khi sử dụng trong báo cáo.
- Cập nhật tài liệu `ARCHITECTURE.md` lên GitHub.

#### 5. Tìm hiểu AWS credit

- Tìm hiểu và thực hiện các nhiệm vụ nhận thêm credit theo chương trình AWS.
- Phân biệt tiến độ hoàn thành nhiệm vụ với số credit thực tế đã được cấp; chưa ghi nhận đã nhận đủ 100 USD.

### Trạng thái cuối tuần

Pipeline Python đã chạy thành công trên máy cá nhân và được kiểm thử với dữ liệu hợp lệ, dữ liệu trùng, dữ liệu thiếu và trường hợp không nhập API key.

Đã thiết lập IAM user, MFA, profile AWS CLI và xây dựng bản sơ đồ kiến trúc giải pháp. Các thành phần xử lý và lưu trữ của project chưa được triển khai lên AWS.