---
title: "FotMob cung cấp cập nhật bóng đá gần như theo thời gian thực cho hàng triệu người dùng nhờ AWS"
date: 2025-03-25
lastmod: 2025-03-25
author: "Emily McKinzie"
categories: ["AWS for Games Blog"]
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

by Emily McKinzie | vào ngày 25 MAR 2025 | trong [Amazon Aurora](https://aws.amazon.com/blogs/gametech/category/database/amazon-aurora/), [Amazon Bedrock](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/), [Amazon CloudFront](https://aws.amazon.com/blogs/gametech/category/networking-content-delivery/amazon-cloudfront/), [Amazon EC2](https://aws.amazon.com/blogs/gametech/category/compute/amazon-ec2/),[Amazon Elastic Kubernetes Service](https://aws.amazon.com/blogs/gametech/category/compute/amazon-kubernetes-service/), [Amazon ElastiCache](https://aws.amazon.com/blogs/gametech/category/database/amazon-elasticache/), [Amazon Machine Learning](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/amazon-machine-learning/), [Amazon Simple Storage Service (S3)](https://aws.amazon.com/blogs/gametech/category/storage/amazon-simple-storage-services-s3/), [Artificial Intelligence](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/), [AWS Lambdak](https://aws.amazon.com/blogs/gametech/category/compute/aws-lambda/),[Compute](https://aws.amazon.com/blogs/gametech/category/compute/), [Database](https://aws.amazon.com/blogs/gametech/category/database/), [Game Development](https://aws.amazon.com/blogs/gametech/category/game-development/), [Games](https://aws.amazon.com/blogs/gametech/category/industries/games/), [Generative AI](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/generative-ai/), [Industries](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/generative-ai/), [Networking & Content Delivery](https://aws.amazon.com/blogs/gametech/category/networking-content-delivery/), [Storage](https://aws.amazon.com/blogs/gametech/category/storage/)


Môn thể thao được xem nhiều nhất thế giới, bóng đá chuyên nghiệp, thu hút lượng người hâm mộ toàn cầu lên đến [năm tỷ](https://publications.fifa.com/en/vision-report-2021/the-football-landscape/) người. Với hàng trăm nghìn cầu thủ thi đấu trên khắp thế giới, môn thể thao này tạo ra một lượng dữ liệu khổng lồ, từ bàn thắng đến cứu thua, kiến tạo, và nhiều hơn thế nữa. Trong thế giới kết nối ngày nay, người hâm mộ muốn truy cập thời gian thực vào tất cả thống kê trận đấu, cầu thủ và đội bóng, thúc đẩy nhu cầu đối với các ứng dụng cập nhật trận đấu như [FotMob](https://www.fotmob.com/). Ứng dụng có hơn 17 triệu người dùng, cung cấp cập nhật theo thời gian thực và tin tức từ 500 giải đấu quốc tế gần như 24/7.

Với hạ tầng được xây dựng trên [Amazon Web Services](https://aws.amazon.com/) (AWS), công ty Na Uy đứng sau ứng dụng có thể mở rộng và đổi mới để liên tục nâng cao trải nghiệm người hâm mộ. Gần đây, đội ngũ đã phát triển hệ thống thông báo đẩy nội bộ giúp cải thiện cập nhật gần như theo thời gian thực cho người dùng và tiết kiệm hơn 130.000 USD mỗi năm.

Khoản tiết kiệm này sẽ đóng vai trò quan trọng trong việc phát triển các tính năng mới, khi tổ chức đặt mục tiêu tăng gấp đôi lượng người dùng trong những năm tới. Nhận thấy cá nhân hóa là chìa khóa của chiến lược tăng trưởng này, đội ngũ FotMob cũng đang thử nghiệm tính năng tóm tắt đội bóng bằng generative AI được xây dựng trên [Amazon Bedrock](https://aws.amazon.com/bedrock/).

## Từ khởi đầu giản dị đến ứng dụng bóng đá hàng đầu

FotMob bắt đầu vào năm 2004 như một dự án đam mê được dẫn dắt bởi hai anh em Christer và Tommy Nordvik. Họ làm việc vào buổi tối và cuối tuần, vừa duy trì công việc toàn thời gian vừa chăm sóc gia đình, để xây dựng công ty từ con số 0. Tuy nhiên, phải đến năm 2008 khi điện thoại thông minh trở nên phổ biến, FotMob mới thực sự cất cánh. Kể từ đó, đội ngũ đã mở rộng dịch vụ để bao gồm các thống kê trận đấu sâu hơn, thông báo cá nhân hóa, và các tóm tắt tin tức đội bóng và trận đấu trên nhiều khu vực.

![Blog Image](/images/logo-blog/bog1.jpg)

“Chúng tôi xây dựng ứng dụng phục vụ mọi kiểu người dùng — từ fan bình thường chỉ muốn xem tỉ số, đến những người đam mê muốn phân tích dữ liệu sâu. Với machine learning, chúng tôi đã biến các thống kê từ nhà cung cấp dữ liệu như Stats Perform thành các hình ảnh dễ hiểu, như biểu đồ động lực trận đấu hoặc hệ thống đánh giá cầu thủ,” nhà sáng lập FotMob Christer Nordvik giải thích. “Hệ thống đánh giá cầu thủ thậm chí còn được một số tuyển trạch viên sử dụng.”

## Nâng cấp hệ thống thông báo đẩy để mở rộng theo lượng người dùng tăng trưởng

Khi FotMob bắt đầu gửi thông báo đẩy cho người dùng, họ sử dụng các nhà cung cấp bên thứ ba. Tuy nhiên, họ nhanh chóng nhận ra rằng các dịch vụ này không thể xử lý lượng thông báo cần gửi và thường bị sập trong giờ cao điểm. Vì vậy, Christer và Tommy đã bắt tay vào xây dựng giải pháp nội bộ và tìm đến AWS.

“Người hâm mộ rất trung thành, nhưng FotMob là dịch vụ thể thao trực tiếp — ứng dụng phải ổn định; downtime là điều không thể,” Christer giải thích. “Nếu có gì đó hỏng hoặc ứng dụng bị tắt trong vài phút, người dùng sẽ chuyển sang nơi khác. Chúng tôi biết AWS có thể mang lại sự yên tâm đó, và điều đó đã đúng.”

Trung bình mỗi tuần, hệ thống của FotMob gửi hơn ba tỷ thông báo đẩy, và chỉ trong một ngày, họ có thể xử lý năm tỷ yêu cầu HTTP mỗi giờ — tương đương 1,6 triệu yêu cầu mỗi giây. Với hạ tầng được AWS hỗ trợ, FotMob có thể phân phối thông báo gần như tức thì trên toàn cầu, ngay cả trong thời điểm cao điểm. [Amazon Simple Storage Service](https://aws.amazon.com/s3/) (S3) và [Amazon Aurora](https://aws.amazon.com/rds/aurora/) giúp lưu trữ dữ liệu trận đấu và highlight theo mô hình đa vùng. [Amazon Elastic Cloud Compute](https://aws.amazon.com/ec2/) (EC2) xử lý và phân phối cập nhật theo thời gian thực, trong khi [Amazon Elastic Kubernetes Service](https://aws.amazon.com/eks/) (EKS) và [Amazon ElastiCache](https://aws.amazon.com/pm/elasticache/) hỗ trợ phân phối thông báo đẩy.

FotMob cũng sử dụng Amazon CloudFront để đảm bảo phân phối nhanh nội dung tĩnh cho người dùng, AWS Lambda cho API mở rộng linh hoạt, và AWS Cloud Development Kit (AWS CDK) để triển khai hạ tầng bằng mã. Christer chia sẻ thêm: “Nhờ AWS, chúng tôi không bị vướng vào các thách thức hạ tầng, vì thế chúng tôi đổi mới nhanh hơn để mang đến tính năng mà người hâm mộ quan tâm. Người dùng nhận được cập nhật nhanh, đáng tin cậy và không bị gián đoạn.”

## Định hướng tương lai

Với tầm nhìn mở rộng lượng người dùng lên 30 triệu, FotMob hiểu rằng cá nhân hóa sẽ là chìa khóa. Họ gần đây đã thử nghiệm generative AI thông qua Amazon Bedrock để tạo tóm tắt tin tức và đội bóng được cá nhân hóa hơn, cùng với các báo cáo trận đấu sinh động hơn cho người hâm mộ.

Cho đến nay, FotMob đã thử nghiệm nhiều mô hình ngôn ngữ lớn, trong đó [Claude của Anthropic](https://aws.amazon.com/bedrock/claude/) cho kết quả tối ưu nhất về chi phí và chất lượng. Với mô hình này, FotMob đã triển khai tính năng tóm tắt đội bóng bằng tiếng Anh và đang có kế hoạch mở rộng thêm ngôn ngữ trong tương lai.

“Amazon Bedrock mang lại cho chúng tôi một nền tảng linh hoạt và có khả năng mở rộng để cung cấp các bản tóm tắt được AI tạo ra mà người dùng mong muốn,” Christer nói. “Nó tích hợp mượt mà với các dịch vụ AWS hiện có và cho phép chúng tôi thử nghiệm mô hình nhanh chóng để đảm bảo độ chính xác và giảm chi phí.”

Ông tin rằng việc FotMob tập trung vào trải nghiệm người dùng và đổi mới chính là điểm khác biệt so với các ứng dụng thể thao khác, và AWS là yếu tố quan trọng giúp duy trì lợi thế này. Christer kết luận: “Một trong những lợi ích lớn nhất của AWS là chúng tôi có mọi thứ từ một nhà cung cấp. Khi khám phá công nghệ mới, chúng tôi thường xem AWS trước vì dễ dàng có mọi thứ ở một nơi.”

[Download FotMob](https://www.fotmob.com/download) để xem công nghệ AWS hoạt động trong thực tế và trải nghiệm cập nhật bóng đá gần như theo thời gian thực. [Khám phá cách](https://aws.amazon.com/gametech/?trk=77f9e342-cda0-4c48-a2dd-0879fd1617ff&sc_channel=ps&ef_id=CjwKCAiA2cu9BhBhEiwAft6IxGqfN6ek5iPMXBv8s2m0UX_X8XjE6oXDTg-Qq7XEYcXtAKozlWKkwxoCNqUQAvD_BwE:G:s&s_kwcid=AL!4422!3!719304002286!e!!g!!aws%20for%20games!21865058392!169751941436&gbraid=0AAAAADjHtp-IHIvIfr6qxfxTz2YWg6xik&gclid=CjwKCAiA2cu9BhBhEiwAft6IxGqfN6ek5iPMXBv8s2m0UX_X8XjE6oXDTg-Qq7XEYcXtAKozlWKkwxoCNqUQAvD_BwE) bạn có thể xây dựng, vận hành và phát triển ứng dụng với AWS hoặc [liên hệ đội ngũ AWS for Games](https://pages.awscloud.com/Amazon-Game-Tech-Contact-Us.html) để biết thêm thông tin.

## Tài liệu tham khảo

[- Bundesliga powered by AWS  ](https://aws.amazon.com/sports/bundesliga/?did=cr_card&trk=cr_card)

[- NFL on AWS](https://aws.amazon.com/sports/nfl/?did=cr_card&trk=cr_card)

[- Cách DAZN sử dụng AWS Step Functions để điều phối phát video theo sự kiện](https://aws.amazon.com/blogs/media/how-dazn-uses-aws-step-functions-to-orchestrate-event-based-video-streaming-at-scale/)

[- Hudl mở rộng xử lý video và tăng độ tin cậy bằng việc tối ưu hóa trên Amazon EC2 Spot Instances](https://aws.amazon.com/solutions/case-studies/hudl-spot/)

  
![Blog Image](/images/logo-blog/blog1.1.png)


Source:  
https://aws.amazon.com/blogs/gametech/fotmob-delivers-near-real-time-football-updates-to-millions-of-fans-with-aws/
