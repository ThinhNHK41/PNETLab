**Báo Cáo Công Việc Tuần 2**

# Tổng quát kết quả Pnetlab

![image](https://user-images.githubusercontent.com/92511177/137463652-ca92afa3-ec99-43e6-a5b5-dc2b09a476ba.png)

# LLDP and DHCPv6

## Mục tiêu Lab: 

-   Trong bài lab này ta sẽ học về cấu hình tự động địa chỉ IPv6,
    DHCPv6, IPv6 traffic filtering, và LLDP. Cả cấu hình tự động và
    DHCPv6 đều là một phần của giao thức IPv6 Neighbor Discovery. LLDP
    là một chuẩn đối tác mở của CDP và được sử dụng để khám phá các hàng
    xóm trên các cổng Ethernet.

## Mô hình Lab:

> ![](.//media/image1.png)
> 
>
> Câu 1: Cấu hình Ethernet 0/0 của R1 với địa chỉ IPv6
> 2001:43:123:14::1/64. Cấu hình R1 cung cấp địa chỉ IPv6 đến cổng
> Ethernet0/0 của R4 liên kết trong vùng 2001:43:123:14::/64. R4 cũng
> nên được nhận như là định tuyến mặc định từ R1.
>
> ![](.//media/image2.png)
> 
>
> ![](.//media/image3.png)
> 
>
> IPv6 unicast-routing nên được kích hoạt trên các router cho việc giao
> tiếp IPv6 được thực hiện. Tự động cấu hình IPv6 dựa trên giao thức
> Neighbor Discovery. R1 đang gửi prefix 2001:43:123:14::/64 thông qua
> giao thức khám phá hàng xóm với một khoảng thời gian 7200 giây (2
> giờ). R4 được cấu hình để nhận địa chỉ IPv6 và định tuyến mặc định qua
> tự động cấu hình, nó sẽ lấy prefix từ R1 và thêm địa chỉ MAC của nó
> vào prefix và tạo nên một địa chỉ IPv6 duy nhất cho cổng đó. Chú ý địa
> chỉ MAC sẽ khác dẫn dến tạo ra một địa chỉ khác nhưng prefix thì luôn
> giống nhau.
>
> Câu 2: Cấu hình R1 cung cấp thêm mạng con 2001:43:123:100::/80 tới R4
> để sử dụng cho các cổng khác. R1 cũng nên cung cấp tên domain của
> google.com và DNS Server 2001:43:123:14::1 tới R4 thông qua đường
> E0/0.
>
> ![](.//media/image4.png)
> 
>
> ![](.//media/image5.png)
> 
>
> R1 được cấu hình với local pool 2001:43:123:100::/64 mà nó sẽ sử dụng
> để cho đi /80 ra khỏi nó. Trong DHCP Pool R1 cũng sẽ có cấu hình cho
> tên miền và DNS theo yêu cầu. R4 đang yêu cầu thông tin DHCP từ R1
> bằng cách tự cấu hình như một máy khách DHCP. Pd là viết tắt của tiền
> tố và "DHCP-FROM-R1" có ý nghĩa cục bộ. Do ảnh hưởng của các cấu hình
> trên, R4 sẽ nhận tiền tố 2001:43:123:100::/80 và sẽ có định tuyến đến
> tiền tố đó được cài đặt tự động trỏ đến Null0 có nghĩa là tôi sở hữu
> tiền tố này. R1 sẽ nhận được định tuyến tĩnh đến 2001:43:123:100::/80
> tự động được cài đặt trong bảng định tuyến của nó trỏ đến giao diện
> Ethernet của R4.
>
> Câu 3: Gán prefix 2001:43:123:100:/80 (DHCP-FROM-R1) tới cổng E1/0 của
> R4 với ::4/80 là địai chỉ host. Gán 2001:43:123:100:3/80 trên E1/0 của
> R3 và cấu hình định tuyến mặc định trên R3 đi qua 2001:43:123:100:4.
> R1 nên ping được 2001:43:123:100::3.
>
> ![](.//media/image6.png)
> 
>
> ![](.//media/image7.png)
> 
>
> Ta cấu hình 2001:43:123:100::3 trên e1/2 của R3 và cấu hình định tuyến
> mặc định đi qua R4. Điểm tiếp cho định tuyến tĩnh mặc định có thể là
> địa chỉ linklocal của mạng kết nối hoặc nó có thể chỉ là địa chỉ
> global next hop. Nếu sử dụng địa chỉ link local của remote router, ta
> sẽ cần cấu hình đúng các cổng next hop.
>
> ![](.//media/image8.png)
> 
>
> Câu 4: Gán tĩnh địa chỉ IPv6 tới các cổng còn lại trong mô hình theo
> bảng sau:
>
> ![](.//media/image9.png)
> 
>
> ![](.//media/image10.png)
> 
>
> ![](.//media/image11.png)
> ![](.//media/image12.png)
> 
>
> ![](.//media/image13.png)
> 
>
> ![](.//media/image14.png)
> 
>
> ![](.//media/image15.png)
> 
>
> ![](.//media/image16.png)
> 
>
> Câu 5: Cấu hình OSPFv3 cho area 0 trên tất cả các cổng trong mô hình
>
> ![](.//media/image17.png)
> 
>
> ![](.//media/image18.png)
> 
>
> ![](.//media/image19.png)
> 
>
> ![](.//media/image20.png)
> 
>
> ![](.//media/image21.png)
> ![](.//media/image22.png)
> 
>
> ![](.//media/image23.png)
> ![](.//media/image24.png)
> 
>
> ![](.//media/image25.png)
> 
>
> ![](.//media/image26.png)
> 
>
> Câu 6: Cấu hình IPv6 traffic filter, R2'LAN trên E0/0
> (2001:43:123:2::/64) không nên đến được R3'LAN trên E0/0
> (2001:43:123:3::/64)
>
> Trước khi thêm trafic filter R2 nên ping 2001:43:123:3::3 đến từ LAN
>
> ![](.//media/image27.png)
> 
>
> Bây giờ ta sẽ cấy hình trafic filter trên R3 để block bất kì traffic
> nào đến từ LAN R2 và đến LAN R3
>
> ![](.//media/image28.png)
> 
>
> ![](.//media/image29.png)
> 
>
> Câu 7: Cấu hình LLDP trên tất cả các cổng ethernet và đảm bảo R1 có
> thể thấy R2 thông qua LLDP
>
> LLDP là một tiêu chuẩn của CDP cho mạng IEEE 802 (Principally
> Ethernet). Nó thì hữu dụng khi kết nối các thiết bị Cisco đến các
> thiết bị khác hoặc điện thoại non-cisco IP.

![](.//media/image30.png)
![](.//media/image31.png)


![](.//media/image32.png)
![](.//media/image33.png)


LLDP được cấu hình tương tự như CDP với những khác biệt nhỏ. LLDP cần
được chạy trên global configuration mode. Sau đó, chúng ta cần kích hoạt
tính năng gửi và nhận các gói lldp trên mỗi cổng mà chúng ta muốn. Sau
khi được bật theo mặc định, nó sẽ chạy trên tất cả giao diện.

Lưu ý: LLDP chỉ hoạt động trên công 802.1 (Ethernet) không hoạt động
trên công ethernet.

![](.//media/image34.png)
![](.//media/image35.png)
![](.//media/image36.png)


![](.//media/image37.png)


LLDP được bật trên tất cả các cổng theo mặc định, nhưng nhìn vào đầu ra,
chúng ta không chỉ thấy Rx & Tx trên các cổng mà còn thứ gì đó ở đầu bên
kia. Trên giao diện bị trục trặc, LLDP Tx ở INIT và Rx ở trạng thái WAIT
PORT OPER.

![](.//media/image38.png)

![](.//media/image39.png)


![](.//media/image40.png)


![](.//media/image41.png)


# IPv6 Tunnels and OSPFv3 Lab

## Mục tiêu Lab:

-   Lab này tập trung để hiểu về việc triển khai và cấu hình đường hầm
    trong Cisco IOS router. Các công nghệ bổ sung bao gồm xác thực và
    bảo mật OSPFv3.

## Mô hình Lab:

> ![](.//media/image42.png)
> 
>
> Câu 1: Cấu hình hostname, địa chỉ IP trên tất cả router như trong mô
> hình mạng.
>
> ![](.//media/image43.png)
> 
>
> ![](.//media/image44.png)
> 
>
> ![](.//media/image45.png)
> 
>
> ![](.//media/image46.png)
> 
>
> Câu 2: Kích hoạt EIGRP trên tất cả router như trong mô hìn. Xác nhận
> cấu hình EIGRP.
>
> ![](.//media/image47.png)
> 
>
> ![](.//media/image48.png)
> 
>
> ![](.//media/image49.png)
> 
>
> ![](.//media/image50.png)
> 
>
> Xác nhận lại cấu hình EIGRP sử dụng lệnh **show ip eigrp neighbors**
>
> ![](.//media/image51.png)
> 
>
> ![](.//media/image52.png)
> 
>
> ![](.//media/image53.png)
> 
>
> ![](.//media/image54.png)
> 
>
> Câu 3: Cấu hình đường hầm IPv6 tĩnh giữa R1 và R4. Đảm bảo có thể ping
> thông qua đường hầm. Xác nhận lại cấu hình

-   Khi cấu hình đường hầm IPv6 tĩnh (thủ công), phải chỉ định IPv6 làm
    giao thức khách và IPv4 làm cả giao thức đóng gói và truyền tải cho
    đường hầm IPv6 thủ công bằng cách sử dụng lệnh cấu hình cổng ipv6ip
    chế độ đường hầm.

> ![](.//media/image55.png)
> 
>
> ![](.//media/image56.png)
> 
>
> Xác nhận lại cấu hình sử dụng lệnh **show interface**
>
> Câu 4: Cấu hình OSPFv3 thông qua đường hầm R1-R4. Sử dụng OSPF area 0.
> Quảng bá các mạng LAN trên R1 và R4 là định tuyến inter-area OSPF. Xác
> nhận R1 và R4 có thể ping LAN-to-LAN.

-   Các yêu cầu cấu hình OSPFv3 của tác vụ rất đơn giản. Để quảng cáo
    mạng con LAN được kết nối dưới dạng các tuyến OSPF liên khu vực, cần
    gán chúng cho các khu vực khác nhau.

> ![](.//media/image57.png)
> ![](.//media/image58.png)
> 
>
> Câu 5: Để bảo mật, hãy cấu hình xác thực khu vực cho xương sống OSPF.
> Sử dụng những thứ sau khi cấu hình các tham số xác thực:

-   Sử dụng Security Parameters Index (SPI) là 256

-   Sử dụng xác thực Secure Hash Algorithm (SHA)

-   Sử dụng key 1234567890abcdef1234567890abcdef12345678

> Xác nhận lại cấu hình.

-   OSPFv3 hỗ trợ xác thực và mã hóa để bảo mật. Để định cấu hình khu
    vực OSPFv3 xác thực, bạn cần sử dụng **area \<area> authentication
    ipsec spi \<size> \[md5\|sha1\] \<key>**

> ![](.//media/image59.png)
> 
>
> ![](.//media/image60.png)
> 
>
> ![](.//media/image61.png)
> 

# IPv6 OSPFv3 Lab

## Mục tiêu Lab:

-   Lab này tập trung để hiểu về việc triển khai và cấu hình đường hầm
    trong Cisco IOS router. Các công nghệ bổ sung bao gồm Frame Relay,
    tóm tắt và Path Control.

    a.  ## Mô hình Lab:

> ![](.//media/image62.png)
> 
>
> Câu 1: Cấu hình hostname và địa chỉ IP cho tất cả router như trong mô
> hình
>
> ![](.//media/image63.png)
> 
>
> ![](.//media/image64.png)
> 
>
> ![](.//media/image65.png)
> 
>
> Câu 2: Kết nối nên chỉ là các địa chỉ Link-Local. Xác nhận cấu hình
>
> ![](.//media/image66.png)
> 
>
> Câu 3: Cấu hình OSPF thông qua kết nối Frame Replay WAN giữa R1, R2 và
> R4. Đảm bảo không chọn DR/BDR trên WAN. Ngoài ra, OSPFv3 nên sử dụng
> các gói tin Unicast để gửi các tin nhắn giao thức. Xác nhận cấu hình
>
> ![](.//media/image67.png)
> 
>
> ![](.//media/image68.png)
> 
>
> Câu 4: Điều hướng mạng LAN kết nối đến R1 thông qua OSPF. Cấu hình R1
> để chỉ định tuyến đơn được quảng bá đến R2 và R4. Xác nhận rằng các
> router có thể ping 3 mạng LAN kết nối đến R1 mặc dù chỉ có một định
> tuyến đơn cho các mạng trong bảng định tuyến
>
> ![](.//media/image69.png)
> 
>
> ![](.//media/image70.png)
> 
>
> ![](.//media/image71.png)
> 
>
> Câu 5: Quảng bá mạng kết nối đến R2 và các cổng LAN R4 qua OSPF. Đừng
> điều hướng mạng này vào OSPF. Các định tuyến nên được nhận là định
> tuyến intrer-area route trên R1. Đảm bảo rằng không có tin nhắn OSPFv3
> được gửi ra các cổng này. Xác nhận cấu hình
>
> ![](.//media/image72.png)
> 
>
> ![](.//media/image73.png)
> 
>
> Câu 6: Cấu hình OSPF để R1 ưu tiên đường đi qua R2 đến mạng IPv6
> 3ffe:abcd:1111:5/64 kết nối R2 và R4. Bạn không được cho phép cấu hình
> trên R1 đến khi hoàn thành câu này. Ngoài ra, không được điều chỉnh
> băng thông cổng hoặc giá trị cost, hoặc giá trị administrative
> distance. Cuối cùng, không được sử dung điều hướng hoặc định tuyến
> tĩnh để hoàn thành câu này. Xác nhận cấu hình.

![](.//media/image74.png)


![](.//media/image75.png)


# Cài đặt hệ thống giám sát Pnetlab (Nagios)

## a. Cài đặt Nagios Server trê CentOS 8 #a.-cài-đặt-nagios-server-trê-centos-8 .list-paragraph

> **Thông số của VM:**

  -------------------------------------------------------------------------
  **Hostname**   **RAM**       **Disk**      **CPU**       **IP**
  -------------- ------------- ------------- ------------- ----------------
  nagios server  1 Gb          20 Gb         1 Core        192.168.17.148

  -------------------------------------------------------------------------

> **Thực hiện:**

-   Cài đặt một số gói cần thiết

> ![](.//media/image76.png)
> 

-   Tắt selinux

> ![](.//media/image77.png)
> 

-   Tắt firewall

> ![](.//media/image78.png)
> 

-   Tạo ra một user để tiến trình của nagios có thể chạy trên user này

> ![](.//media/image79.png)
> 

-   Dùng wget để download và cài đặt nagios

> yum groupinstall \"Development Tools\" -y
>
> ![](.//media/image80.png)
> 

-   Tạo ra một user để truy cập website nagios

> ![](.//media/image81.png)

-   Download và cài đặt nagios plugins

> ![](.//media/image82.png)
> 

-   Bắt đầu dịch vụ nagios và httpd

> ![](.//media/image83.png)
> 

-   Truy cập vào web site vào đăng nhập với tài khoản mật khẩu ở bước 6

> ![](.//media/image84.png)
> 
>
> Sau khi cài đặt xong một nagios server thì nó sẽ chỉ giám sát CPU;
> RAM; Disk,... tại nagios server. Để có thể giám sát được nhiều dịch vụ
> với các máy từ xa thì ta phải cài đặt thêm plugins.

## b. Sử dụng Nagios Server để giám sát PNETLab #b.-sử-dụng-nagios-server-để-giám-sát-pnetlab .list-paragraph

> Để giám sát PNETLab từ xa với nagios, ta có thể sử dụng nhiều loại
> plugins khác nhau. Ở đây ta sẽ sử dụng plugins NRPE để giám sất
> PNETLab.
>
> **Mô hình và kịch bản:**
>
> ![](.//media/image85.png)
> 
>
> Kịch bản: Cìa đặt Nagios trên máy được gọi là Nagios Server (Ở phần
> a). Cài đặt và sử dụng NRPE để có thể giám sát được máy PNETLab từ xa.

  -------------------------------------------------------------------------
  **Hostname**   **IP**           **CPU**       **RAM**       **Disk**
  -------------- ---------------- ------------- ------------- -------------
  PNETLab        192.168.17.136   4 Core        4 Gb          100 Gb

  Nagios server  192.168.17.149   1 Core        1 Gb          20 Gb
  -------------------------------------------------------------------------

> **Thực hiện:**
>
> **Trên PNETLab:**

1.  Cài đặt các gói phụ kiện cần thiết

> yum install -y gcc glibc glibc-common gd gd-devel make net-snmp
> openssl-devel

2.  Tạo user để NRPE dùng nó để xử lý tiến trình (user nagios ta đã tạo
    ở bước 4 phần a)

> ![](.//media/image86.png)
> 

3.  Download file plugins

> ![](.//media/image87.png)
> 

4.  Giải nén và cài đặt plugins

> ![](.//media/image88.png)
> 

5.  Sau đó thêm user vào group và cấp quyền sử dụng tập lưu NRPE cho
    usser nagios và group nagios

> ![](.//media/image89.png)
> 

6.  Cài đặt xinetd

> ![](.//media/image90.png)
> 

7.  Download và cài đặt NRPE

> ![](.//media/image91.png)
> 

8.  Sửa file /usr/local/nagios/etc/nrpe.cfg để có thể nghe thấy nagios
    server

> ![](.//media/image92.png)
> 
>
> ![](.//media/image93.png)
> 

9.  Sửa file /etc/services sử dụng port 5666 cho NRPE. Thêm dòng sau đây

> ![](.//media/image94.png)
> 
>
> ![](.//media/image95.png)
> 

10. Chạy các dịch vụ

> ![](.//media/image96.png)
> 

11. Kiểm tra xem đã cài đặt và sử dụng được NPRE chưa

> ![](.//media/image97.png)
> 
>
> **Trên Nagios Server:**

1.  Download NRPE

> ![](.//media/image98.png)
> 

2.  GIải nén file vừa download

> ![](.//media/image99.png)
> 

3.  Cài đặt lệnh NRPE

> ![](.//media/image100.png)
> 

4.  Kiểm tra xem đã sử dụng được NRPE chưa

> ![](.//media/image101.png)
> 
>
> **Thêm một host vào để nagios server giám sát**

1.  Thêm vào file /usr/local/nagios/etc/nagios.cfg. Khai báo file chứa
    thông tin của host cần giám sát

> ![](.//media/image102.png)
> 
>
> ![](.//media/image103.png)
> 

2.  Khai báo lệnh NRPE vào file vi
    /usr/local/nagios/etc/objects/commands.cfg

> ![](.//media/image104.png)
> 
>
> ![](.//media/image105.png)
> 

3.  Thêm thông tin của host vào file /usr/local/nagios/etc/hosts.cfg

> ![](.//media/image106.png)
> 
>
> ![](.//media/image107.png)
> 

4.  Thêm thông tin của service vào file
    /usr/local/nagios/etc/services.cfg

> ![](.//media/image108.png)
> 
>
> ![](.//media/image109.png)
> 

5.  Kiểm tra cấu hình xem đúng hay sai kết quả giống hiện ra ở dưới sẽ
    là đúng và không có lỗi xảy ra

> ![](.//media/image110.png)
> 

6.  Khởi động lại dịch vụ nagios

> ![](.//media/image111.png)
> 
>
> ![](.//media/image112.png)
> 
>
> ![](.//media/image113.png)
> 

## Cảnh báo qua mail khi sử dụng Nagios

> Thực hiện mọi thứ trên Nagios Server

1.  Cài đặt gói mail postfix

> ![](.//media/image114.png)
> 

2.  Tạo file lưu trữ user và pass của mail trong file

> ![](.//media/image115.png)
> 
>
> ![](.//media/image116.png)
> 

3.  Khai báo file chứa địa chỉ mail tại file cấu hình chính của dịch vụ
    mail

> ![](.//media/image117.png)
> 
>
> ![](.//media/image118.png)
> 

4.  Thiết lập chế độ less secure của Gmail

> Có rất nhiều mail chưa bật tính năng này. Ta cần phải bật tính năng
> này để có thể sử dụng gửi mail bằng Nagios
>
> ![](.//media/image119.png)
> 

5.  Cấp quyền sử dụng vào đọc cho file chứa user passwd của mail mình sử
    dụng để gửi đến các mail cần nhận cảnh báo

> ![](.//media/image120.png)
> 

6.  Khởi động dịch vụ postfix

> ![](.//media/image121.png)
> 

7.  Kiểm tra xem dịch vụ postfix đã hoạt động hay chưa

> ![](.//media/image122.png)
> 

8.  Khai báo contact nhận cảnh báo gmail

> ![](.//media/image123.png)
> 
>
> ![](.//media/image124.png)
> 

9.  Khởi động lại dịch vụ Nagios

> ![](.//media/image125.png)
> 

10. Kiểm tra dịch vụ cảnh báo qua gmail. Tắt client và kiểm tra mail
    trong contact

> ![](.//media/image126.png)
> 
>
> Nó sẽ giúp nhận được thông báo rằng máy mình đã bị tắt, giúp kịp thời
> nhận ra và kiểm tra ngay lập tức.
