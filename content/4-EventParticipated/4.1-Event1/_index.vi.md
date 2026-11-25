---
title: "FCAJ Community Day"
date: 2026-10-31
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “FCAJ Community Day”

### Thông tin sự kiện

- **Thời gian:** 09:00–12:00, ngày 31/10/2026 (GMT+7).
- **Địa điểm:** Bitexco Financial Tower, Thành phố Hồ Chí Minh.
- **Vai trò:** Người tham dự.

### Mục đích của sự kiện

- Chia sẻ kinh nghiệm xây dựng, phát triển và vận hành phần mềm.
- Giới thiệu kiến thức về kiến trúc web serverless và xử lý bất đồng bộ trên AWS.
- Chia sẻ định hướng chuẩn bị kiến thức, kỹ năng cho sinh viên trước khi tham gia ngành công nghệ.
- Trao đổi kinh nghiệm thực tập và ứng dụng dịch vụ AWS vào project.
- Khuyến khích sinh viên tham gia cộng đồng và đóng góp cho các dự án mã nguồn mở.

### Danh sách diễn giả

Thinh Nguyen
Henry Duc Bui
Hung Tran
Dao Luong
Khang Duong
Tuan Tran

### Nội dung nổi bật

#### Lessons Learned from Building Software Factories

- Chia sẻ kinh nghiệm xây dựng và tổ chức hoạt động phát triển phần mềm ở quy mô lớn.
- Giới thiệu những khó khăn thường gặp trong quá trình triển khai.
- Đưa ra các bài học thực tế từ đội ngũ đã trực tiếp xây dựng và vận hành.

#### Education

- Chia sẻ góc nhìn của người làm giáo dục về việc chuẩn bị nguồn nhân lực Cloud.
- Đề cập những kiến thức và kỹ năng sinh viên nên chuẩn bị trước khi đi làm.
- Thảo luận về khoảng cách giữa việc học tại trường và yêu cầu thực tế của doanh nghiệp.

#### AWS Lambda Web Functions: Rethinking Serverless Web Architecture

- Giới thiệu khả năng hỗ trợ HTTP trực tiếp và xử lý nhiều request đồng thời trong nội dung trình bày về Lambda.
- Phân tích ảnh hưởng của lớp adapter đến quá trình xử lý request.
- Giới thiệu Active CPU Billing và các yếu tố cần xem xét khi đánh giá chi phí.
- So sánh cách tiếp cận serverless với triển khai ứng dụng bằng Docker trên EC2/ECS thông qua các benchmark được trình bày.

#### Amazon SQS: Building Asynchronous Systems

- Giải thích nhu cầu xử lý bất đồng bộ trong các hệ thống hiện đại.
- Giới thiệu vai trò của Amazon SQS trong việc giảm phụ thuộc giữa các thành phần.
- Chia sẻ các mẫu thiết kế và lưu ý khi triển khai hệ thống sử dụng hàng đợi.

#### My 3-Month AWS Internship Journey

- Chia sẻ hành trình thực tập kéo dài ba tháng.
- Giới thiệu cách ứng dụng các dịch vụ AWS vào một project thực tế.
- Đưa ra kinh nghiệm và lời khuyên dành cho sinh viên chuẩn bị tham gia thực tập.

#### Start & Maintain Consistency with Open Source Contributing

- Giới thiệu cách bắt đầu đóng góp cho một dự án mã nguồn mở.
- Chia sẻ phương pháp duy trì thói quen đóng góp và động lực học tập.
- Phân tích giá trị của việc đóng góp mã nguồn mở đối với kỹ năng và định hướng nghề nghiệp.

### Những gì học được

#### Tư duy xây dựng phần mềm

- Việc phát triển phần mềm cần quan tâm đến quy trình, khả năng phối hợp và vận hành lâu dài.
- Kinh nghiệm từ các hệ thống thực tế giúp nhận diện những vấn đề khó thấy khi chỉ học lý thuyết.
- Lựa chọn công nghệ cần gắn với yêu cầu cụ thể của bài toán.

#### Kiến trúc serverless và xử lý bất đồng bộ

- Khi đánh giá serverless, cần xem xét đồng thời hiệu năng, mô hình xử lý request và chi phí.
- Hàng đợi là một phương án để tách bước tiếp nhận yêu cầu khỏi bước xử lý.
- Xử lý bất đồng bộ cần được cân nhắc theo đặc điểm công việc, thay vì áp dụng cho mọi chức năng.

#### Chuẩn bị cho kỳ thực tập và nghề nghiệp

- Sinh viên cần kết hợp việc đọc tài liệu với thực hành và xây dựng project.
- Việc ghi nhận tiến độ, lỗi gặp phải và kết quả kiểm thử giúp trình bày quá trình học tập rõ ràng hơn.
- Tham gia cộng đồng và đóng góp mã nguồn mở là cơ hội để học cách đọc code, trao đổi và làm việc với người khác.

### Định hướng ứng dụng vào project

#### Đánh giá cách sử dụng AWS Lambda

- Xem xét mức độ phù hợp của Lambda đối với các tác vụ thu thập và xử lý dữ liệu trong project điện năng.
- Đánh giá thời gian thực thi, tài nguyên cần thiết và chi phí trước khi triển khai.

#### Cân nhắc xử lý bất đồng bộ

- Tìm hiểu khả năng sử dụng Amazon SQS nếu project cần tách các bước xử lý độc lập.
- Chỉ bổ sung hàng đợi khi có nhu cầu rõ ràng về điều phối tải, xử lý lỗi hoặc mở rộng hệ thống.

#### Hoàn thiện tài liệu và mã nguồn

- Duy trì mã nguồn trên GitHub với nội dung commit rõ ràng.
- Bổ sung hướng dẫn sử dụng, cấu hình và kiểm thử để người khác có thể hiểu project.
- Tìm hiểu cách đóng góp nhỏ cho mã nguồn mở, bắt đầu từ tài liệu hoặc báo cáo lỗi.

### Trải nghiệm trong sự kiện

Tham gia FCAJ Community Day giúp tôi có thêm góc nhìn về việc học Cloud và xây dựng phần mềm từ những chia sẻ thực tế. Các chủ đề từ serverless, xử lý bất đồng bộ đến kinh nghiệm thực tập cũng giúp tôi liên hệ với quá trình chuẩn bị project cá nhân.

#### Nội dung quan tâm nhất

Tôi quan tâm nhất đến các phiên chia sẻ về AWS Lambda, Amazon SQS và hành trình thực tập ba tháng trên AWS.

Với project pipeline dữ liệu điện năng, nội dung về Lambda giúp tôi có thêm hướng tìm hiểu cách thực thi tác vụ và đánh giá chi phí. Phần Amazon SQS gợi mở cách tách các bước xử lý khi hệ thống có nhu cầu mở rộng, thay vì để mọi chức năng phụ thuộc trực tiếp vào nhau.

Chia sẻ về hành trình thực tập cũng giúp tôi định hướng việc kết hợp học kiến thức, thực hành và hoàn thiện tài liệu cho project.

#### Kết nối và trao đổi

Sự kiện mang lại cơ hội tiếp cận cộng đồng những người cùng quan tâm đến AWS và công nghệ. Thông qua các nội dung chia sẻ, tôi có thêm góc nhìn về những kỹ năng sinh viên cần chuẩn bị và giá trị của việc học hỏi từ kinh nghiệm thực tế.

Tôi cũng quan tâm hơn đến hoạt động mã nguồn mở, đặc biệt là cách bắt đầu từ những đóng góp nhỏ như cải thiện tài liệu hoặc báo cáo lỗi.

#### Bài học rút ra

- **Lựa chọn dịch vụ theo nhu cầu:** Không cần đưa nhiều dịch vụ vào project ngay từ đầu. Mỗi thành phần cần có mục đích rõ ràng và phù hợp với phạm vi triển khai.
- **Quan tâm đến vận hành và chi phí:** Ngoài việc chạy đúng chức năng, hệ thống cần được kiểm thử, theo dõi lỗi và đánh giá chi phí sử dụng.
- **Duy trì tiến độ bằng những việc nhỏ:** Chia project thành từng bước, ghi nhận kết quả và cập nhật tài liệu thường xuyên giúp quá trình thực hiện dễ kiểm soát hơn.
### Một số hình ảnh khi tham gia sự kiện

<!-- ![Check-in tại FCAJ Community Day](/images/events/event1/check-in.jpg) -->

### Tài liệu tham khảo

- Chương trình sự kiện **FCAJ Community Day**, ngày 31/10/2026.
<!-- Bổ sung đường dẫn trang sự kiện hoặc bài đăng chính thức. -->