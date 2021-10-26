# 1. DMVPN Phase 3 with IPSec

## a. Khái niệm DMVPN

> \- Dynamic Multipoint Virtual Private Network (DMVPN) là sự kết hợp
> của các công nghệ IPSec, mGRE và NHRP. Là một giải pháp phần mềm trên
> hệ điều hành Cisco dùng để xây dựng IPSec + GRE VPN dễ dàng và có khả
> năng mở rộng.
>
> \- Đồng thời nó đáp ứng cho như cầu ngày càng tăng của các công ty
> doanh nghiệp để có thể kết nối các văn phòng chi nhánh với các trụ sở
> chính và giữa các chi nhánh với nhau trong khi vẫn giữ chi phí thấp,
> giảm thiểu độ phức tạp cấu hình và tăng tính linh hoạt của hệ thống
> mạng.

## b. Cách dạng triển khai

> \- Trong DMVPN, 1 router (thường đặt ở trụ sở chính) sẽ đóng vai trò
> Hub còn các router ở các chi nhánh sẽ là các Spoke. DMVPN bao gồm hai
> thiết kế triển khai chủ yếu:

-   Hub to Spoke: được sử dụng để kết nối từ trụ sở đến chi nhánh

-   Spoke to Spoke: được sử dụng để kết nối giữa các chi nhánh

> ![](.//media/image1.png)
> 
>
> Trong cả 2 trường hợp Router Hub bắt buộc phải có địa chỉ IP public
> tĩnh, trong khi Router Spoke có thể sử dụng IP tĩnh hoặc động.
>
> \- Các Spoke đều có các kết nối đến Hub thông qua mGRE Tunnel (Hub to
> Spoke Tunnel), còn các Spoke kết nối với nhau qua Spoke to Spoke
> Tunnel động, được khởi tạo khi có nhu cầu giao tiếp giữa các chi
> nhánh.
>
> \- DMVPN sử dụng NHRP để xác định địa chỉ IP Public hiện tại của các
> Spoke. Các Spoke khi được cấu hình DMVPN sẽ khai báo địa chỉ IP Public
> của mình tới Hub và truy vấn địa chỉ IP của Spoke khác khi cần tọa
> Tunnel.
>
> \- DMVPN sử dụng multiple GRE (mGRE) Tunnel thay vì GRE để giảm số
> lượng Tunnel cần tạo. mGRE không có tunnel destination được cấu hình
> nên mGRE sẽ sử dụng NHRP để xác định IP đích khi cần khởi tạo Tunnel.

## c. Các thành phần trong DMVPN

> \- Các thành phần cần thiết để triển khai một hệ thống mạng doanh
> nghiệp, sử dụng DMVPN bao gồm:

-   Hệ thống Hub và Spoke là những thiết bị hỗ trợ tốt trong việc tạo
    kết nối DMVPN. Hệ thống Hub và Spoke phổ biến nhất vẫn là Router của
    Cisco.

-   Cloud dùng để kết nối được giữa Hub và Spoke. Cloud ở đây ám chỉ nhà
    cung cấp dịch vụ Internet (ISP). Cloud này có thể là Frame-Reply,
    ATM, Leased Lines.

## d. Ưu điểm của việc sử dụng DMVPN

> \- DMVPN cho phép mở rộng những mạng IPSec VPN. Ngoài ra nó còn có một
> số thuận lợi như:

-   Giảm độ phức tạp khi cấu hình trên router hub mà nó cung cấp khả
    năng thêm nhiều kênh một cách tự động mà không đụng đến cấu hình của
    hub.

-   Bảo đảm các packet được mã hóa khi truyền đi

-   Hỗ trợ nhiều giao thức định tuyến động chyaj trên DMVPN Tunnels

-   Khả năng thiết lập động và trực tiếp giữa các kênh spoke-to-spoke
    IPSec giữa các site mà không cần thông qua hub (nhờ mGRE và NHRP)

-   Hỗ trợ các spoke router với những địa chỉ vật lý động (được cấp vởi
    ISP)

## e. Mô hình chung DMVPN

> \- Với việc sử dụng DMVPN chúng ta sẽ giải quyết được những hạn chế
> trên và làm cho hệ thống trở nên mở rộng và linh động hơn, bằng cách
> sử dụng các giao thức mGRE và NHRP:
>
> ![](.//media/image2.png)
> 

-   Ở mỗi spoke, chúng ta không cần phải dùng một địa chỉ tĩnh nữa, mà
    có thể sử dụng địa chỉ IP động do ISP cung cấp. Vì mGRE chỉ yêu cầu
    xác định địa chỉ nguồn, còn địa chỉ đích thì sẽ nhờ một giao thức
    khác xác định. Trên router HUB cũng bắt buộc phải là một địa chỉ
    tĩnh.

-   Trên router HUB, bây giờ chỉ cần cấu hình một tunnel mGRE. Nếu thêm
    một spoke nào nữa thì trên HUB cũng không cần phải cấu hình thêm.
    Điều này làm giảm tải ở router HUB.

-   Khi sử dụng mGRE thì việc định địa chỉ đích sẽ nhờ vào một giao thức
    khác, đó là NHRP.

\- Như vậy, việc sử dụng DMVPN đem lại nhiều thuận lợi hơn so với VPN
thông thường.

\- DMVPN phase:

-   Phase 1: Tính năng của Hub và Spoke

-   Phase 2: Tính năng của Spoke-to-Spoke

-   Phase 3: Khả năng thay đổi spoke-to-spoke để quy mô các mạng được mở
    rộng.

##  f. DMVPN Phase 3

\- Ở giai đoạn 3 này nó sẽ cho phép các spoke xây dựng đường hầm
spoke-to-spoke và để vượt qua hạn chế giai đoạn 2 bằng cách sử dụng các
thông báo chỉ dẫn lưu lượng NHRP từ trung tâm để báo hiệu cho các spoke
rằng tồn tại một con đường tốt hơn dẫn đến mạng đích.

\- Ở phase 3 cấu hình dựa trên 4 bước:

-   Xác định cổng Tunnel (bắt buộc)

-   Xác định NHRP (bắt buộc)

-   Xác định quy trình EIGRP (bắt buộc)

-   Xác định cấu hình IPSec (Tùy chọn)

> \- Trong ví dụ sau, ta có 3 router gồm 1 HUB (Ciscozine) và 2 spoke.
> Địa chỉ IP như sau:
>
> ![](.//media/image3.png)
> 
>
> ![](.//media/image4.png)
> 
>
> ![](.//media/image5.png)
> 
>
> ![](.//media/image6.png)
> 
>
> ![](.//media/image7.png)
> 

### Xác định cổng Tunnel (Bắt buộc)

> \- Cho phép một cổng đơn GRE hỗ trợ nhiều tunnel, đơn giản hóa kích
> thước và phức tạp hóa cấu hình

-   HUB

> interface Tunnel1
>
> description DMVPN-HUB
>
> ip address 10.0.1.1 255.255.255.0 ! IP address of the tunnel
>
> ip mtu 1400
>
> ip tcp adjust-mss 1360
>
> tunnel source Ethernet1/0 ! The tunnel source is the \"outside\"
> interface
>
> tunnel mode gre multipoint ! The tunnel type: multipoint GRE
>
> tunnel key 101

-   Spoke2

> interface Tunnel1
>
> description DMVPN-SPOKE2
>
> ip address 10.0.1.2 255.255.255.0 ! IP address of the tunnel
>
> ip mtu 1400
>
> ip tcp adjust-mss 1360
>
> tunnel source Ethernet1/0 ! The tunnel source is the \"outside\"
> interface
>
> tunnel mode gre multipoint ! The tunnel type: multipoint GRE
>
> tunnel key 101

-   Spoke3

> interface Tunnel1
>
> description DMVPN-SPOKE2
>
> ip address 10.0.1.3 255.255.255.0 ! IP address of the tunnel
>
> ip mtu 1400
>
> ip tcp adjust-mss 1360
>
> tunnel source Ethernet1/0 ! The tunnel source is the \"outside\"
> interface
>
> tunnel mode gre multipoint ! The tunnel type: multipoint GRE
>
> tunnel key 101

\- Chú ý: gói MTU được thiết lập thành 1400 bytes do chi phí GRE và
IPSec, trong khi TCP MSS tối đa thấp hơn 40 byte so với MTU (20 bytes IP
header + 20 bytes IP header).

\- Sau đây là chi tiết gói IPv4:

![](.//media/image8.png)


New IPv4 Header (Tunnel Mode): 20 bytes

SPI (ESP Header): 4 bytes

Sequence (ESP Header): 4 bytes

ESP-AES (IV): 16 bytes

New IPv4 Header (GRE): 20 bytes

GRE Header + Tunnel Key: 8 bytes

**Original Data Packet: 14000 bytes**

ESP Pad (ESP-AES): 10 bytes

Pad length (ESP Trailer): 1 byte

Next Header (ESP Trailer): 1 byte

ESP-SHA-256-HMAC ICV (ESP Trailer): 16 bytes

Total IPSec Packet Size: 1500 bytes

**Lưu ý:** Khóa id tunnel được sử dụng như một hình thức bảo mật yếu để
ngăn chặn việc cấu hình không đúng hoặc đưa các gói từ nguồn nước ngoài
vào. Chìa khóa phải giống nhau trong tất cả các đường hầm.

### Xác định NHRP (Bắt buộc)

> \- Cho phép các spoke được triển khai với các địa chỉ IP công cộng
> được chỉ định động (nghĩa là đằng sau bộ định tuyến của ISP). Hub duy
> trì một cơ sở dữ liệu NHRP về các địa chỉ giao diện công khai của mỗi
> spoke. Mỗi spoke đăng ký địa chỉ thực của nó khi nói khởi động, khi nó
> cần xây dựng các đường hầm tunnel trực tiếp với các nạn nhân khác, nó
> sẽ truy vấn cơ sở dữ liệu NHRP để biết địa chỉ thực của các spoke
> đích.
>
> \- HUB
>
> interface Tunnel1
>
> ip nhrp authentication CiscoPWD ! NHRP authentication key
>
> ip nhrp map multicast dynamic
>
> ip nhrp network-id 101 ! NHRP identifier
>
> ip nhrp holdtime 300 ! Seconds that NHRP NBMA addresses are advertised
> as valid in positive NHRP responses
>
> ip nhrp redirect ! Mandatory to enable DMVPN phase3 on the hub router
>
> **Lưu ý:** Lệnh \"**ip nhrp map multicast dynamic**\" cho phép NHRP tự
> động thêm các router đến multicast NHRP mapping khi các spoke router
> khởi tạo mGRE tunnel và đăng ký unicast NHRP mapping của chúng. Điều
> này là cần thiết để cho phép các giao thức định tuyến động hoạt động
> trên các đường hầm mGRE giữa hub và các spoke.
>
> \- Spoke2 / Spoke3
>
> interface Tunnel1
>
> ip nhrp authentication CiscoPWD ! NHRP authentication key
>
> ip nhrp map 10.0.1.1 17.17.17.1
>
> ip nhrp map multicast 17.17.17.1 ! Enable to receive multicast or
> broadcast packets
>
> ip nhrp network-id 101 ! NHRP identifier
>
> ip nhrp holdtime 300 ! Seconds that NHRP NBMA addresses are advertised
> as valid in positive NHRP responses
>
> ip nhrp nhs 10.0.1.1
>
> ip nhrp shortcut ! Mandatory to enable DMVPN phase3 on the spoke
> router
>
> Lệnh \"**ipnhrp map 10.0.1.1 17.17.17.1**\" định cấu hình ánh xạ tĩnh
> IP-to-NBMA của HUB router, trong khi lệnh \"**ip nhrp nhs 10.0.1.1**\"
> xác định địa chỉ IP của máy chủ next-hop (hub). Các lệnh này được yêu
> cầu trên toàn bộ các spoke router.
>
> **Lưu ý:** Chuỗi xác thực, thời gian lưu trữ và id mạng phải giống
> nhau trên tất cả đường hầm.

### Xác định quy trình EIGRP (Bắt buộc)

> \- Tìm hiểu mạng lưới giữa hub và các spoke: Chuỗi khóa được sử dụng
> để xác thực quy trình EIGRP; rõ ràng, nó phải giống nhau trên tất cả
> các router.
>
> HUB - Spoke2 - Spoke3
>
> key chain DMVPN
>
> key 1
>
> key-string eigrp-Ciscozine
>
> HUB
>
> router eigrp 100
>
> network 10.0.1.0 0.0.0.255 ! Used for neighborship
>
> network 192.168.1.0 ! Announce the 192.168.1.0/24 network
>
> passive-interface default
>
> no passive-interface Tunnel1
>
> no passive-interface Ethernet0/0
>
> interface Tunnel1
>
> ip authentication mode eigrp 100 md5 ! Enable MD5 authentication
> process
>
> ip authentication key-chain eigrp 100 DMVPN ! Enable authentication
> process using DMVPN key chain
>
> ip summary-address eigrp 100 192.168.0.0 255.255.0.0 ! Advertise a
> summary route
>
> Spoke2
>
> router eigrp 100
>
> network 10.0.1.0 0.0.0.255 ! Used for neighborship
>
> network 192.168.2.0 ! Announce the 192.168.2.0/24 network
>
> passive-interface default
>
> no passive-interface Tunnel1
>
> no passive-interface Ethernet0/0
>
> interface Tunnel1
>
> ip authentication mode eigrp 100 md5 ! Enable MD5 authentication
> process
>
> ip authentication key-chain eigrp 100 DMVPN ! Enable authentication
> process using DMVPN key chain
>
> Spoke3
>
> router eigrp 100
>
> network 10.0.1.0 0.0.0.255 ! Used for neighborship
>
> network 192.168.3.0 ! Announce the 192.168.3.0/24 network
>
> passive-interface default
>
> no passive-interface Tunnel1
>
> no passive-interface Ethernet0/0
>
> interface Tunnel1
>
> ip authentication mode eigrp 100 md5 ! MD5 authentication process
>
> ip authentication key-chain eigrp 100 DMVPN ! Enable authentication
> process using DMVPN key chain
>
> Ở cuối bước này, DMVPN đã hoạt động và có thể được sử dụng, nhưng ta
> có thể hoàn thành việc mã hóa và bảo vệ kiến trúc DMVPN với tất cả dữ
> liệu bằng IPSec.

### Xác định cấu hình IPSec (Tùy chọn)

> \- Bước cuối cùng này (tùy chọn) nhằm bảo vệ đường hầm mGRE với IPSec.
> Để tiến hành, bạn cần xác định chính sách/thông tin isakmp và hệ
> chuyển đổi/thông tin ipsec.
>
> HUB - Spoke2 - Spoke3
>
> crypto keyring VPN-KEYRING-WAN
>
> pre-shared-key address 0.0.0.0 0.0.0.0 key Ciscozine ! Define the
> preshared key
>
> crypto isakmp policy 10 ! Define the isakmp security settings
>
> encr aes
>
> hash sha256
>
> authentication pre-share
>
> group 5
>
> crypto isakmp profile WAN
>
> keyring VPN-KEYRING-WAN
>
> match identity address 0.0.0.0
>
> crypto ipsec transform-set TSET esp-aes 256 esp-sha256-hmac ! Define
> the ipsec security settings
>
> mode tunnel
>
> crypto ipsec profile IPSEC-PROFILE
>
> set transform-set TSET
>
> Sau đó, ta có thể gán thông tin IPSec cho cổng đường hầm:
>
> Interface Tunnel1
>
> tunnel protection ipsec profile IPSEC-PROFILE

# 2. DMVPN Phase 3 without IPSec

> \- Đối với DMVPN Phase 3 không có IPSec thì cũng sẽ cấu hình 3 bước
> (Xác định cổng đường hầm, Xác định NHRP, Xác định quy trình EIGRP) như
> trên và bỏ qua bước cuối (Xác định cấu hình IPSec). Đối với dạng DMVPN
> Phase 3 này thì ta sẽ không thể đảm bảo được tính bảo mật cho kiến
> trúc DMVPN và tất cả dữ liệu.

# 3. DMVPN Phase 1 with Static Mapping

> \- DMVPN Phase 1 là tính năng của Hub và Spoke.
>
> \- Ưu điểm của DMVPN phase 1 là:

-   Hub và spoke cấu hình đơn giản và nhỏ gọn

-   Hỗ trợ Multicast traffic từ Hub đến các spoke

-   Hỗ trợ địa chỉ cho các spoke một cách linh động

> \- Ta sẽ dùng lệnh sau để cấu hình Static Mapping với DMVPN Phase 1:
>
> **ip nhrp map multicast dynamic**

-   HUB: với dòng lệnh này cho ta biết đâu là router để forward gói
    multicast đến. Vì không biết địa chỉ IP của các spoke router nên ta
    cấu hình dynamic để tự thêm địa chỉ IP của spoke router vào danh
    sách multicast destination khi spoke đăng ký.

> **ip nhrp map** (vd: ip nhrp map 172.16.0.1 1.1.1.1)

-   Spoke: Trên spoke router sẽ tạo địa chỉ ip 172.16.0.1 để map vào
    tunnel và Hub NBMA (NonBroadcast Multicast Access) địa chỉ là
    1.1.1.1 và nó sẽ lưu NHRP vào cache spoke router.

> **ip nhrp map multicast** (vdL ip nhrp map multicast 1.1.1.1)

-   Spoke: Nơi sẽ nhận broadcast hay multicast traffic thông qua
    interface tunnel. Nhập địa chỉ NHRP vào đây vì nó sẽ dùng trong các
    giao thức routing (RIP, OSPF, EIGRP) yêu cầu multicast.

# 4. Vận hành giám sát hoạt động của Zabbix

> **a. Zabbix là gì ?**
>
> \- Zabbix là một giải giáp giảm sát dịch vụ hệ thống mạng phân tán mã
> nguồn mở nổi tiếng, có nhiều tính năng độc đáo và khả năng tùy biến
> cao. Zabbix có khả năng phục vụ cho hệ thống mạng tầm trung và lớn của
> doanh nghiệp hiện tại với mức chi phí đầu tư vừa phải.
>
> \- Zabbix được sáng lập bởi Alexei Vladishev và hiện tại được phát
> triển cũng như hỗ trợ bởi tổ chức Zabbix SIA. Zabbix được viết và phát
> hành dưới bản quyền General Public License GPL phiên bản 2. Zabbix sử
> dụng các cơ chế thông báo vấn đề linh hoạt cho quản trị viên như
> email, sms, OTT App,\... Zabbix cũng cung cấp báo cáo và dữ liệu cực
> kì chính xác dựa trên cơ sở dữ liệu đã thu thập được từ thiết bị mạng.
>
> \- Tất cả báo cáo, thống kê cũng như cấu hình thông số của Zabbix có
> thể dễ dàng truy cập qua giao diện web tinh tế đẹp mắt. Chúng ta theo
> dõi được tình trạng hệ thống thiết bị server, dịch vụ,\...
>
> ![](.//media/image9.png)
> 
>
> **b. Ưu / Nhược điểm của Zabbix**
>
> \- Ưu điểm của dịch vụ Zabbix

-   Tự động tìm phát hiện server và hệ thống mạng

-   Hỗ trợ server cài đặt trên dòng hệ điều hành Unix/Linux

-   Hỗ trợ máy trạm client nhiều hệ điều hành

-   Giao diện web cực kì tinh tế và đẹp mắt

-   Có thông báo sự cố qua email hoặc OTP App

-   Có báo cáo, biểu đồ qua giao diện web đẹp mắt

-   Kiểm tra theo dõi việc đăng nhập

-   Linh động trong việc phân quyền người dùng

-   Mã nguồn mở, chi phí đầu tư thấp

-   Nhiều plugin hỗ trợ cho các dịch vụ hệ thống khác nhau

![](.//media/image10.png)


\- Nhược điểm của dịch vụ Zabbix

-   Không có giao diện web mobile hỗ trợ

-   Không phù hợp với hệ thống mạng lớn hơn 1000+ node thiết bị client
    cần giám sát. Lúc này phát sinh vấn đề hiệu suất về PHP và Database

-   Thiết kế Template/alerting rule đôi khi khá phức tạp.

**c. Yêu cầu phần cứng**

\- Tùy theo số lượng máy chủ hoặc thiết bị mạng cần giám sát mà ta sẽ có
các mức cấu hình phần cứng phù hợp cho dịch vụ Zabbix Server. Phần cứng
tối thiểu gồm:

-   CPU: 2 core

-   RAM: 1GB

-   Disk: 50GB

![](.//media/image11.png)


**d. Các thành phần của hệ thống giám sát Zabbix**

\- Zabbix Server: Đây là ứng dụng chương trình dịch vụ chính của dịch vụ
Zabbix. Zabbix Server sẽ chịu trách nhiệm cho các hoạt động kiểm tra
dịch vụ mạng từ xa, thu thập thông tin, lưu trữ, hiển thị, cảnh báo,\...
từ đó các quản trị viên có thể thao tác giám sát hệ thống tốt nhất.

![](.//media/image12.png)


\- Zabbix Proxy: là một máy chủ được dùng cho việc quản lý nhiều nhánh
hệ thống ở xa, hoặc ở lớp mạng khác nhau. Từ Zabbix Proxy sẽ thu thập
các thông tin thiết bị mạng rồi chuyển tiếp về cho máy chủ dịch vụ chính
Zabbix Server.

![](.//media/image13.png)


\- Zabbix Agent: là chương trình zabbix dùng để cài đặt lên các máy chủ
hoặc thiết bị phía client. Từ đó hỗ trợ kết nối từ Zabbix Server để lấy
các thông tin cần thiết từ client nhằm kiểm tra các tình trạng hệ thống
hoặc theo nhu cầu quản trị viên.

![](.//media/image14.png)


\- Giao diện web: cung cấp giao diện web trên nền tảng mã nguồn PHP cùng
phong cách metro tinh tế. Hiện tại có thể xem Zabbix là một trong những
ứng dụng có giao diện đẹp nhất, thiết kế vị trí tính năng bắt mắt và hợp
lý.

![](.//media/image15.png)


# Tài liệu tham khảo #tài-liệu-tham-khảo .list-paragraph

https://vnpro.vn/thu-vien/gioi-thieu-dynamic-multipoint-virtual-private-network-dmvpn-2420.html

https://www.ciscozine.com/dmvpn-phase-3-guide/

https://khanhvc.blogspot.com/2019/07/cisco-dynamic-multipoint-vpn-dmvpn.html

https://cuongquach.com/zabbix-la-gi-tim-hieu-he-thong-zabbix.html

https://viettelco.vn/huong-dan-cai-dat-zabbix-5-0-tren-centos-7/
