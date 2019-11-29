# Tìm hiểu về Web Server

# 1.Khái niệm máy chủ Web-Web Server

- Web server là một loại máy chủ (hay server) được dùng để xử lý các truy cập được gửi từ máy khách thông qua giao thức HTTP. Các truy cập HTTP này thường được 
 gửi từ các trình duyệt web trên máy tính cá nhân

- Web Server có thể là phần cứng hoặc phần mềm hoặc cả hai:
  + Về phần cứng  thì web server về bản chất cũng là 1 loại máy chủ giống như các máy chủ khác, tuy nhiên máy chủ này cần phải được cài đặt ít nhất một phần mềm 
   web server để giúp máy chủ có thể xử lý các truy cập gửi tới thông qua giao thức HTTP.
   
  + Về mặt phần mềm,Web server được dùng là tên gọi của các phần mềm cài đặt trên máy chủ web. Hai phần mềm web server phổ biến hiện nay là: Apache, Nginx.
  
- Mỗi web server đều có một địa chỉ IP hoặc cũng có thể có một domain name. Bất kỳ máy tính nào cũng có thể trở thành web server bởi việc cài đặt lên nó một 
 chương trình phần mềm server software và sau đó kết nối vào Internet.

# 2.Web Server dùng để làm gì?

- Web Server có khả năng gửi đến máy khách những trang web thông qua mội trường internet thông qua giao thức http.
  ==> nhờ có chương trình này mà người sử dụng có thể truy cập đến các thông tin của trang Web từ một máy tính khác ở trên mạng

# 3.Hoạt động của máy chủ web

- Khi bạn nhập URL trên trình duyệt của mình (ví dụ:https://smartcloud.vn/ ), trình duyệt của bạn yêu cầu trang từ web server  và web server sẽ gửi lại trang
- B1: Trình duyệt phân giải tên miền thành địa chỉ IP
  + Đầu tiên trình duyệt web bạn xác định địa chỉ IP của tên miền https://smartcloud.vn/ trỏ về. Nếu thông tin được lưu trữ sẵn trên bộ nhớ cache thì trình 
  duyệt web sẽ biết được IP của tên miền.Còn nếu thông tin không được lưu trữ sẵn thì trình duyệt web sẽ yêu cầu thông tin từ máy chủ DNS.Máy chủ DNS sẽ
  cho trình duyệt web biết IP của tên miền.
- B2: Trình duyệt web yêu cầu URL đầy đủ
  + Bây giờ trình duyệt web đã biết địa chỉ IP của trang web,nó có thể yêu cầu đầy đủ URL của web server
- B3: Web server gủi trang được yêu cầu
  + Web server gửi lại phản hồi bằng cách gửi lại trang được yêu cầu.Nếu trang không tồn tại hoặc có lỗi xảy ra thì web server se gửi lại lỗi thông báo lỗi
   thích hợp
- Trình duyệt hiển thị trang web
  + Trình duyệt web của bạn nhận được phản hồi từ web server và hiển thị trang được yêu cầu.

- Mốt số hoạt động khác;
  + Vận hành nhiều website: một Web Server có thể chứa nhiều hơn một website.
  + Page Not Found: Nếu không tìm thấy trang được yêu cầu, webserver sẽ gửi mã / thông báo lỗi thích hợp trở lại máy khách.
  + SSL Certificates: Bạn có thể áp dụng SSL certificates trên 1 website thông qua web server. Điều này giúp hạn chế việc những cá nhân có động cơ không tốt có
  thể đọc được các thông tin nhạy cảm của người dùng truy cập web.
  
# 4.Vận hành một trang web

- Để vận hành một trang web,chúng ta cần một web server tĩnh hoặc một web server động

# 4.1.Web tĩnh

- Trang web tĩnh thường được xây dưng bằng các ngôn ngữ HTML,DHTML,..
- Trang web tĩnh thường được dùng để thiết kế các trang web cần ít thay đổi và cập nhật  
- Web tĩnh là website chỉ chứa các web tĩnh,không chứa các cơ sở dữ liệu đi kèm
- Web tĩnh thích hợp với cá nhân,tổ chức,các doanh nghiệp vừa và nhỏ mới làm quen với môi trường internet.

- Ưu điểm web tĩnh:
  + Thiết kế đồ họa đẹp
  + Tốc độ truy cập nhanh: vì không mất thời gian truy vấn cơ sở dữ liệu như web động
  + thân thiện hơn với các máy tìm kiếm
  + Chi phí đầu tư thấp: vì không phải đầu tư cho việc xây dựng các cơ sở dữ liệu,lập trình phần mềm cho website, thuê chỗ cho cơ sở dữ liệu.

- Nhược điểm của web tĩnh:
  + khó khăn trong việc cập nhật và thay đổi thông tin
  + Thông tin không có tính linh hoạt:Do nội dung trên trang web tĩnh được thiết kế cố định nên khi nhu cầu về thông tin của người truy cập tăng cao thì thông 
  tin trên website tĩnh sẽ không đáp ứng được. 
  + Khó tích hợp nâng cấp,mở rộng:Khi muôn nâng cấp hay mở rộng một website thì hầu như là phải làm lại mơi từ đâu.
  
  
# 4.2 Web động

- Một web server động bao gồm một web server tĩnh cùng với các phần mềm mở rộng của chúng. 
- web động là những website có cơ sở dữ liệu và được hỗ trợ bởi các phần mềm phát triển web
- Với web động, thông tin hiển thị được gọi ra từ một cơ sở dữ liệu khi người dùng truy vấn tới một trang web
- Trang web được gửi tới trình duyệt gồm những câu chữ; hình ảnh; âm thanh hay những dữ liệu số hoặc ở dạng bảng hoặc ở nhiều hình thức khác nữa.
- Web động thường được phát triển bằng các ngôn ngữ lập trình tiên tiến như PHP; ASP; ASP.NET; Java..
- Web động sử dụng các cơ sở dữ liệu quan hệ mạnh như Access; My SQL; MS SQL; Oracle; DB2…

- Ưu điểm:
  + Thông tin trên web động luôn luôn mới vì nó dễ dàng được bạn thường xuyên cập nhật thông qua việc bạn sử dụng các công cụ cập nhật của các phần mềm quản 
  trị web. 
  + Web động có tính tương tác với người sử dụng cao
- Nhược điểm:   
  + cần phải có chi phí đầu tư cao hơn web tĩnh.
  
# 5.Install apache

- Cập nhật package: `apt-get update`

- Cài đặt Apache: `apt-get install apache2`

- Cài đặt xong thì truy cập vào địa chỉ IP của máy chủ, bạn sẽ thấy trang chào mừng của Apache như thế này:
- ![]( /image/apache1.PNG)

- Cấu trúc thư mục cấu hình Apache trên Ubuntu:
  + `conf-available/ `– Thư mục này sẽ chứa các file thiết lập cấu hình sẵn của Apache trên Ubuntu
  + `conf-enabled/` – Thư mục chứa các file thiết lập cấu hình của Apache trên Ubuntu đang được bật
  + `mods-available/` – Thư mục chứa các file từng module của Apache trên Ubuntu nhưng chưa được bật
  + `mods-enabled/ `– Thư mục chứa các file từng module của Apache trên Ubuntu đang được bật.
  + `site-available/` – Thư mục chứa file cấu hình VirtualHost của Apache trên Ubuntu nhưng chưa được bật.
  + `site-enabled/` – Thư mục chứa file cấu hình VirtualHost của Apache trên Ubuntu đang được bật
  + `apache2.conf` – File cấu hình Apache trên Ubuntu.
  + `envvars` – File thiết lập các biến với giá trị sẵn để sử dụng trong các file cấu hình.
  + `magic` – File thiết lập của module mod_mime_magic trên Apache.
  + `ports.conf` – File cấu hình cổng mạng của Apache (mặc định là port 80).



-Tạo alias cho web site:` sudo vi /var/www/html/test.html`

 ![]( /image/test.PNG)

- ![]( /image/apache2.PNG)
  






# tham khảo:

- https://vdodata.vn/ung-dung-may-chu-web-web-server/
- https://viblo.asia/p/tim-hieu-ve-web-server-maGK7zyx5j2?__cf_chl_captcha_tk__=047dec39eda6e46df09be6e2a8d3f96bce0080e9-1574904446-0-AfpG7lwyPQislfSprdzOteNnDSPsGjVdYIKvbqCcBt8cCZMVaW-Yc2-dDwB2bm6D-RNeG6ju9KEFDhwF1RJ6s6Vk5jLibfFtLdIdgN1alx4yl2UDTVf5DyBp0yOUmj7M9k2RSG5vVcdc_B56JEpSJDclPP4bdfmAsqii7cTSSBby_9fayApD7YZTvOUbvqp9HwnjuK6W0Wt6j-TXiKAaUDIKkyps7rKZDjcycY3VrysQCv_bPxrs1q_naZUtVwmtlgUYSrAp13xWN9WFJlTPSwycW-pZ3srUSE5p2Tl0cZInOGtDZV7oX0Jrhyw3t8vJ_Kvj-ngT3dQmplPgdgwngrWPDaG0Gk7eziTI31stx9ZXxeVEW29FW9yGnNz5nNDAdT34EJmp-PPsumHGare5YX_Pk-MWG652ohGFiq88ZWxB
- https://www.codehub.vn/Web-server-la-gi
- https://tech.bizflycloud.vn/tim-hieu-web-server-hoat-dong-nhu-the-nao-20180703101609013.htm
   
