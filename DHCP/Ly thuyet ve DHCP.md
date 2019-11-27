# Tìm hiểu DHCP	

# 1.Tại sao DHCP ra đời?
- DHCP là giao thức cấu hình host động được thiết kế nhằm làm giảm thời gian chỉnh cấu hình cho mạng TCP/IP bằng các tự động gán IP cho khách hàng
  khi họ vào mạng.

- Nhờ có DHCP mà người điều hành mạng có rất nhiều thuận lợi,nó làm yên tâm về các vấn đề sự cố xảy ra khi phải cấu hình IP thủ công.

# 2.DHCP là gì ?

- Dynamic Host Configuration Protocol (DHCP - giao thức cấu hình động máy chủ) là một giao thức cấu hình tự động địa chỉ IP.
- Hiện nay DHCP có 2 version: cho IPv4 và IPv6
- DHCP sử dụng port 67,68 và dùng giao thức UDP.
- Được xác định trên mô hình client-server
- DHCP hỗ trợ 3 cơ chế cấp địa chỉ IP
  + Cấp tự động: DHCP gán 1 địa chỉ IP thường trực → 1 Client
  + Cấp động: DHCP gán địa chỉ IP cho 1 khoảng thời gian hữu hạn nào đó
  + Cấp thủ công: 1 địa chỉ IP được gán bời người quản trị. DHCP chỉ để đưa địa chỉ này đến Client
  
# 3.Chức năng của DHCP

- Câú hình động các máy
- Cấu hình Ip cho các máy một cách liền mạch.
- Tập trung quản lí thông tin về cấu hình IP

# 4.Các thuât ngữ trong DHCP

- `DHCP Server`: máy quản lý việc cấu hình và cấp phát địa chỉ IP cho Client
- `DHCP Client`: máy trạm nhận thông tin cấu hình IP từ DHCP Server
- `Scope`: phạm vi liên tiếp của các địa chỉ IP có thể cho một mạng.
- `Exclusion Scope`: là dải địa chỉ nằm trong Scope không được cấp phát động cho Clients.
- `Reservation`: Địa chỉ đặt trước dành riêng cho máy tính hoặc thiết bị chạy các dịch vụ (tùy chọn này thường được thiết lập để cấp phát địa chỉ cho các Server,
 Printer,…..)
- `Scope Options`: các thông số được cấu hình thêm khi cấp phát IP động cho Clients như DNS Server(006), Router(003)

# 5.Các loại bản tin DHCP

- `DHCP Discover`: Khi 1 client muốn gia nhập mạng, nó sẽ broadcast 1 gói tin dhcp discover tới dhcp server để yêu cầu cấp thông tin địa chỉ ip.Ip nguồn trong
  gói là 0.0.0.0.
  
- ` DHCP Offer `: 
  + Unicast từ DHCP server sau khi nhận được gói Discover của client.
  + Gói tin bao gồm thông tin IP đề nghị cấp cho client như: IP address, Subnet Mask, Gateway...
  + Có thể sẽ có nhiều DHCP server cùng gửi gói tin này, Client sẽ nhận và xử lý gói Offer đến trước.

- ` DHCP Resquest `:
  + Broadcast từ client khi nhận được gói DHCP Offer.
  + Nội dung gói tin: xác nhận thông tin IP sẽ nhận từ server để cho các server khác không gửi gói tin offer cho clien đấy nữa.
  
- ` DHCP Acknowledge `:
  + Unicast bởi DHCP server đến DHCP client xác nhận thông tin từ gói DHCP Request.
  + Tất cả thông tin cấu hình IP sẽ được gửi đến cho client và kết thúc quá trình cấp phát IP.

- `DHCP Nack`: Unicast từ server, khi server từ chối gói DHCP Request.

- `DHCP Decline`:Broadcast từ client nếu client từ chối IP đã được cấp.

- `DHCP Release`:Được gửi bởi DHCP client khi client bỏ địa chỉ IP và hủy thời gian sử dụng còn lại.

# 6.Cách thức hoạt động:

- ![]( /image/hddhcp.png)

- Bước 1: DHCP Client gửi broadcast thông điệp discover message để tìm một DHCP Server nhằm xin IP

- Bước 2: Nhiều DHCP server có thể nhận thông điệp và chuẩn bị IP cho client.Nếu máy chủ có cấu hình hợp lệ cho client, nó gửi thông điệp "DHCP Offer" chứa
  địa chỉ MAC của khách, địa chỉ IP, subnet mask, địa chỉ IP của server và thời gian cho thuê đến client.
  
- Bước 3: Khi client nhận được các thông điệp DHCP Offer nó sẽ chọn 1 trong các địa chỉ IP, sau đó sẽ gửi DHCP Request để yêu cầu IP tương ứng với DHCP server 
  đó
  
- Bước 4: Cuối cùng, DHCP Server xác nhận lại với client bằng thông điệp DHCP Acknowlegde.Ngoài ra server còn gửi kèm những thông tin bổ sung như địa chỉ 
  gateway mặc định, địa chỉ DNS Server.

# 7.DHCP Relay Agent

- ![]( /image/dhcpreplay.jpg)

- DHCP Relay là gì:
  + DHCP Relay Agent là một cấu hình được đặt cho máy tính hoặc một Router tiếp nhận các thông tin yêu cầu cấp phát IP của clients và chuyển các thông tin này
  đến DHCP server

- Tại sao phải sử dụng DHCP Relay Agent ?
  + Khi giữa Clients và DHCP server có nhiều mạng khác tương ứng với nhiều router khác thì cần phải cấu hình DHCP Relay Agent vì Clients sử dụng địa chỉ 
  broadcast để quảng bá yêu cầu cấp phát IP, khi gói tin gửi bằng broadcast đến Router thì sẽ bị loại bỏ, do vậy phải có cách để cho các router trung gian 
  chấp nhập những gói tin broadcast này và gửi đến DHCP server, cách này chính là DHCP Relay Agent.
  
- Ưu diểm của DHCP Relay:
  + Phù hợp với các máy tính thường xuyên di chuyển giữa các lớp mạng.
  + Kết hợp với hệ thống mạng không dây ( Wireless) cung cấp tại các điểm – Hotspot như: nhà ga, sân bay, khách sạn, trường học.
  + Thuận tiện cho việc mở rộng hệ thống mạng.

# Tham khảo:

[1]  https://vdodata.vn/cac-khai-niem-co-ban-ve-dhcp/

[2] https://github.com/hocchudong/thuctap032016/blob/master/LTLinh/LTLinh-B%C3%A1o%20c%C3%A1o%20giao%20th%E1%BB%A9c%20DHCP/LTLinh-baocaotimhieugiaothucdhcp.md

[3] https://vdodata.vn/dhcp-relay-la-gi-va-cau-hinh-dhcp-relay-nhu-the-nao/
  
  
 
  
 
