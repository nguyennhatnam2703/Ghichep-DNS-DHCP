# Triển khai DHCP

# Mô hình:

- DHCP server chạy trên hệ điều hành Ubuntu server 18.04, sử dụng gói phần mềm isc-dhcp-server để chạy DHCP server. Địa chỉ ip: 192.168.74.135/24

- Client sử dụng hệ điều hành Ubuntu server 16.04

# Các bước hoạt động

- Cài đặt gói isc-dhcp-server để triển khai dịch vụ DHCP Server.
   ` apt-get install -y install isc-dhcp-server  `
-  Cấu hình DHCP Server:
   + Cấu hình Interface dùng cho DHCP Server: `/etc/default/isc-dhcp-server`
   +  sửa `INTERFACESv4="ens33"`
   
   + sửa file cấu hình:
   ``` ddns-update-style none;
       option domain-name "example.org";
       option domain-name-servers ns1.example.org, ns2.example.org;
       default-lease-time 600;
       max-lease-time 7200;
       authoritative;
       log-facility local7;
       subnet 192.168.74.0 netmask 255.255.255.0 {
	   option routers 192.168.74.1;
	   option subnet-mask 255.255.255.0;
	   range dynamic-bootp 192.168.74.160 192.168.74.170;
	   option broadcast-address 192.168.74.255;
       } . `
	   
	+ ![]( /image/dhcp1.png)   
	   
- Giải thích file cấu hình:
  + ddns-update-style none; : Không cho cập nhật DNS động

  + option domain-name “nhoclinh.com; : Tên domain của mạng

  + option domain-name-servers ns1.example.org, ns2.example.org : Máy chủ DNS

  + default-lease-time 600; : Thời gian cấp mặc định là 600 giây

  + max-lease-time 7200; : Thời gian tối đa cấp IP nếu sau thời gian này không phản hồi tín hiệu thì IP sẽ được cấp cho clients khác trong mạng

  + authoritative; : Nếu DHCP Server dùng cho mạng cục bộ thì ta nên kích hoạt tính năng authritative

  + log-facility local7; file log.

  + subnet : Địa chỉ mạng.

  + netmask : Định nghĩa lớp mạng.

  + option routers : Default getway cho mạng.

  + range : khoảng IP dùng để cấp cho các client trong mạng.  
  
-   Khởi chạy dịch vụ: ` service isc-dhcp-server start `

- Kết quả: Trên client:
  ![]( /image/dhcp2.png)

  
	   
	   
	   

