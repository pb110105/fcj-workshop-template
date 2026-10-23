---
title: "Bản đề xuất"
date: 2026-10-23
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Xây dựng pipeline thu thập, kiểm tra chất lượng và phân tích dữ liệu điện năng trên AWS với triển khai tự động

## 1. Tổng quan dự án

Dự án xây dựng pipeline thu thập dữ liệu điện năng từ EIA Open Data API, kiểm tra chất lượng, lưu trữ và cung cấp dữ liệu phục vụ phân tích. Hệ thống dự kiến sử dụng kiến trúc serverless trên AWS và triển khai hạ tầng bằng AWS Serverless Application Model (AWS SAM).

Phạm vi ban đầu tập trung vào California Independent System Operator (CISO), gồm ba chỉ số theo giờ:

- **D — Demand:** Nhu cầu điện thực tế.
- **DF — Day-ahead demand forecast:** Dự báo nhu cầu điện ngày hôm trước.
- **NG — Net generation:** Sản lượng phát điện ròng.

Thời gian được xử lý theo UTC; đơn vị dữ liệu được giữ theo nguồn EIA là megawatthours (MWh).

## 2. Vấn đề cần giải quyết

Việc gọi API, tải dữ liệu, lưu file và kiểm tra thủ công khó duy trì khi cần cập nhật định kỳ hoặc xử lý nhiều khoảng thời gian. Dữ liệu thiếu mốc giờ, trùng bản ghi hoặc sai định dạng có thể ảnh hưởng đến kết quả phân tích.

Dự án đề xuất xây dựng một quy trình thống nhất để:

- Thu thập dữ liệu theo cấu hình.
- Kiểm tra chất lượng trước khi đưa vào phân tích.
- Lưu riêng dữ liệu gốc, dữ liệu sạch và dữ liệu không đạt.
- Theo dõi trạng thái và lỗi của từng lần chạy.
- Hỗ trợ chạy lại hoặc tải bổ sung dữ liệu lịch sử.
- Tái tạo hạ tầng bằng mã cấu hình.

## 3. Mục tiêu dự án

### 3.1. Mục tiêu kỹ thuật

- Xây dựng tác vụ thu thập dữ liệu từ EIA API, hỗ trợ phân trang, timeout và thử lại có giới hạn.
- Tách các thông số khu vực, chỉ số và thời gian khỏi mã nguồn.
- Kiểm tra trường bắt buộc, kiểu dữ liệu, khóa trùng và tính đầy đủ theo giờ.
- Lưu trữ dữ liệu trên Amazon S3 theo cấu trúc phù hợp cho truy vấn.
- Sử dụng Amazon Athena để phân tích dữ liệu.
- Thiết lập lịch chạy, nhật ký và cảnh báo lỗi.
- Triển khai tài nguyên AWS bằng AWS SAM.

### 3.2. Mục tiêu phân tích

- Xác định các giờ có nhu cầu điện cao.
- So sánh nhu cầu thực tế với dự báo ngày hôm trước.
- Tính sai số dự báo bằng MAE và WAPE.
- Quan sát biến động nhu cầu và sản lượng phát điện ròng theo thời gian.

Dự báo DF được lấy từ EIA, không phải mô hình do dự án tự huấn luyện.

## 4. Phạm vi thực hiện

| Thành phần | Phạm vi |
| --- | --- |
| Nguồn dữ liệu | EIA Open Data API |
| API route | `electricity/rto/region-data/data/` |
| Khu vực ban đầu | CISO |
| Chỉ số | D, DF và NG |
| Độ phân giải | Theo giờ |
| Múi giờ xử lý | UTC |
| Dữ liệu kiểm thử | Tháng 9/2026 và khoảng 01–07/09/2026 |
| Dữ liệu lịch sử dự kiến | Mở rộng tới 12 tháng, thu thập theo từng khoảng nhỏ |
| Cập nhật định kỳ dự kiến | Hằng ngày, có tải lại một khoảng gần nhất để tiếp nhận dữ liệu nguồn điều chỉnh |
| Phương thức triển khai | AWS SAM |

Mốc 12 tháng là phạm vi mở rộng dự kiến, được điều chỉnh sau khi kiểm tra khả năng đáp ứng của API và chi phí thực tế.

Dữ liệu sử dụng là dữ liệu điện năng tổng hợp của Hoa Kỳ, không đại diện cho Việt Nam và không xác định riêng mức tiêu thụ điện của trung tâm dữ liệu AI.

Huấn luyện mô hình dự báo và xử lý dữ liệu streaming theo giây nằm ngoài phạm vi ban đầu.

## 5. Kiến trúc giải pháp dự kiến

Hệ thống dự kiến triển khai tại Region Singapore (`ap-southeast-1`).

| Dịch vụ / Công cụ | Vai trò |
| --- | --- |
| Amazon EventBridge Scheduler | Kích hoạt tác vụ thu thập theo lịch |
| AWS Lambda | Gọi API, kiểm tra và chuẩn hóa dữ liệu |
| Amazon S3 | Lưu dữ liệu gốc, dữ liệu sạch, dữ liệu không đạt và báo cáo |
| AWS Glue Data Catalog | Quản lý metadata bảng phục vụ truy vấn |
| Amazon Athena | Truy vấn và phân tích dữ liệu sạch |
| Amazon CloudWatch | Lưu log, theo dõi chỉ số thực thi và cảnh báo lỗi |
| AWS Systems Manager Parameter Store | Lưu EIA API key dưới dạng SecureString |
| AWS IAM | Phân quyền truy cập theo từng thành phần |
| AWS SAM / AWS CloudFormation | Khai báo và triển khai hạ tầng bằng mã |

Trong phạm vi ban đầu, AWS Glue được sử dụng cho Data Catalog; chưa dự kiến sử dụng Glue ETL jobs.

### Luồng xử lý

1. EventBridge Scheduler kích hoạt tác vụ Lambda theo lịch.
2. Lambda đọc cấu hình và API key, gọi EIA API theo từng trang.
3. Dữ liệu gốc được lưu vào vùng `raw/` trên S3, không lưu API key hoặc URL chứa key.
4. Tác vụ kiểm tra đánh giá cấu trúc, giá trị, khóa và tính đầy đủ.
5. Dữ liệu đạt yêu cầu được chuẩn hóa và lưu vào `clean/`.
6. Dữ liệu không đạt được lưu vào `quarantine/` kèm báo cáo; không được đưa vào tập dữ liệu sạch.
7. Glue Data Catalog mô tả dữ liệu để Athena truy vấn.
8. Kết quả phân tích được lưu vào `reports/` và sử dụng để tạo biểu đồ.
9. CloudWatch ghi nhận trạng thái, số bản ghi và lỗi của từng lần chạy.

Dữ liệu sạch dự kiến được phân vùng theo khu vực và ngày UTC, sử dụng định dạng Parquet để hỗ trợ truy vấn.

Lambda dự kiến truy cập API công khai mà không gắn vào VPC. Kiến trúc ban đầu không cần EC2, NAT Gateway hoặc VPN.

Sơ đồ kiến trúc sử dụng biểu tượng AWS chính thức sẽ được bổ sung sau khi chốt thiết kế.

## 6. Kiểm tra chất lượng dữ liệu

Khóa nghiệp vụ được xác định bằng:

`period + respondent + type`

Các quy tắc kiểm tra gồm:

- Có đầy đủ các trường bắt buộc.
- Giá trị có thể chuyển thành số hữu hạn.
- Khu vực và chỉ số phù hợp với cấu hình.
- Đơn vị đúng với dữ liệu nguồn.
- Thời gian đúng định dạng và nằm trong phạm vi yêu cầu.
- Không trùng khóa nghiệp vụ.
- Đủ từng tổ hợp giờ, khu vực và chỉ số.
- Không xuất hiện tổ hợp ngoài phạm vi.

Dữ liệu thiếu không được tự động thay bằng 0. Khi chạy theo lịch, hệ thống cần xét thời gian công bố của nguồn để phân biệt dữ liệu chưa được cung cấp với lỗi thu thập.

### Xử lý chạy lại

- Giữ dữ liệu gốc theo lần thu thập để đối chiếu.
- Cập nhật dữ liệu sạch theo khóa nghiệp vụ hoặc thay thế phân vùng ngày đã được kiểm tra.
- Không nối thêm dữ liệu một cách không kiểm soát.
- Cho phép tải lại khoảng dữ liệu thất bại hoặc dữ liệu nguồn đã điều chỉnh.

## 7. Phân tích và kết quả đầu ra

### Các câu hỏi phân tích

- Những giờ nào có nhu cầu điện cao nhất?
- Nhu cầu điện thực tế chênh lệch bao nhiêu so với dự báo?
- Sai lệch dự báo thay đổi theo ngày và giờ như thế nào?
- Nhu cầu điện và sản lượng phát điện ròng biến động ra sao?

### Chỉ số phân tích

- **MAE:** Trung bình sai số tuyệt đối giữa nhu cầu thực tế và dự báo.
- **WAPE:** Tổng sai số tuyệt đối chia cho tổng giá trị thực tế tuyệt đối, nhân 100%. Trường hợp mẫu số bằng 0 được xử lý riêng.

Các chỉ số mô tả sai lệch trong dữ liệu được cung cấp, chưa đủ để kết luận nguyên nhân hoặc đánh giá chất lượng dự báo trong mọi điều kiện.

### Sản phẩm bàn giao dự kiến

- Repository mã nguồn và README.
- Cấu hình mẫu cho các khoảng dữ liệu.
- Template AWS SAM.
- Dữ liệu gốc, dữ liệu sạch và báo cáo chất lượng.
- Truy vấn SQL trên Athena.
- Biểu đồ phân tích nhu cầu và sai lệch dự báo.
- Báo cáo kiểm thử.
- Workshop tiếng Việt và tiếng Anh.
- Hướng dẫn triển khai, vận hành và dọn dẹp tài nguyên.

Repository mã nguồn:

[electricity-data-pipeline](https://github.com/pb110105/electricity-data-pipeline)

## 8. Tiến độ hiện tại

### Đã hoàn thành

- Xây dựng pipeline PowerShell gồm thu thập, kiểm tra chất lượng và phân tích.
- Tích hợp các bước vào một lệnh chạy.
- Tạo cấu hình JSON và tham số `-ConfigPath`.
- Kiểm thử thành công với 2.160 bản ghi cho tháng 9/2026.
- Kiểm thử thành công với 504 bản ghi cho khoảng 01–07/09/2026.
- Kiểm chứng khả năng phát hiện bản ghi trùng và bản ghi thiếu.
- Kiểm chứng pipeline dừng khi file cấu hình không tồn tại.
- Xuất báo cáo chất lượng và kết quả so sánh dự báo.
- Quản lý mã nguồn bằng Git, đẩy repository và README lên GitHub.
- Cài đặt AWS CLI và AWS SAM CLI.

### Chưa hoàn thành

- Xác nhận đăng nhập và quyền sử dụng AWS CLI.
- Chuyển logic xử lý sang Python để chạy trên Lambda.
- Bổ sung phân trang và cơ chế thử lại.
- Hoàn thiện sơ đồ và ước tính chi phí.
- Triển khai tài nguyên project lên AWS.
- Thiết lập lịch chạy, truy vấn Athena và giám sát.

## 9. Kế hoạch triển khai

| Giai đoạn | Công việc chính | Điều kiện hoàn thành |
| --- | --- | --- |
| 1. Hoàn thiện thiết kế | Chốt phạm vi, sơ đồ, quyền truy cập và chi phí | Có thiết kế và giả định chi phí rõ ràng |
| 2. Chuẩn bị mã AWS | Chuyển logic sang Python, bổ sung phân trang, timeout và retry | Xử lý được dữ liệu hợp lệ và các trường hợp lỗi |
| 3. Triển khai thử | Viết SAM template, tạo S3, Lambda và tham số bí mật | Một lần thu thập trên AWS hoàn thành và đạt kiểm tra |
| 4. Phân tích và vận hành | Thiết lập Data Catalog, Athena, Scheduler và CloudWatch | Có kết quả truy vấn và kiểm chứng lịch chạy |
| 5. Hoàn thiện báo cáo | Kiểm thử chạy lại, bổ sung biểu đồ, tài liệu và dọn dẹp | Có bằng chứng thực thi và hướng dẫn tái tạo |

Thời lượng dự kiến cho các giai đoạn tiếp theo là 3–4 tuần, điều chỉnh theo kết quả kiểm thử và thời gian thực hiện thực tế.

## 10. Ngân sách và kiểm soát chi phí

Chưa có ước tính AWS Pricing Calculator được xác nhận.

Mục tiêu ngân sách thử nghiệm ban đầu là **10–15 USD**. Đây là giới hạn lập kế hoạch, không phải chi phí đã được tính toán hoặc cam kết.

Trước khi triển khai, cần ước tính tại Region Singapore dựa trên:

- Số lần chạy, bộ nhớ và thời gian thực thi Lambda.
- Dung lượng, số request và thời gian lưu dữ liệu trên S3.
- Lượng dữ liệu Athena quét.
- Chi phí log, giám sát và lưu tham số bí mật.
- Các tài nguyên phát sinh từ quá trình triển khai.

Biện pháp kiểm soát:

- Chỉ bật lịch chạy khi cần.
- Giới hạn khoảng dữ liệu và số lần thử lại.
- Sử dụng phân vùng và Parquet.
- Thiết lập giới hạn quét cho Athena workgroup.
- Cấu hình thời hạn lưu CloudWatch Logs và vòng đời dữ liệu S3.
- Kiểm tra Bills và lượng credit thực tế trước khi triển khai.
- Tắt lịch và dọn tài nguyên sau khi kết thúc thử nghiệm.

Không mặc định Free Tier hoặc credit sẽ chi trả toàn bộ dịch vụ. AWS Budget là công cụ cảnh báo, không tự động dừng mọi tài nguyên.

## 11. Rủi ro và phương án xử lý

| Rủi ro | Phương án dự kiến |
| --- | --- |
| API gián đoạn hoặc giới hạn truy cập | Timeout, retry có giới hạn, backoff và tải lại khoảng thất bại |
| Dữ liệu công bố chậm | Áp dụng khoảng trễ thu thập và kiểm tra lại |
| Dữ liệu nguồn điều chỉnh | Tải lại khoảng gần nhất, giữ dữ liệu gốc để đối chiếu |
| Trùng dữ liệu khi chạy lại | Kiểm soát khóa nghiệp vụ và thay thế phân vùng có kiểm tra |
| Lộ API key | SecureString, quyền IAM giới hạn, không commit key và không log URL chứa key |
| Chi phí vượt dự kiến | Ước tính trước, hạn chế lịch chạy và quét dữ liệu, dọn tài nguyên |

## 12. Tiêu chí nghiệm thu

- Thu thập đầy đủ dữ liệu trong phạm vi cấu hình, có xử lý phân trang.
- Phát hiện được dữ liệu thiếu, trùng và sai định dạng.
- Dữ liệu không đạt không được đưa vào tập sạch.
- Chạy lại không làm tăng số bản ghi trùng.
- Có báo cáo chất lượng và kết quả phân tích.
- Truy vấn được dữ liệu sạch bằng Athena.
- Kiểm chứng tác vụ chạy theo lịch và ghi nhận lỗi.
- Có thể triển khai lại bằng AWS SAM.
- Có hướng dẫn dọn dẹp và kiểm tra chi phí sau thử nghiệm.

## 13. Tài liệu tham khảo

- [EIA Open Data](https://www.eia.gov/opendata/)
- [EIA API Documentation](https://www.eia.gov/opendata/documentation.php)
- [EIA Electric Grid Monitor](https://www.eia.gov/electricity/gridmonitor/)
- [AWS Serverless Application Model](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html)
- [AWS Serverless Data Analytics Pipeline Reference Architecture](https://aws.amazon.com/blogs/big-data/aws-serverless-data-analytics-pipeline-reference-architecture/)
- [AWS Pricing Calculator](https://calculator.aws/)