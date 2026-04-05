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