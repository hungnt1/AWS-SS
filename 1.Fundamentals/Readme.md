

##  1. Cơ bản về AWS.   
- Hiện tại AWS có 4 gói cơ bản sau 
    + Basic ( Free)
    + Developer ( chủ yếu sử dụng để trải nghiệm và phát triển  )
    + Business  ( sử dụng trong trường hợp có workload chạy trên AWS, có nhân viên tech hỗ trợ 24/7 ) 
    + Enterprise ( workload trên AWS là core của doanh nghiệp, ảnh hưởng nhiều đến business )

- Public và Private Service ( đây chỉ là vấn đề networking, không phải quyền )
    + Public  Internet: AWS là một nền tảng public và kết nối tới internet
    + AWS Public zone: kết nối trực tiếp với Public Internet. S3 Bucket được host trên Public Zone, nhưng không phải là tất cả.
    + AWS Private Zone: Khồng có kết nối trực tiếp giữa Public ZOne và Private Zone, trừ khi bạn cấu hình cho phép 2 Zone liên hệ với nhau ( cơ bản là NAT Private Zone ra Public Zone.), điều này cho phép một phần trong dịch vụ của bạn có kết nối ra/ vào với internet.


    
## 2. AWS Global Infrastructure

### 2.1. Regions

- Region là một vị trí địa lý là AWS chọn để xây dựng hạ tầng tại đây
- Area có thể là một quốc gia hoặc thành phố trong quốc gia ví dụ như: Singapore, Ohio, Londo. List region của AWS thì khó mà list vì nhiều và không ổn định

### 2.2. AWS EDGE Location

- Các Edge Location của AWS chủ yếu để lưu trữ các dữ liệu, mục đích là nguồn dữ liệu càng gần người dùng càng tốt, độ trẽ thấp thì trải nghiệm người dùng càng mượt mà.

### 2.3. AWS Management
- Các Region kết nối với nhau thông qua line mạng tốc độ cao. Một số dịch vụ cần chọn region để có thể hoạt động ví dụ như EC2 hoặc S3, còn với IAM là mang tính global.


### 2.4 Các lợi ích của Region

- Phân cách địa lý
    + Tránh được các thiên tại tự nhiên
    +  Cung cấp miền lỗi độc lập
    + Các khu vực hoàn toàn tách biệt 100%

- Kiểm soát vị trí 
    + có thể mở rộng thêm để gần với khách hàng
    + Điều chỉnh kiến trúc cho phép tăng hiệu năng

## 2.5. Regions and AZs

- Ví dụ mình có một region là Singapore. Có sẽ ẻm nó là  ap-southeast-2
- AWS sẽ bố trí có ít nhất 2 AZ và nhiều nhất là 6AZ trên region này.
- Trên các AZ nguồn tính toán, lưu trữ, mạng và nguồn điện được tách biệt nhau. Các thành phần có khả năng phân phối tải và khả năng tự phục hồi giữa các AZ trên một region.
- Các AZ được kết nối với nhau bằng mạng dự phòng tốc độ cao.

## 2.6. Khả năng phục hồi dịch vụ

    1. Phục hồi toàn cầu: Với IAM và Route53 thì chỉ có ngày tận thế mới làm dịch vụ down do dữ liêu được nhân bản ra toàn bộ các region.
    2. Phục hồi toàn region: Thông thường dữ liệu được nhân bản sang các AZ trong region.
    3. Phục hồi trong AZ: đây là miền lỗi dễ mất dữ liệu nhất trên AWS. Nguyên nhân chủ yếu là lỗi phần cứng, biết là có dự phòng phần cứng nhưng cũng không nên dựa vào nhiều.


## 2.7. AWS Default VPC
- VPC là một mạng ảo bên trong AWS. Một VPC sẽ nằm trong một tài khoản, và có effect trên toàn region. 
- MẶC định VPC hoàn toàn private với nhau  cho dến khi bạn cấu hình thêm

- Mặc định mỗi region sẽ có một VPC có subnet nè 173.31.0.0/16, nếu muốn thì có thể tạo thêm VPC. Nếu không nhầm thì AWS không limit vụ này.

- Thông thường default VPC không được sử dụng do /16 là quá lớn, không cần thiết, cũng như cần thiết kế lại plan network trước khi xây dựng. VPC mặc định chỉ để sử dụng trong quá trình test.