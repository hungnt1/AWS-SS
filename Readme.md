
## AWS-SSA Note
- Đây là tài liệu ghi chép các nhân dựa lên bộ tài liệu gốc https://github.com/acantril/aws-sa-associate-saac02 và https://github.com/alozano-77/AWS-SAA-C02-Course#12-aws-fundamentals


## 1. Introduction

### Bài toán đặt ra

- Animals4life là một tổ chức cứu hộ và bản tồn động vật. Hiện tại hệ thống IT của tổ chức bao gồm Call Center, Admin, IT Marketing, Account, ngoài ra bao gồm gần khoảng 100 nhân viên hoạt động trên toàn cầu.
- Hiện tại công ty có các văn phòng tại London, Net york và Seattle và có một trung tâm dữ liệu tại Briban. Hiện tại công ty đang thử nghiệm tại AWS Singapore để dịch chuyển hạ tầng IT 


### Các vấn đề đang gặp phải
- Hạ tầng on-premises đang gặp vấn đề về lỗi
- AWS Piolot/AWS đang bị lộn xộn và không phải hoàn toàn tối ứu
- Vấn đề hiệu năng cho các công nhân
- Thiếu HA và khả năng mở rộng do chi phí đầu tư phần cứng đắt
- Khi muốn dây dựng một cơ sở hạ tầng mới rất khó khăn do chi phí cao.

### Một số yêu cầu cụ thể
- Yêu cầu hiệu năng cao và nhanh cho tất cả công nhân
- Khả năng xây dựng một vùng mới khi có yêu cầu
- Hạ chế cost và tăng khả năng mở rộng
- Khả năng xây dựng các hệ thống IOT, BigData và tự động


## 2. Cơ bản về Điện Toán Đám Mây ( Cloud Computing )

- Tham khảo thêm lại nist.gov/system/files/documents/itl/cloud/cloud-def-v15.pdf

### 2.1 Định nghĩa cơ bản
- Dưới đây là định nghĩa về Cloud Computing của Viện NIST. Tốt nhất là không nên dịch sang Tiếng Việt để giữ được nguyên bản của định nghĩa.
"Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction."

### 2.2 Mô hình 5-4-3 trong Cloud Computing
- Cơ bản NIST chia Cloud Computing thành mô hình 5-4-3. 
- 5 tính chất cơ bản:
    + Tính tự phục vụ: Người dùng dịch có thể tự phân phối các tài nguyên tính toán có thể là máy chủ, lưu trữ tự động mà công cần tác động của con người vào dịch vụ.
    + Tính truy cập qua mạng: mọi thiếu bị có thể sử dụng mạng kết nối vào hệ thống sử dụng các giao thức và phương thức chuẩn
    + Tính tổng hợp tài nguyên: khả năng tổng hợp tài nguyên và cấp pháp cho nhiều nhu cầu sử dụng khác nhau. Với mặt khách hàng toàn toàn trong suốt không có khả năng quản lý và biết, tuy nhiên người dùng có thể chỉ định vị trí và nhóm tài nguyên.
    + Tính co giãn: có thể mở rộng và thu hẹp dựa vào tải của hệ thống. Tính co giãn này có thể tự động dựa vào các ngưỡng của hệ thống, điều này giúp tối ưu chi phí và tính linh động của hệ thống.
    + TÍnh đo lường: Khả năng đo lường thông số sử dụng của các dịch vụ. Chỉ phải trả tiền cho những gì bạn sử dụng, dùng bao nhiêu trả bấy nhiêu, không như đổ xăng xe máy rồi dùng từ từ.

- 4 mô hình dịch vụ
    + Cloud Software as Service ( SaaS ): Sử dụng các phần mềm dưới dạng dịch vụ giống như Google Drive hoặc Netflix. Vendor cung cấp sẽ đảm bảo an toàn và tính bền vững của ứng dụng tuy nhiên phải trả thêm phí. Nhược điểm là khả năng kiểm soát ít, đa số chỉ có thể sử dụng.
    + Platform as a Service ( PaaS): Phù hợp với use-case là chỉ để chạy ứng dụng, vendor sẽ cung cấp môi trường ( runtime ) cho ứng dụng. Bạn sẽ kiểm soát ứng dụng và dữ liệu, còn lại vendor lo
    + nfrastructure as a Service (IaaS): Vendor sẽ quản lý và cung cấp các tài nguyên để có một OS hoàn chỉnh ( network, storage, GPU, CPU, RAM). Chỉ yếu mình sẽ sử dụng và trả phí cho các tài nguyên để hoạt động OS đó trên từng phút hoặc giờ. Ngoài ra một số HĐH yêu cầu license sẽ yêu cầu trả thêm phí license cho OS đó.

- 3 mô hình dịch vụ
    + Public Cloud: các vendor sẽ cung cấp dịch vụ, chỉ việc trả tiền và dùng như AWS, Azure, Google Cloud. 
    + Private Cloud: xây dựng một nền tảng cloud trên hạ tầng tại chỗ, xây lên thì lây 5 tiêu chuẩn ở trên làm kim chỉ nam.
    + Hybrid Cloud: sử dụng Private Cloud và Public Cloud cho một môi trường. Đây là sử dụng nền tảng Cloud chứ không phải sử dụng hardware on-premises  và Public Cloud
    + Community Cloud: một tổ chức xây dựng nền tảng Cloud, sau đó mục đích vì cộng đồng thì có thể chia tài nguyên.

