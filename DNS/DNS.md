# Tìm hiểu về  DNS

=========
# Mục lục
=========

[1. DNS sever là gì](#1) 

[2. Chức năng DNS server](#2)

[3. Nguyên tắc làm việc của dns server](#3)

[4. Cách sử dụng DNS](#4)

[5. Cách đọc tên miền](#5)

[6. Các loại của DNS server và vai trò của nó](#6)

[7. DNS zone](#7)

[7.1. Tạo zone](#7.1)

[8.Cách DNS server hoạt động](#8)


<a name="1"></a>
# 1.DNS sever là gì
- DNS (domain name system) là hệ thống phân giải tên được phát minh vào năm 1984,chỉ một hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền.
- Hệ thống tên miền (DNS) về căn bản là một hệ thống giúp cho việc chuyển đổi các tên miền mà con người dễ ghi nhớ (dạng kí tự, ví dụ www.example.com) sang 
  địa chỉ IP vật lý (dạng số, ví dụ 123.11.5.19) tương ứng của tên miền đó. 

<a name="2"></a>
# 2.Chức năng DNS server
-Mỗi Website có một tên (là tên miền hay đường dẫn URL:Universal Resource Locator) và một địa chỉ IP. Địa chỉ IP gồm 4 nhóm số cách nhau bằng dấu chấm(Ipv4).
Khi mở một trình duyệt Web và nhập tên website, trình duyệt sẽ đến thẳng website mà không cần phải thông qua việc nhập địa chỉ IP của trang web. Quá trình 
"dịch" tên miền thành địa chỉ IP để cho trình duyệt hiểu và truy cập được vào website là công việc của một DNS server. Các DNS trợ giúp qua lại với nhau để 
dịch địa chỉ "IP" thành "tên" và ngược lại. Người sử dụng chỉ cần nhớ "tên", không cần phải nhớ địa chỉ IP 

<a name="3"></a>
# 3.Nguyên tắc làm việc của dns server
- Mỗi nhà cung cấp dịch vụ vận hành và duy trì DNS server riêng của mình, gồm các máy bên trong phần riêng của mỗi nhà cung cấp dịch vụ đó trong Internet. 
Tức là, nếu một trình duyệt tìm kiếm địa chỉ của một website thì DNS server phân giải tên website này phải là DNS server của chính tổ chức quản lý website 
đó chứ không phải là của một tổ chức (nhà cung cấp dịch vụ) nào khác.

- DNS server có khả năng ghi nhớ lại những tên vừa phân giải. Để dùng cho những yêu cầu phân giải lần sau. Số lượng những tên phân giải được lưu lại tùy thuộc
 vào quy mô của từng DNS.
 
- DNS có khả năng truy vấn các DNS server khác để có được một cái tên đã được phân giải. DNS server của mỗi tên miền thường có hai việc khác biệt. Thứ nhất,
 chịu trách nhiệm phân giải tên từ các máy bên trong miền về các địa chỉ Internet, cả bên trong lẫn bên ngoài miền nó quản lý. Thứ hai, chúng trả lời các DNS
 server bên ngoài đang cố gắng phân giải những cái tên bên trong miền nó quản lý. 
 
 <a name="4"></a>
# 4.Cách sử dụng DNS
- Do các DNS có tốc độ biên dịch khác nhau, có thể nhanh hoặc có thể chậm, do đó người sử dụng có thể chọn DNS server để sử dụng cho riêng mình. Có các cách
 chọn lựa cho người sử dụng. Sử dụng DNS mặc định của nhà cung cấp dịch vụ (Internet), trường hợp này người sử dụng không cần điền địa chỉ DNS vào network 
 connections trong máy của mình. Sử dụng DNS server khác (miễn phí hoặc trả phí) thì phải điền địa chỉ DNS server vào network connections. Địa chỉ DNS server
 cũng là 4 nhóm số cách nhau bởi các dấu chấm. 

<a name="5"></a>
# 5.Cách đọc tên miền:
-Giả sử có tên miền www.abc.com.vn Một tên miền sẽ được đọc từ trái qua phải, với tên miền nêu trên sẽ được cấu tạo từ các nhãn www, abc, com, vn.Trong đó:
 + www là tên máy tính
 + abc là tên miền cấp ba
 + com là tên miền cấp hai
 + vn là tên miền ở mức top-level-domanin

<a name="6"></a>
# 6.Các loại của DNS server và vai trò của nó:
- Root name server:là máy chủ tên miền chứa các thông tin để tìm kiếm các thông tin máy chủ tên miền lưu trữ cho các tên thuộc tên miền cao nhất( top- level-
domain) 
- Local name server:Là máy chủ tên miền chứa các thông tin để tìm kiếm các thông tin máy chủ tên miền lưu trữ cho các tên thuộc tên miền thuộc thấp hơn.Nó
 thường đươc làm chủ và duy trì bởi các doanh nghiệp,các nhà cung cấp dịch vụ internet.
- Primary name server: Là DNS chính trên đó cho phép thêm sửa xóa CSDL trên DNS
- Secondary name server:Là DNS phụ,backup lại CSDL của Primary.Secondary name server không được sửa,xóa CSDL trên DNS.Nó được sử dụng khi Primary bị fail
hoặc khi quá tải.
- Caching name server:DNS server và client sẽ lưu lại các truy vấn,nó có tác dụng:
  + Để khi được truy vấn lần sau nó sẽ tìm đến các cache trước,nếu cache có thì nó sẽ trả lời ngay lập tức mà không cần truy vấn nữa
 =>> điều nay nó giúp cho mạng hoạt động nhanh hơn.

 <a name="7"></a>
 # 7.DNS zone
- Một domain có thể có 1 hoặc nhiều domain con bên trong nó gọi là subdomain.
- Ví dụ:domain “.com” có nhiều subdomain như vnnetpro.com, yahoo.com, google.com,…​
- Những domain và subdomain mà DNS Server quản lý gọi là Zone.
=>> 1 zone có thể bao gồm 1 domain và một hoặc nhiều subdomain.
- Thông tin DNS zone bao gồm:
  + tên Host
  + địa chỉ IP được lưu trong DNS server.
- Zone file : Lưu thông tin của Zone, có thể ở dạng text hoặc trong Active Dicrectory.

<a name="7.1"></a>
# 7.1.Tạo zone:

- Forward Lookup Zone :​
  + dùng để phân giải host name thành địa chỉ IP.
- Reverse Lookup Zone :​
  + Dùng cho việc phân giải ngược giống như In-addr.arpa Zone. Cho phép phân giải địa chỉ IP thành host name  

<a name="8"></a>
# 8.Cách DNS server hoạt động

- ![]( /image/hddns.png )

- B1:Trước hết chương trình trên máy người sử dụng gửi yêu cầu tìm kiếm địa chỉ IP ứng với tên miền whitehat.vn tới máy chủ quản lý tên miền (name server)
 cục bộ thuộc mạng của nó
- B2:Máy chủ tên miền cục bộ này kiểm tra trong cơ sở dữ liệu của nó có chứa cơ sở dữ liệu chuyển đổi từ tên miền sang địa chỉ IP của tên miền mà người sử
 dụng yêu cầu không. 
- B3:Trong trường hợp máy chủ tên miền cục bộ có cơ sở dữ liệu này, nó sẽ gửi trả lại địa chỉ IP của máy có tên miền nói trên.
- B4:Trong trường hợp máy chủ tên miền cục bộ không có cơ sở dữ liệu về tên miền này nó sẽ hỏi lên các máy chủ tên miền ở mức cao nhất 
- B5:Máy chủ tên miền ở mức ROOT này sẽ chỉ cho máy chủ tên miền cục bộ địa chỉ của máy chủ tên miền quản lý các tên miền có đuôi .VN.
- B6:Máy chủ tên miền cục bộ gửi yêu cầu đến máy chủ quản lý tên miền có đuôi (.VN) tìm tên miền whitehat.vn. 
- B7: Máy chủ tên miền quản lý các tên miền.VN sẽ gửi lại địa chỉ của máy chủ quản lý tên miền whitehat.vn
-B8: Máy chủ tên miền cục bộ sẽ hỏi máy chủ quản lý tên miền vnn.vn này địa chỉ IP của tên miền whitehat.vn. 
- B9:Do máy chủ quản lý tên miền vnn.vn có cơ sở dữ liệu về tên miền whitehat.vn nên địa chỉ IP của tên miền này sẽ được gửi trả lại cho máy chủ tên miền 
 cục bộ
- B10:Máy chủ tên miền cục bộ chuyển thông tin tìm được đến máy của người sử dụng. Người sử dụng dùng địa chỉ IP này để kết nối đến server chứa trang web có
 địa chỉ whitehat.vn 
 # Tham khảo:
 [1] http://svuit.vn/threads/chapter-4-3-dns-server-va-dnz-zone-part-3-252/
 
 [2] https://whitehat.vn/threads/cach-domain-name-system-dns-hoat-dong.472/
 
 [3] https://anninhmang.edu.vn/cau-hinh-dns-server-tren-centos/
 
 [4] https://github.com/hocchudong/ghichep-DNS/blob/master/docs/dns-install.md
 
 [5] https://vi.wikipedia.org/wiki/H%E1%BB%87_th%E1%BB%91ng_ph%C3%A2n_gi%E1%BA%A3i_t%C3%AAn_mi%E1%BB%81n#T.E1.BB.95ng_quan
 
 
  
