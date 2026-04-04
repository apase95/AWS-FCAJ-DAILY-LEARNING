---
title: "Những thuật ngữ mới"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Ở đây sẽ lưu lại một số thuật ngữ mới trong AWS hay trong lập trình mà mình chưa nắm rõ.

- DC (Data Center): Là nơi lưu trữ máy chủ của AWS, được tối ưu hóa để cho ra hiệu năng tốt nhất
- AZ (Availability Zone): 1AZ gồm 1DC/nDC. Các AZ được thiết kế (độc lập khi gặp lỗi, liên kết khi bình thường). Giữa 2AZ có các đường kết nối riêng tốc độ cao
- R (Region): 1R/(>=3)AZ. Các Region được kết nối với nhau qua mạng backbone. Các dữ liệu/dịch vụ giữa các Region là độc lập với nhau
- Edge Locations (POP): Là mạng lưới cung cấp các dịch vụ mạng biên (CloudFront CDN, WAF, Route 53 DNF)
- CloudFront CDN: Content Delivery Network, caching data những dữ liệu thường xuyên được truy cập -> người dùng truy cập nhanh hơn
- WAF (Web Application Firewall): Lớp bảo vệ website, hạn chế DDOS
- Route 53: Tạo Domain, gắn certificate cho domain
- Serverless: Những dịch vụ không có máy chủ (tạo database, thiết kế API,...)
- AWS Budget: Dịch vụ theo dõi/quản lý chi phí sử dụng các dịch vụ của AWS

- Amazon VPC (Virtual Private Cloud): Một vùng không gian riêng cho phép bạn khởi chạy các tài nguyên AWS vào 1 mạng ảo xác định
    - VPC nằm trong 1 Region, bắt buộc phải có CIDR IPv4 khi tạo VPC
    - Giới hạn 5VPC/1Region/1Account
    - Mục đích: Tách các môi trường (Production/Dev/Test/Staging)
    - VPC cho phép tạo nhiều mạng ảo, chia các mạng ảo thành nhiều mạng con -> Subnet
    - VPC Subnet: Nằm trong 1AZ cụ thể, CIDR Subnet là mạng con của CIDR VPC

- Route table: Bảng tập hợp các Route, để xác định đường đi cho mạng
    - Khi tạo VPC sẽ có 1 Default Route table (là Route cho phép tất cả Subnet trong cùng VPC kết nối với nhau) (DRT không thể xóa)
    - Route table được gán vào subnet
    - Có thể tạo Custom Route table

- ENI (Elastic Network Interface): Là card mạng ảo, được duy trì khi chuyển đổi server (IP Private, Elastic IP, MAC)
- EIP (Elastic IP Address): Là một địa chỉ IPv4 tĩnh, có thể liên kết với ENI

- VPC Endpoint: Giúp kết nối các tài nguyên trong VPC đến Services thông qua AWS PrivateLink (không cần kết nối qua Internet)
    - Interface Endpoint: Dùng ENI trong VPC và IP Private để kết nối tới Services
    - Gateway Endpoint: Dùng Route table để định tuyến đường truyền đến Services (DynamoDB & S3)

- Internet Gateway: Là một thành phần của VPC, cho phép các EC2 Instance trong VPC có thể truyền ra ngoài Internet, được quản lý bởi AWS
- NAT Gateway: Cho phép các EC2 Instance trong Subnet truy cập tới Internet/Services. Chỉ cho phép đi ra, không cho phép di vào

- Sercurity Group (SG): Là một tường lửa ảo có trạng thái "Stateful" giúp kiểm tra lưu lượng truy cập đến và đi trong tài nguyên AWS
    - SG rule được hạn chế theo (Protocol, S.Address, Connection Port, SG khác)
    - SG rule chỉ cho phép rule allow
    - SG được áp dụng lên các ENI

- Network Access Control List (NACL): Là tường lửa ảo không trạng thái "Stateless" giúp kiểm soát lưu lượng truy cập đến và đi trong tài nguyên AWS
    - NACL được hạn chế theo (Protocol, S.Address, Connection Port)
    - NACL được áp dụng lên các VPC Subnet
    - Mặc định NACL cho phép mọi truy cập đến và đi

- VPC Flow Logs: Ghi lại lưu lượng IP đến và đi từ các ENI trong VPC
    - Các tập tin logs có thể được xuất lên CloudWatch Logs Hoặc S3
    - VPC Flow Logs không capture nội dung gói tin

- VPC Peering: Giúp kết nối 2 hay nhiều VPC, tài nguyên trong các VPC có thể liên lạc với nhau mà không cần thông qua Internet
    - VPC Peering là dạng kết nối 1:1 giữa 2 VPC thành viên, không hỗ trợ transitive routing
    - VPC Peering không hỗ trợ khi 2 VPC bị overlap IP Address

- Transit Gateway (TGW): Kết nối các VPC và mạng on-premises thông qua hub trung tâm (đơn giản hóa việc kết nối mạng)
    - Transit Gateway Attachment (TGA): Là công cụ để gán subnet của từng VPC cần kết nối với nhau vào một TGW.
    - TGA hoạt động ở quy mô AZ (AZ-level)
    - Trong VPC, 1Subnet ở 1AZ có TGA với TGW, các Subnet khác trong cùng AZ đều có thể kết nối tới TGW

- VPN Site to Site: Dùng trong mô hình Hybrid, giúp giữ kết nối liên tục giữa môi trường (DataCenter | AWS VPC)
    - Virtual Private Gateway: Được quản lý hoàn toàn bởi AWS (chia 2 endpoints ở 2 đầu AZ)
    - Customer Gateway: Endpoint ở phía khách hàng (Hardware Device | Software Appliance)

- VPN Client to Site: Cho phép một host truy cập tới tài nguyên trong VPC. Khuyến khích: Dùng VPN Client to Site trong AWS Market Place

- AWS Direct Connect: Dịch vụ cho phép kết nối từ DC truyền thống tới AWS (Độ trễ: 20ms - 30ms)
    - Hoạt động dưới 2 dạng: Hosted Connections - Dedicated Connections (Có thể thay đổi băng thông)

- Elastic Load Balancing (ELB): Dịch vụ cân bằng tải của AWS, giúp phân phối lưu lượng cho nhiều EC2 Instance hoặc Container
    - Có 4 loại ELB:
        - Application Load Balancer (ALB): Hoạt động ở Layer 7 (HTTP/HTTPS)
        - Network Load Balancer (NLB): Hoạt động ở Layer 4 (TCP/UDP), hỗ trợ gán Static IP
        - Gateway Load Balancer (GLB): Hoạt động ở Layer 3 (IP)
        - Classic Load Balancer (CLB): Hoạt động ở Layer 4 và Layer 7
    - Có thể nằm ở Public hoặc Private Subnet
    - Mỗi ELB sẽ được cấp DNS và kết nối thông qua DNS
    - ELD có tính năng lưu trữ logs truy cập (Access Logs) vào S3

- Application Load Balancer (ALB):
    - Hoạt động ở Layer 7 (HTTP/HTTPS)
    - Hỗ trợ tính năng path-based routing (/mobile /desktop sẽ được route tới các target group khác nhau)
    - Cho phép Route Traffic tới các Target nằm ngoài VPC, EC2, Lambda, Container (ECS, EKS)

- Network Load Balancer (NLB):
    - Hoạt động ở Layer 4 (TCP/UDP)
    - Hỗ trợ tính năng set static IP
    - Hỗ trợ hiệu năng cao nhất trong các loại ELB (hàng triệu request)
    - Cho phép Route Traffic tới các Target nằm trong VPC, EC2, Container (ECS, EKS)

- Classic Load Balancer (CLB):
    - Hoạt động ở Layer 4 và Layer 7
    - Chi phí cao hơn và ít tính năng cao cấp hơn ALB, NLB
    - Chỉ cho phép Route Traffic tới EC2
