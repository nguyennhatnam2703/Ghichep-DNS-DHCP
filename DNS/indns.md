# Mục lục

# Cài đặt DNS server

# 1.Chuẩn bị:
- Để chuẩn bị lab này ,người viết sử dụng 2 máy.Trong đó 1 máy làm DNS server chính,một máy làm client
- Máy 1:DNS Server Master :
  + Hệ điều hành : CentOS 7
  + Hostname : masterdns.anninhmang.edu.vn
  + IP : 192.168.74.139/255.255.255.0
  
- Máy 2: DNS Server Client :
  + Hệ điều hành : Win 7 Ultimate
  + Hostname : client.anninhmang.edu.vn
  + IP : 192.168.74.138/255.255.255.0
  
#  2.Cài đặt DNS Server Master :

- Trước hết cần cài đặt gói bind vào máy: ` yum install bind bind-utils –y `

## 3.Cấu hình DNS Server :

- Tìm và Edit file ‘/etc/named.conf’: `vi /etc/named.conf  `
- Ta tìm đến ` listen-on port 53 { 127.0.0.1; }; ` và sửa lại thành:  
 ` listen-on port 53 { 127.0.0.1; 192.168.74.139;}; `
- trong block options, ta tìm đến `allow-query { localhost; }; ` và sửa lại thành:
  ` allow-query  { localhost; 192.168.74.0/24; }; `
- Cấu hình liên kết zone files: Việc cấu hình này nhắm mục đích tạo ra liên kết tới một zone để khai báo cho các tên miền cho phép DNS Server phân giải tên miền
 từ các địa chỉ IP :
  +  sau đó thêm nội dung sau ở bên ngoài block options
  + ` zone "anninhmang.edu.vn" IN {

      type master;

      file "forward.anninhmang";

      allow-update { none; };

      };

      zone "74.168.192.in-addr.arpa" IN {

      type master;

      file "reverse.anninhmang";

      allow-update { none; };

      }; `
- Tiến hành tạo Zone File : Như bạn đã thấy ở trên file ‘/etc/named.conf’, chúng ta có thêm vào vài dòng trong đó có đề cập đến 2 file Forward và Reserve :

- Tạo vùng Forward Zone :
  + Tạo file forward.anninhmang trong thư mục ‘/var/named’ : ` vi /var/named/forward.anninhmang `
  + Thêm vào những dòng này :
  ``` $TTL 86400

    @   IN  SOA     masterdns.anninhmang.edu.vn. root.anninhmang.edu.vn. (

    2011071001  ;Serial

    3600        ;Refresh

    1800        ;Retry

    604800      ;Expire

    86400       ;Minimum TTL

  )

    @       IN  NS          masterdns.anninhmang.edu.vn.

    @       IN  A           192.168.74.139

    @       IN  A           192.168.74.138

    masterdns       IN  A   192.168.74.139

    client          IN  A   192.168.74.138  ```
  
–  Tạo vùng Reserve Zone :
   + Tạo file reserve.anninhmang ở trong thư mục ‘/var/named’ : ` vi /var/named/reverse.anninhmang `
   + Thêm vào những dòng sau :
    ` $TTL 86400

      @   IN  SOA     masterdns.anninhmang.edu.vn. root.anninhmang.edu.vn. (

      2011071001  ;Serial

      3600        ;Refresh

      1800        ;Retry

      604800      ;Expire

      86400       ;Minimum TTL

    )

      @       IN  NS          masterdns.anninhmang.edu.vn.

      @       IN  PTR         anninhmang.edu.vn.

      masterdns       IN  A   192.168.74.139

	  client          IN  A   192.168.74.138

	  139     IN  PTR         masterdns.anninhmang.edu.vn.

	  138     IN  PTR         client.anninhmang.edu.vn. `

# 4.Khởi chạy dịch vụ DNS Server :
- systemctl enable named

- systemctl start named

# 5.Cấu hình Firewall :

- Mở Port 53 trên Firewall để dịch vụ DNS có thể được thông qua :
  + ` firewall-cmd --permanent --add-port=53/tcp `
  + ` firewall-cmd --permanent --add-port=53/udp `
  
- Restart lại Firewall để thay đổi có hiệu lực : ` firewall-cmd –reload `

# 6.Tiến hành Test thử DNS Server để đảm bảo không có lỗi :

- Chạy dòng lệnh để check DNS Server : `named-checkconf /etc/named.conf`
  + Nếu dòng lệnh không có gì trả về, tức là bạn đã cấu hình đúng.
  
- Check Forward Zone bằng dòng lệnh : `named-checkzone anninhmang.edu.vn /var/named/forward.anninhmang`
  + kết quả trả về:
  + ` zone anninhmang.edu.vn/IN: loaded serial 2011071001
  
      OK `

- Check Reserve Zone bằng dòng lệnh : `named-checkzone anninhmang.edu.vn /var/named/reverse.anninhmang`
  + kết quả trả về:
  + ` zone anninhmang.edu.vn/IN: loaded serial 2011071001

     OK `
	 
# 7.Tiến hành Add DNS Server vào file cấu hình card mạng :

- Ta tiến hành sửa file: ` vi /etc/sysconfig/network-scripts/ifcfg-ens33 `
  + thêm vào dòng ` DNS="192.168.74.139" `
  
- Edit file /etc/resolv.conf, ` vi /etc/resolv.conf `

- Thêm vào địa chỉ IP của Name Server : ` nameserver      192.168.74.139 `

# 8.Test DNS Server	

- chạy dòng lệnh: `dig masterdns.anninhmang.edu.vn`
- kết quả trả về:
- ![]( /image/dns1.PNG) 

- Chạy tiếp dòng lệnh : ` nslookup anninhmang.edu.vn `
-  kết quả trả về:
- ![]( /image/dns2.PNG)

- Vậy là DNS Server đã sẳn sàng để sử dụng.
	  
	  
	  

	  `
	  
  
  
