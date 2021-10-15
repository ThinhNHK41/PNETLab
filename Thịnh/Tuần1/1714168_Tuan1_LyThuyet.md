# 1. Cisco Discovery Protocol (Giao thức CDP)

**a. Tổng quát:**

\- Là giao thức ở Layer 2 cho phép thiết bị (Router, Switch,
Firewall,\...) thu thập thông tin về các thiết bị láng giềng kết nối
trực tiếp với mình để dễ quản lý cũng như là công cụ để vẽ nên sơ đồ
mạng. Trong đó, CDP là giao thức độc quyền của Cisco, những Switch khác
thì có chuẩn chung là LLDP.

\- CDP mặc định được bật trên tất cả các cổng, các cổng này sẽ gửi thông
điệp CDP đến các thiết bị Cisco láng giềng, qua việc trao đổi thông điệp
CDP thì các thiết bị sẽ nắm rõ được hết các thiết bị láng giềng của nó.
Các thông điệp này được gửi định kỳ 60s/lần chỉ trên link up/up.

\- Hold time: Là thời gian chờ phản hồi từ thiết bị láng giềng, nếu
trong thời gian 180s mà thiết bị Cisco không nhận được thông tin từ láng
giềng thì sẽ xóa thông tin láng giềng đó trong bảng CDP Neighbor.

![](.//media/image1.png)


\- Các thiết bị Cisco không truyền gói tin CDP mà chỉ hỗ trợ lưu trữ
thông tin nhận được vào bảng. Thông tin trong bảng được làm mới mỗi khi
một gói tin quảng bá được nhận, và thông tin về thiết bị sẽ bị bỏ sau
khi ba gói tin quảng bá từ thiết bị bị mất.

\- Các thông tin từ gói quản tin quảng bá CDP chứa dựa trên loại thiết
bị và phiên bản hệ điều hành được cài đặt. Một vài thông tin mà CDP có
thể học bao gồm: Phiên bản IOS Cisco đang chạy trên thiết bị Cisco, nền
tảng phần cứng của thiết bị, địa chỉ IP của các cổng trên thiết bị, Các
thiết bị láng giềng được kết nối quảng bá với thiết bị Cisco, các cổng
được kích hoạt trên thiết bị CIsco (bao gồm loại mã hóa), hostname,
thiết lập duplex, VLAN Trunking Protocol (VTP) Domain, Native VLAN.

\- CDP Version 2 cung cấp các đặc tính theo dõi thiết bị thông minh hơn
cái có sẵn ở Version 1. Một trong các đặc tính có sẵn là cơ chế báo cáo
nâng cao để theo dõi lỗi nhanh hơn, giúp giảm thời gian chết của mạng.
Các lỗi được báo cáo bao gồm Native VLAN IDs (IEEE 802.1Q) không khớp
trên các cổng kết nối và trạng thái port-duplex không khớp giữa các
thiết bị. Các thông báo về lỗi được báo cáo sẽ được gửi đến bảng điều
khiển hoặc máy chủ ghi log.

\- Sử dụng Cisco Discovery Protocol (CDP) với Simple Network Management
Protocol (SNMP) cho phép các ứng dụng quản lý mạng học các loại thiết bị
và địa chỉ đại diện SNMP của các thiết bị lân cận. Các ứng dụng có thể
cũng gửi các hàng chờ SNMP đến các thiết bị láng giềng. Nó cũng sẽ học
được địa chỉ cổng và loại thiết bị láng giềng bằng cách lấy lại các bảng
CDP từ các đại diện SNMP trên các thiết bị đó. Khi cho phép, Đại diện
SNMP module quản lý mạng sẽ khám phá các thiết bị láng giềng và xây dựng
nó dựa trên bộ nhớ đệm cục bộ với thông tin về các thiết bị này. Một máy
trạm quản lý các thể lấy lại bộ nhớ đệm này bằng cách gửi các yêu cầu
SNMP để có thể truy cập CISCO-CDP-MIB.

\- CDP và hỗ trợ định tuyến theo yêu cầu (On-Demand Routing = ODR) cho
ATM PVC (ATM point-to-point permanent virtual circuits). Hỗ trợ định
tuyến theo yêu cầu sử dụng CDP để tuyên truyền thông tin địa chỉ IP
trong cấu trúc liên kết hub-and-spoke. Khi hỗ trợ định tuyến được kích
hoạt, các bộ định tuyến sẽ tự động quảng cáo các mạng con của nó bằng
cách sử dụng CDP. Để kích hoạt CDP sử dụng lệnh **cdp enable** và để
kích hoạt ODR sử dụng lệnh **router odr** (đồng thời tắt tất cả
dynamic-routing protocols trên các spoken router.

\- CDP hỗ trợ cho IPv6 có chức năng giống như IPv4 và cho các lợi ích
tương tự. Cải tiến IPv6 cho phép CDP trao đổi IPv6 và thông tin địa chỉ
mạng láng giềng. Cải tiến này cũng cung cấp thông tin IPv6 cho các sản
phẩm quản lý mạng và các công cụ khắc phục sự cố.

\- Lợi ích của CDP:

-   Cho phép các hệ thống sử dụng các giao thức lớp mạng khác nhau để
    học về một hệ hệ thống khác.

-   Tạo điều kiện thuận lợi cho việc quản lý các thiết bị Cisco bằng
    cách khám phá chúng và khám phá cách chúng được cấu hình.

-   Hỗ trợ khắc phục sự cố các trường Type-Length-Value (TLV).

-   Hoạt động với SNMP bằng cách tìm hiểu địa chỉ đại diện SNMP và gửi
    các truy vấn SNMP.

**b. Các lệnh của CDP:**

**cdp run / no cdp run**

![](.//media/image2.png)
![](.//media/image3.png)


![](.//media/image4.png)
![](.//media/image5.png)


Cho phép hoặc không cho phép CDP trên thiết bị hoặc từng cổng riêng
biết.

**cdp timer** seconds **/ cdp holdtime** seconds

![](.//media/image6.png) 

Dùng để thiết lập thời gian gửi và chờ các gói tin CDP.

**cdp advertise-v2 / no cdp advertise-v2**

![](.//media/image7.png)
![](.//media/image8.png)


CDP Version 2 được kích hoạt mặc định trên các thiết bị Cisco. Có thể
dùng 1 trong 2 câu lệnh trên để kích hoạt hoặc vô hiệu nó.

**Một số lệnh theo dõi CDP**

![](.//media/image9.png) 

***show cdp neighbors***

![](.//media/image10.png)


Các thông tin nhận được:

\- Device ID: Tên của thiết bị láng giềng Switch01

\- Local Interface: Router01 sử dụng cổng F0/0 để nối đến Switch01

\- Holdtime: thời gian mà thiết bị chưa nhận được thông tin về láng
giềng là 151s

\- Capability: S -\> Láng giềng là thiết bị Switch

\- Platform: dòng sản phẩm của thiết bị láng giềng là 2960

\- Port ID: láng giềng sử dụng cổng F0/1 kết nối đến Router01

***show cdp neighbors detail***

![](.//media/image11.png)


Cho biết thêm một số thông tin khác của láng giềng như: địa chỉ IP, Hệ
điều hành đang sử dụng.

**c. Tấn công giao thức CDP:**

**Tấn công giao thức CDP:**

\- Những thông tin này mặc định được gửi ra trên các port và rất dễ bị
tấn công nhằm mục đích nghe lén để xác định xem là ip của Server,
Switch, Router là bao nhiêu, đang chạy trên hệ điều hành nào,\...

\- Do mỗi hệ điều hành, mỗi phiên bản đều có các lỗ hổng riêng, nếu
hacker biết được thông tin này thì sẽ tìm ra các lỗi và từ các lỗ hổng
này tấn công vào hệ thống.

**Ngăn chặn tấn công CDP:**

\- Do CDP mặc định được bật trên tất cả các cổng nên dễ bị rò rỉ thông
tin IP cũng như hệ điều hành mà thiết bị đang sử dụng. Ta chỉ cần bật
giao thức CDP trên các cổng kết nối giữa các thiết bị quan trọng để dễ
dàng quản lý và tắt trên các cổng kết nối với các thiết bị người dùng để
tránh khỏi sự can thiệp không cần thiết.

![](.//media/image12.png)


\- Muốn tắt CDP trên một Port cụ thể ta vào interface và gõ lệnh no cdp
enable

![](.//media/image13.png)


\- Nếu muốn CDP tắt trên tất cả các port thì gõ lệnh no cdp run trên
Global Config

![](.//media/image14.png)


# 2. Changing the Configuration Register on IOS devices

**a. Tổng quát về Đăng ký Cấu hình**

Router có một dải đăng ký cấu hình 16-bit trên NVRAM. Mỗi bit có giá trị
1 (được thiết lập) hoặc giá trị 0 (không được thiết lập), và cài đặt mỗi
bit sẽ tác động đến hiệu suất router trên lần khởi động lại kế tiếp.

Có thể sử dụng đăng ký cấu hình để

\- Buộc router khởi động vào màn hình ROM (chương trình bootstrap)

\- Chọn nguồn khởi động và tên tệp khởi động mặc định

\- Bật hoặc tắt chức năng Break

\- Kiểm soát địa chỉ phát sóng

\- Khôi phục mật khẩu bị mất

\- Thay đổi tốc độ dòng bảng điều khiển

***Bảng D-1***: Mô tả bit Đăng ký Cấu hình

![image](https://user-images.githubusercontent.com/92511177/137448454-d7fffed8-ebe7-400e-a35b-2a9933ce99db.png)

![image](https://user-images.githubusercontent.com/92511177/137448660-cad5e0d6-4609-4ff9-b155-e9fd2d16a1b0.png)

![image](https://user-images.githubusercontent.com/92511177/137448593-8ef7778e-4135-4a11-a861-82c069ab0b50.png)


**Bảng D-2: Mô tả Bit Đăng ký Cấu hình trường khởi động**

![image](https://user-images.githubusercontent.com/92511177/137448801-ca253596-66b1-4e0c-ab4f-8746718e7952.png)


Bảng D-3: Sự kết hợp Bit Đăng ký cấu hình Địa chỉ Broadcast

  ---------- ---------- -------------------------------------------------
  **Bit 10** **Bit 14** **Địa chỉ Broadcast (\<net> \<host>)**

  0          0          \<ones> \<ones>

  1          0          \<ones> \<zeros>

  1          1          \<zeros> \<zeros>

  0          1          \<zeros> \<ones>
  ---------- ---------- -------------------------------------------------

**Bảng D-4: Sự kết hợp Bit Đăng ký cấu hình tốc độ dòng bảng điều
khiển**

  ---------- ----------- ---------- --------------------------------------
  **Bit 5**  **Bit 11**  **Bit 12** **Tốc độ dòng bảng điều khiển (baud)**

  1          1           1          115200

  1          0           1          57600

  1          1           0          38400

  1          0           0          19200

  0          0           0          9600

  0          1           0          4800

  0          1           1          2400

  0          0           1          1200
  ---------- ----------- ---------- --------------------------------------

**b. Thay đổi Cài đặt Đăng ký Cấu hình**

\- Có thể thay đổi cài đặt đăng ký cấu hình từ màn hình ROM hoặc Cisco
IOS CLI. Để thay đổi đăng ký cấu hình sử dụng màn hình ROM, tìm Appendix
C, \"Using ROM Monitor\".

\- Để thay đổi cài đặt đăng ký cấu hình từ Cisco IOS CLI, ta thực hiện
theo các bước sau:

**Bước 1:** Kết nối một thiết bị đầu cuối hoặc máy tính cá nhân đến cổng
điều khiển router.

**Bước 2:** Cấu hình thiết bị đầu cuối hoặc phần mềm mô phỏng thiết bị
đầu cuối cho 9600 baud (mặc định), 8 bi dữ liệu, không có chẵn lẻ, và 2
bit dừng.

**Bước 3:** Bật router lên

**Bước 4:** Nếu bạn được hỏi có muốn vào initial dialog hãy trả lời No

![](.//media/image15.png)


Sau vài giây, chế độ user EXEC (Router>) sẽ xuất hiện

**Bước 5:** Truy cập vào chế độ privileged EXEC bằng cách gõ lệnh
**enable** và nhập mật khẩu

![](.//media/image16.png)


**Bước 6:** Truy cập vào chế độ Global Configuration

![](.//media/image17.png)


**Bước 7:** Để thay đổi cài đặt cấu đăng ký cấu hình, gõ lệnh
**config-register** value , trong đó value là giá trị hệ thập lục phân
bắt đầu với 0x:

![](.//media/image18.png)


**Bước 8:** Thoát chế độ Global Configuration

![](.//media/image19.png)


**Bước 9:** Lưu các thay đổi cấu hình vào NVRAM

![](.//media/image20.png) 

Các cài đặt đăng ký cấu hình mới sẽ được lưu vào NVRAM, nhưng chúng sẽ
không có tác dụng đến khi router được khởi động lại.

**c. Hiển thị Cài đặt Đăng ký Cấu hình**

\- Để hiển thị cài đặt đăng ký cấu hình hiện đang có hiệu lực và các cài
đặt sẽ được sử dụng ở lần tải lại router tiếp theo, hãy nhập lệnh hiển
thị phiên bản ở chế độ privileged EXEC.

\- Cài đặt Đăng ký cấu hình được hiển thị ở dòng cuối cùng của lệnh
**show version**

![](.//media/image21.png)


**d. Cấu hình Tốc độ dòng bảng điều khiển (CIsco IOS CLI)**

\- Cài đặt kết hợp của bit 5, 11, và 12 xác định tốc độ dòng bảng điều
khiển. Có thể sửa đổi các bit thanh ghi cấu hình cụ thể chỉ từ màn hình
ROM.

\- Để thay đổi đăng ký cấu hình sử dụng màn hình ROM, tìm Appendix C, \"
Using ROM Monitor\"

\- Để cấu hình tốc độ dòng bảng điều khiển từ giao diện dòng lệnh Cisco
IOS, thực hiện các bước sau:

![](.//media/image22.png)


# 3. Troubleshooting OSPFv2 Neighbor Adjacencies

OSPF thì không giống như EIGRP là một giao thức link-state tuy nhiên
điểm chung của chúng là 2 giao thức định tuyến đều thiết lập một vùng
lân cận trước khi trao đổi thông tin định tuyến. Trong trường hợp OSPF,
chúng ta trao đổi LSAs (Quảng cáo trạng thái liên kết) để xây dựng LSDB
(Cơ sở dữ liệu trạng thái liên kết). Thông tin tốt nhất từ LSDB sẽ được
sao chép vào bảng định tuyến.

Mỗi khi nhìn vào OSPF hàng xóm gần kề, chúng ta sẽ thấy:

![](.//media/image23.png)


Thông thường để xem đầy đủ thông tin ở đây ta cần xem trên các thiết bị
liền kề.

\* Có một ngoại lệ đối với quy tắc này: Khi chúng ta sử dụng DR/BDR thì
hai bộ định tuyến OSPF \"bình thường\" (không DR hoặc không BDR) sẽ
không tạo thành một sự liền kề đầy đủ với nhau. Chúng sẽ vẫn ở trạng
thái 2 chiều.

Khi OSPF hàng xóm gần kề không ở trạng thái full state thì nó bị một
trong các nguyên nhân sau:

\- Không có người hàng xóm OSPF nào cả

\- Nó bị mắc kẹt trong ATTEMPT

\- Nó bị kẹt ở INIT

\- Nó bị mắc kẹt trong 2 chiều

\- Nó bị mắc kẹt trong EXSTART / EXCHANGE

\- Nó bị kẹt trong LOADING

Sau đây là một vài lỗi khác nhau dẫn đến việc không thể hình thành mối
quan hệ láng giềng OSPF:

**a. OSPF Network Command**

Trường hợp đầu tiên. Ta có 2 router OSPF:

![](.//media/image24.png)


Tuy nhiên chúng lại không là hàng xóm của nhau:

![](.//media/image25.png)


![](.//media/image26.png)


![](.//media/image27.png)


Ta sẽ sử dụng lệnh **show ip ospf interface**. Ta thấy rằng OSPF không
được kích hoạt trên cổng Fa0/0 của R1 nhưng trên R2 thì lại chạy. Bây
giờ ta hãy xem cấu hình của R1:

![](.//media/image28.png)


Ta có thể thấy rằng địa chỉ mạng của R1 bị sai và ta sửa lại như sau:

![](.//media/image29.png)


![](.//media/image30.png) 

Như vậy lỗi đã được sửa, OSPF hàng xóm gần kề đã hoạt động.

-\> Đảm bảo rằng cấu hình chính xác địa chỉ mạng, lớp mạng và khu vực.

**b. OSPF Passive Interface**

![](.//media/image31.png)


Cấu hình R1, R2 như sau:

![](.//media/image32.png)


![](.//media/image33.png)


OSPF đã được kích hoạt trên cổng của các router nghĩa mạng đã được cấu
hình đúng. Tuy nhiên trên R1 bị lỗi \"No Hellos (Passive interface)\".
Nếu bạn cấu hình passive interface sau đó mạng trên cổng đó vẫn sẽ được
quảng bá nhưng nó không gửi bất kỳ gói tin OSPF hello nào. Vì vậy không
thể hình thành hàng xóm liền kề. Hãy xem qua cấu hình của R1:

![](.//media/image34.png)


Ta có thể fix như sau:

![](.//media/image35.png) 

Hãy loại bỏ passive interface. Và ta có được hàng xóm liền kề:

![](.//media/image36.png)


-\> Đảm bảo OSPF đang gửi các gói tin hello trên cổng nếu không thì sẽ
không thể trở thành hàng xóm được.

**c. OSPF Multicast Filtering**

![](.//media/image31.png)


Kiểm tra hàng xóm liền kề:

![](.//media/image37.png)


Ta thấy rằng R1 hiển thị OSPF hàng xóm ở trạng thái INIT trong khi R2
thì không hiển thị gì. Đối với các cổng như sau:

![](.//media/image38.png)


OSPF đã được cấu hình đúng trên cả 2 giao diện như trên.

Từ khi R1 hiển thị INIT state có nghĩa là nó nhận thứ gì đó từ R2. R2
thì không hiển thị gì cả vì vậy nó có lẽ không nhận được gì từ R1. OSPF
sử dụng các gói tin hello để thiết lập OSPF hàng xóm gần kề và gửi địa
chỉ multicast 224.0.0.5. Hãy ping thử:

![](.//media/image39.png)


R1 và R2 không nhận được phản hồi

![](.//media/image40.png) 

![](.//media/image41.png)


Sau khi ping access-list ta thấy rằng R2 có một access-list được gọi là
BLOCKSTUFF. Hãy xem thử show access-list:

![](.//media/image42.png)


Access-list hiện tại chỉ cho phép TCP, UDP và ICMP traffic. OSPF không
sử dụng TCP hoặc UDP và nó bị bỏ bởi access-list bởi vì ngầm phủ nhận
bất kỳ. Hãy thêm vào access-list để cho phép OSPF traffic:

![](.//media/image43.png) 

![](.//media/image44.png)


![](.//media/image45.png)


Như vậy đã R1 và R2 đã là hàng xóm của nhau và ping được.

-\> Đừng cấm địa chỉ multicast OSPF 224.0.0.5 và 224.0.0.6.

**d. OSPF Subnet Mask**

![](.//media/image31.png)


![](.//media/image46.png) 

Không có OSPF hàng xóm nhưng OSPF đã được kích hoạt trên các cổng.

![](.//media/image47.png)


![](.//media/image48.png)


Ta có thể thấy rằng R2 đã cấu hình lớp mạng trên cổng sai. Hãy cấu hình
lại lớp mạng trên R2:

![](.//media/image49.png)


![](.//media/image50.png)


Như vậy OSPF hàng xóm gần kề đã hoạt động.

-\> Đảm bảo rằng cùng lớp mạng trên các router được kết nối trực tiếp
với nhau.

**e. OSPF Hello & Dead Interval**

![](.//media/image31.png)


Ta thử kiểm tra ospf:

![](.//media/image51.png)


Ta thấy rằng cấu hình R1 dead-interval 24s và R2 là 11s. R1
hello-interval 6s và R2 là 10s. Hãy thiết lập lại cùng thời gian:

![](.//media/image52.png)


![](.//media/image53.png) 

-\> Đảm bảo tất cả các tham số bắt buộc trong gói hello đều khớp.

# 4. OSPF LSA types and functions

\- OSPF sử dụng các LSA hay Quảng cáo trạng thái liên kết (Link state
Advertisements) để chia sẻ thông tin của từng mạng và điền LSDB (Cơ sở
dữ liệu trạng thái liên kết). Các LSA được sử dụng bởi router để thay
đổi thông tin cấu trúc liên kết. Một LSA chứa thông tin định tuyến và
cấu trúc liên kết mô tả một phần của mạng OSPF. Router thay đổi các LSA
và học hoàn toàn cấu trúc của mạng đến khi tất cả router có chính xác cơ
sở dữ liệu cấu trúc giống nhau. Trên thực tế, OSPF gửi các cập nhật
(LSA) khi có một sự thay đổi đến một trong các liên kết. Các LSA được
làm mới thêm sau mỗi 30 phút.

\- Bảng tổng quát tất cả các loại OSPF LSA

  ----------------------- -----------------------------------------------
  **Loại**                **Mô tả**

  LSA Type 1              Router LSA

  LSA Type 2              Network LSA

  LSA Type 3 or 4         Summary LSA & ASBR LSA

  LSA Type 5              Autonomous System External LSA

  LSA Type 6              Multicast OSPF LSA Type

  LSA Type 7              Defined for Not-So-Stubby-Areas

  LSA Type 8              External Attribute LSA for BGP

  LSA Type 9, 10, 11      Opaque LSA
  ----------------------- -----------------------------------------------

![](.//media/image54.png)


Hình 1. Các loại LSA có trong gói OSPF LSU

**a. LSA Type 1: Router LSA**

![](.//media/image55.png)


Hình 2. Các gói LSA loại 1 trao đổi giữa các router OSPF trong cùng 1
khu vực

\- Loại LSA này bị tràn (flood) bởi mọi bộ định tuyến trong một khu vực

\- LSA bao gồm thông tin về các liên kết được kết nối trực tiếp

\- Nó được xác định bằng ID bộ định tuyến hoặc bộ định tuyến gốc

\- Nó bị từ tràn (flood) trong một khu vực

\- LSA loại 1 không vượt qua ABR

\- Chúng ta xem đây là các tuyến \"O\" trong bảng định tuyến

\- LSA 1 - O, Bộ định tuyến LSA chứa tất cả các ID liên kết - mạng, được
tạo bởi mọi bộ định tuyến và là cục bộ cho khu vực.

**b. LSA Type 2: Network LSA**

![](.//media/image56.png)


Hình 3. Các gói LSA loại 2 trao đổi giữa OSPF DR và các router hàng xóm

\- Được tạo bởi bộ định tuyến DR trên mạng quảng bá. Nó bao gồm ID mạng,
mặt nạ mạng con và cả danh sách các bộ định tuyến được đính kèm trong
quá trình truyền

\- Trong OSPF, chúng ta có thể có một LSA Network hoặc LSA Loại 2 cho
mỗi chương trình phát sóng chuyển tiếp trong Mạng NBMA

\- LSA này cũng chỉ có thể bị từ tràn (flood) trong khu vực và không thể
vượt qua ABR

\- Chúng ta xem đây là các tuyến \"O\" trong bảng định tuyến

\- LSA 2 - O, Mạng LSA chứa tất cả các bộ định tuyến được gắn vào phân
đoạn, được tạo bởi DR và là cục bộ cho khu vực.

**c. LSA Type 3: Summary LSA**

![](.//media/image57.png)


Hình 4. LSA loại 3 - Router OSPF ABR quảng bá tuyến đường tóm tắt
192.168.2.0/24 đến khu vực 0

Nhìn vào hình trên, Router ABR R2 tạo LSA Tóm tắt loại 3 và đưa nó vào
khu vực 0. Theo cách tương tự, Router ABR R3 tạo LSA Tóm tắt loại 3 và
đưa nó vào khu vực 2. Các LSA Tóm tắt loại 3 xuất hiện dưới dạng các mục
O IA trong bảng định tuyến bộ định tuyến.

\- LSA Loại 3 được sử dụng để chia sẻ thông tin mạng với các khu vực
khác. Liên khu vực (IA)

\- Các LSA này được quảng bá bởi Router ABR

\- Các LSA này được biểu diễn trong bảng định tuyến dưới dạng các tuyến
\"OIA\"

\- Để tràn (flood) thông tin thông qua Hệ thống tự trị, chúng được tạo
lại bởi các ABR sau đó

\- LSA 3 - O IA, Tóm tắt mạng LSA mô tả mạng từ một khu vực khác, được
tạo bởi ABR và được truyền giữa các khu vực

\- Nó chứa ID mạng và mặt nạ mạng con.

**d. LSA Type 4: ASBR Summary LSA**

![](.//media/image58.png)


Hình 5. Gói LSA Loại 4 được đưa vào Vùng 0 & 2 bởi ABR R2 và ABR R3

Trong khi cá gói LSA loại 4 được ABR sử dụng để quảng bá tuyến ASBR qua
các khu vực của chúng, nó sẽ không được sử dụng bởi chính ASBR trong khu
vực cục bộ của nó (Area 1); ASBR sử dụng LSA Loại 1 để thông báo cho các
láng giềng của nó (trong trường hợp này là R2) trong mạng của nó.

\- Loại LSA này còn được gọi là LSA tóm tắt được sử dụng để quảng bá về
ASBR tới các khu vực khác trong cùng một hệ tự trị

\- Nó được tạo ra bởi ABR của khu vực ban đầu

\- Các loại LSA này tràn (flood) khắp Hệ thống tự trị

\- Các loại LSA này chỉ chứa Router ID của ASBR

\- LSA 4 - O IA, Tóm tắt các trạng thái liên kết ASB, được tạo bởi ABR
và được truyền giữa các khu vực.

**e. LSA Type 5: ASBR External LSA**

![](.//media/image59.png)


Hình 6. Gói LSA loại 5 quảng bá định tuyến mặc định đến tất cả router
OSPF

Tiền tố/ Tuyến đường bên ngoài này được phân phối lại vào mạng OSPF bởi
ASBR(R1) và được xem như các mục nhập O E1 hoặc E2 trong các bảng định
tuyến bộ tuyến OSPF khác.

\- Chỉ được quảng bá bởi ASBR và cũng thuộc sở hữu của ASBR

\- Các LSA này được sử dụng để quảng bá mạng từ các hệ thống tự trị khác

\- Các LSA này tràn (flood) trong toàn bộ Hệ thống tự trị

\- ID bộ định tuyến quảng bá không bị thay đổi trong toàn bộ Á khi nó
đang lan truyền

\- LSA Loại 4 được sử dụng để tìm ASBR

\- Các tuyến đường không được tóm tắt theo mặc định

\- LSA 5 - O E1, O E2, Các trạng thái liên kết bên ngoài, được tạo bởi
ASBR và được truyền.

**f. LSA Type 6: Multicast OSPF LSA**

\- Được sử dụng khi định tuyến sử dụng multicast (Giao thức định tuyến
MODPF)

\- Các LSA này không được hỗ trợ bởi Router Cisco.

**g. LSA Type 7: Not-So-Stubby-Are (NSSA) External LSA**

![](.//media/image60.png)


Hình 7. Gói LSA loại 7 truyền qua NSSA và được chuyển đổi thành LSA loại
5 bởi ABR

Trong ví dụ ở trên, ABR R2 chuyển đổi LSA loại 7 thành LSA loại 5 và làm
tràn (flood) nó vào mạng OSPF.

\- Vì LSA loại 5 không được phép vào các khu vực NSSA, một giải pháp cho
điều đó được cho là LSA loại 7

\- Nó mang thông tin tương tự như LSA loại 5 nhưng điều này không bị
chặn trong khu vực NSSA

\- Khi đạt đến ABR, nó được dịch ngược trở lại LSA loại 5 và bị tràn
(flood) sang các khu vực khác

\- LSA 7 - O N1, O N2, Các trạng thái liên kết bên ngoài NSSA, được tạo
bởi ASBR vào vùng NSSA và được truyền vào vùng 0 dưới dạng E1 hoặc E2.

**h. LSA Type 8: External Attributes LSA (OSPFv2) / Link Local LSA
(OSPFv3)**

\- Các gói LSA loại 8 (Thuộc tính bên ngoài LSA - OSPFv2 / Liên kết cục
bộ LSA - OSPFv3) trong OSPFv2 (IPv4) được gọi là LSA Thuộc tính bên
ngoài và được sử dụng để chuyển các thuộc tính BGP qua mạng OSPF trong
khi các đích BGP được truyền tải qua LSA loại 5. Tuy nhiên, tính năng
này không được hầu hết các bộ định tuyến hỗ trợ. Với OSPFv3 (IPv6), LSA
loại 8 được định nghĩa lại để mang thông tin IPv6 qua mạng OSPF.

**j. LSA Type 9: Link Scope Opaque (OSPFv2) / Intra Area Prefix LSA
(OSPF v3)**

\- Loại LSA này nằm trong phạm vi Trạng thái liên kết và không bị tràn
(flood) ngoài mạng cục bộ.

**k. LSA Type 10: Area Scope Opaque LSA**

\- Phạm vi của loại LSA này là khu vực cục bộ. Loại LSA này không bị
tràn (flood) vượt ra ngoài biên giới của khu vực liên quan của chúng.

**l. LSA Type 11: OSPF As Scope Opaque LSA**

\- Loại LSA này bị tràn (flood) khắp các Hệ thống tự trị (AS). Một phần
nào đó có thể liên quan đến LSA loại 5 là các điều khoản về phạm vi
tràn. Có 3 tính năng chính của LSA loại 11:

-   Chúng bị tràn (flood) khắp các khu vực vận chuyển

-   Không bị tràn (flood) vào các khu vực sơ khai từ xương sống

-   Không bắt nguồn bởi các bộ định tuyến có các khu vực sơ khai được
    kết nối.

# 5. Segment Routing OSPF Basic

\- Giao thức định tuyến OSPF (Open Shortest Path First) là một giao thức
cổng nội bộ (Interior Gateway Protocol - IGP) được phát triển bởi nhóm
công tác OSPF của Lực lượng Đặc nhiệm Kỹ thuật Internet (the Internet
Engineering Task Force - IETF). Được thiết kế rõ ràng cho mạng IP, OSPF
hỗ trợ mạng con IP và gắn thẻ thông tin định tuyến có nguồn gốc bên
ngoài. OSPF cũng cho phép xác thực gói tin và sử dụng IP Multicast khi
gửi và nhận gói tin.

a\. Kích hoạt Định tuyến phân đoạn cho Giao thức OSPF

\- Định tuyến phân đoạn trên nền tảng kiểm soát OSPF hỗ trợ những thứ
sau:

-   Nền tảng điều khiển OSPFv2

-   Đa khu vực

-   SID tiền tố IPv4 cho tiền tố máy chủ lưu trữ trên giao diện lặp lại

-   SID gần kề cho các vị trí liền kề

-   MPLS nhảy hop áp chót (PHP) và báo hiệu rõ ràng null

\- Trước khi bắt đầu, mạng của bạn cần hỗ trợ thuộc tính phần mềm MPLS
Cisco IOS XR trước khi kích hoạt định tuyến phân đoạn cho OSPF trên
router.

![](.//media/image61.png)


![](.//media/image62.png)


![](.//media/image63.png)


![](.//media/image64.png)


![](.//media/image65.png)


b\. Định cấu hình tiền tố - SID trên giao diện vòng lặp được kích hoạt
OSPF

\- Mã định danh phân đoạn tiền tố (SID) được liên kết với tiền tố IP.
Tiền tố SID được định cấu hình theo cách thủ công từ phạm vi nhãn khối
toàn cầu định tuyến phân đoạn (SRGB). Một SID tiền tố được cấu hình
trong giao diện lặp lại với địa chỉ lặp lại của nút làm tiền tố. Đoạn
tiền tố hướng lưu lượng truy cập dọc theo con đường ngắn nhất đến đích
của nó.

\- SID tiền tố có thể là SID nút hoắc SID Anycast. SID nút là một loại
SID tiền tố xác định một tập hợp các nút và được định cấu hình với xóa
cờ n. Tập hợp các nút (nhóm Anycast) được định cấu hình để quảng cáo một
địa chỉ tiền tố được chia sẻ và SID tiền tố. ĐỊnh tuyến Anycast cho phép
điều hướng lưu lượng truy cập đến nhiều nút quảng cáo. Các gói được gửi
đến một địa chỉ Anycast được chuyển tiếp đến các nút gần nhất về mặt cấu
trúc liên kết.

\- Tiền tố SID là duy nhất trên toàn cầu trong vùng định tuyến phân
đoạn.

> \- Tác vụ này mô tả cách định cấu hình chỉ số định danh phân đoạn tiền
> tố (SID) hoặc giá trị tuyệt đối trên giao diện Loopback hỗ trợ OSPF.
>
> \- Trước khi bắt đầu, đảm bảo định tuyến phân đoạn được kích hoạt trên
> mọi phiên bản, khu vực hoặc giao diện.
>
> ![](.//media/image66.png) 
>
> ![](.//media/image67.png)
> 
>
> ![](.//media/image68.png)
> 
>
> \- Kiểm tra lại Cấu hình Prefix-SID:
>
> ![](.//media/image69.png)
> 

c\. Định tuyến phân đoạn tối ưu hóa ECMP-FEC

\- ECMP-FECs được sử dụng cho bất kỳ chương trình ECMP nào trên hệ
thống, ví dụ như MPLS LSP ECMP, VPN multipath, và EPVN multi-homing.

\- Giải pháp tối ưu hóa SR ECMP-FEC giảm thiểu tiêu thụ tài nguyên
ECMP-FEC trong quá trình lập trình lớp dưới cho mạng SR-MPLS. Tính năng
này hỗ trợ chia sẻ cùng một mục nhập ECMP-FEC, FEC thông thường và đầu
vào DB đóng gói (EEBD) cho tất cả / 32 tiền tố định tuyến phân đoạn IPv4
với cùng một tập hợp các bước nhảy tiếp theo. Tối ưu hóa ECMP-FEC được
kích hoạt khi tất cả các out_labels được liên kết với các đường dẫn ECMP
cho một tiền tố nhất định có cùng giá trị. Nếu quy tắc này không được
đáp ứng, thì tiền tố được lập trình với ECMP-FEC chuyên dùng. Các tiền
tố khác đáp ứng quy tắc là các ứng cử viên để tối ưu hóa.

\- Định tuyến nhãn phân đoạn Bộ định tuyến cạnh nhãn (LER). Tối ưu hóa
ECMP-FEC cho phép tối ưu hóa ECMP-FEC ban đầu được phát triển cho các
nút Bộ định tuyến chuyển mạch nhãn (LSR) (MPLS P) được bật trên bộ định
tuyến LER (Lớp 3 MPLS PE).

\- Để kích hoạt tối ưu hóa SR ECMP-FEC, sử dụng lệnh **hw-module fib
mpls label lsr-optimized** ở chế độ cấu hình Global. Sau khi kích hoạt
thuộc tính này thì cần xác nhận.

![](.//media/image70.png)


\- Kiểm tra lại (ví dụ xem mức độ sử dụng NPU trước và sau khi tối ưu
hóa SR ECMP-FEC)

![](.//media/image71.png)


![](.//media/image72.png)


# 6. OSPF Route LSA Filtering STUB NSSA

**OSPF Stubby Areas Concept**

\- Stubby Areas cung cấp một phương pháp để lọc các external routes và
các lựa chọn để cấm các interarea routes

\- Có 4 loại OSPF Stubby Areas:

-   Stub Area

-   Totally Stubby Area

-   Not-So-Stubby-Area (NSSA)

-   Totally NSSA

![](.//media/image73.png)


Hình 1. Các kiểu vùng biến thể của stub trong OSPF

  ----------------------------------- -----------------------------------
  **Kiểu stub**                       **Lệnh trong chế độ router ospf**

  Stub                                Area area-id stub

  Totally stubby                      Area area-id stub no-summary

  Not-so-stubby-area                  Area area-id nssa

  Totally NSSA                        Area area-id nssa no-summary
  ----------------------------------- -----------------------------------

Hình 2. Các câu lệnh cấu hình kiểu mạng Stub

**a. Stub Area**

\- OSPF stub area cấm các LSA loại 5 (external routes) và các LSA loại 4
(ASBR summary LSA) đi vào stub area tại ABR

\- RFC 2328 bắt đầu khi LSA loại 5 đến ABR tại stub area, ABR tạo
Default Route cho stub area dưới dạng LSA loại 3

\- ABR tạo ra default route khi area được cấu hình stub và interface
OSPF được bật trong area 0

\- Cấu hình Stub Area:

**(config-router)# area** [area-id].ul **stub**

\- Kiểm tra stub area: **show ip route ospf** hoặc **show ip ospf
database** sau khi cấu hình Stub.

**b. Totally Stubby Area (cực kỳ bế tắc)**

\- Totally Stubby Area cấm LSA loại 3 (interarea), loại 4 (ASBR Summary)
và loại 5 (External routes) đi vào area totally stubby tại con ABR

\- khi con ABR của Totally Stubby Area nhận LSA loại 3 hoặc loại 5, ABR
này tạo ra default route cho area này.

\- Chỉ có intra-area và default route mới tồn tại trong totally stubby
area

\- Cấu hình Totally Stubby Area

> (config-router)# **area** [area-id].ul **stub no-summary**

\- Kiểm tra stub area: **show ip route ospf** hoặc **show ip ospf
database** sau khi cấu hình Totally Stubby.

c\. Not-So-Stubby Area (NSSA)

\- NSSA cấm LSA loại 5 đi vào ABR nhưng cho phép Redistribution (chuyển
hướng) của External route đi vào NSSA

\- ASBR Redistribution mạng vào NSSA OSPF, ASBR quảng bá LSA loại 7 thay
vì loại 5

\- Khi LSA loại 7 đến ABR, thì ABR chuyển LSA loại 7 thành loại 5. ABR
không tự động quảng bá default route khi LSA loại 5 và loại 7 bị cấm.

\- Cấu hình NSSA:

-   Trên con ABR ta cấu hình: **area** [area-id].ul **nssa
    \[default-information-originate\]**

-   Trên tất cả router trong NSSA phải cấu hình: **area** [area-id].ul
    **nssa**

\- Kiểm tra stub area: **show ip route ospf** hoặc **show ip ospf
database** sau khi cấu hình NSSA.

**d. Totally NSSA**

\- Totally Stubby Area cấm lSA loại 3 (Interarea), loại 4 (ASBR Summary)
và loại 5 (External routes) đi area khác đi vào Totally Stubby Area tại
ABR. Nhưng vẫn cho phép redistributions external networks nên ta sử dụng
Totally NSSA.

\- Cấu hình Totally NSSA:

-   Trên ABR cấu hình: **area** [area-id].ul **nssa no-summary**

-   Trên tất cả ASBR trong Totally NSSA: **area** [area-id].ul
    **nssa**

\- Kiểm tra stub area: **show ip route ospf** hoặc **show ip ospf
database** sau khi cấu hình Totally NSSA.

**Tóm tắt:**

\- Tất cả các loại Stubby Area: ABR đề filter LSA loại 5

\- Totally Stubby và Totally NSSA: ABR cũng filter cả LSA loại 3

\- Vùng Stub và NSSA: ABR không filter LSA loại (nhưng vẫn filter loại 5
theo ý đầu)

\- NSSA và Totally NSSA thì cho phép Redistribute (chuyển hướng)

**Kiểm tra:**

\# show ip ospf

\# show ip ospf database

\# show ip ospf database database-summary

# 7. OSPF Summarization and Path Control

**a. OSPF Route Summarization**

\- Là quá trình tóm tắt lộ trình OSPF. Các router biên giới khu vực (ABR
- Area Border Router) gửi quảng cáo liên kết tóm tắt để mô tả các tuyến
đường đến các khu vực khác. Tùy thuộc vào số lượng điểm đến, một khu vực
có thể bị tràn (flood) với một lượng lớn các bản ghi trạng thái liên
kết, có thể sử dụng tài nguyên thiết bị định tuyến. Để giảm thiểu số
lượng quảng cáo tràn (flood) trong một khu vực, bạn có thể định cấu hình
ABR để kết hợp hoặc tóm tắt, một loạt các địa chỉ IP và gửi thông tin có
thể truy cập về các địa chỉ này trong một quảng cáo trạng thái liên kết
(LSA). Bạn có thể tóm tắt một hoặc nhiều dải địa chỉ IP, trong đó tất cả
các tuyến đường phù hợp với phạm vi khu vực được chỉ định đều được lọc ở
ranh giới khu vực và bản tóm tắt được quảng cáo ở vị trí của chúng.

\- Đối với một khu vực OSPF, bạn có thể tóm tắt và lọc các tiền tố trong
khu vực. Tất cả các tuyến đường phù hợp với phạm vi khu vực được chỉ
định đều được lọc ở ranh giới khu vực và bản tóm tắt được quảng cáo ở vị
trí của chúng. Đối với khu vực không quá sơ khai của OSPF (NSSA), bạn
chỉ có thể kết hợp hoặc lọc các LSA bên ngoài của NSSA (Loại 7) trước
khi chúng được dịch sang các LSA bên ngoài AS (Loại 5) và đi vào khu vực
xương sống. Tất cả các tuyến đường bên ngoài đã học trong khu vực không
thuộc phạm vi của một trong các tiền tố sẽ được quảng cáo riêng lẻ đến
các khu vực khác.

\- Ngoài ra, bạn cũng có thể giới hạn số lượng tiền tố (tuyến đường)
được xuất vào OSPF. Bằng cách đặt số tiền tố tối đa do người dùng xác
định, bạn ngăn thiết bị định tuyến tràn ngập quá nhiều tuyến đường vào
một khu vực.

![](.//media/image74.png)


\- Như ta đã biết OSPF sử dụng LSA loại 3 cho các router inter-area và
LSA loại 5 cho các tiền tố bên ngoài được phân phối lại thành OSPF.

\- OSPF có thể tóm tắt nhưng nó thì bất khả thi để tóm tắt trong cùng
một khu vực. ĐIều này nó nghĩa là ta phải cấu hình tóm tắt trên ABR hoặc
ASBR. OSPF chỉ có thể tóm tắt LSA loại 3 và 5.

\- Tóm tắt định tuyến giúp giảm lưu lượng truyền và xung đột định tuyến
OSPF. OSPF không giống như EIGRP, nó không tự động tóm tắt. Cũng không
giống như EIGRP có thể định tuyến trên mọi router trong một mô hình mạng
EIGRP, OSPF chỉ có thể tóm tắt trên ABR và ASBR.

\- Câu lệnh sau được sử dụng để tóm tắt OSPF:

![](.//media/image75.png)


\- Để hiểu rõ hơn về quá trình tóm tắt OSPF, ta sẽ xem ví dụ sau:

![](.//media/image76.png) 

Cả 3 router đều đang chạy OSPF và trao đổi định tuyến với nhau. Trước
khi cấu hình tóm tắt OSPF, R1 bên trong khu vực backbone có 2 mục nhập
cho mạng 11.0.0.0/24 và 11.0.1.0/24 trong bảng định tuyến của nó.

![](.//media/image77.png)


Ta có thể tóm tắt 2 mạng con này trên R2, cho nên R1 chỉ cần nhận một
cập nhật định tuyến cho cả 2 mạng con. Ta có thể dùng lệnh sau trên R2:

![](.//media/image78.png)


Bây giờ, R1 chỉ có một nhập trong bảng định tuyến của nó cho các mạng
con được kết nối trực tiếp của R3:

![](.//media/image79.png)


**b. OSPF Path Control**

\- Khi một cấu trúc liên kết được chia sẻ trên mạng, OSPF sử dụng cấu
trúc liên kết để định tuyến các gói tin giữa các nút mạng. Mỗi đường đi
giữa các hàng xóm với nhau được chỉ định một chi phí dựa trên thông
lượng, thời gian phản hồi và độ tin cậy của liên kết. Tổng chi phí trên
một đường cụ thể giữa các máy chủ xác định chi phí tổng thể của đường
dẫn. Các gói sau đó được định tuyến dọc theo đường ngắn nhất bằng cách
sử dụng thuật toán đường đi ngắn nhất (SPF). Nếu tồn tại nhiều đường có
chi phí bằng nhau giữa địa chỉ nguồn và đích, OSPF định tuyến các gói
tin đi qua một đường luân phiên, theo kiểu vòng tròn. Các tuyến đường có
tổng số đường dẫn thấp hơn được ưa thích hơn các tuyến có số đường dẫn
cao hơn.

\- Bạn có thể sử dụng các phương pháp sau để kiểm soát lưu lượng OSPF:

-   Kiểm soát chi phí của các phân đoạn mạng OSPF riêng lẻ

-   Tự động điều chỉnh các chỉ số giao diện OSPF dựa trên băng thông

-   Kiểm soát lựa chọn tuyến đường OSPF

```=html
<!-- -->
```
-   **Kiểm soát chi phí của các phân đoạn mạng OSPF riêng l**ẻ

> \- OSPF sử dụng công thức sau đây để xác định chi phí của một tuyến
> đường:
>
> **chi phí = băng thông tham chiếu / băng thông giao diện**
>
> \- Có thể sửa đổi giá trị băng thông tham chiếu, được sử dụng để tính
> chi phí giao diện mặc định. Giá trị băng thông giao diện không thể cấu
> hình được người dùng và đề cập đến băng thông thực tế của giao diện
> vật lý.
>
> \- Theo mặc định, OSPF gán chỉ số chi phí mặc định là 1 cho bất kỳ
> liên kết nào nhanh hơn 100 Mbps và số liệu chi phí mặc định là 0 cho
> giao diện loopback (1o0). Không có băng thông nào được liên kết với
> giao diện loopback.
>
> \- Để kiểm soát luồng các gói trên mạng, OSPF cho phép gán thủ công
> chi phí (hoặc số liệu) cho một phân đoạn đường dẫn cụ thể. Khi bạn chỉ
> định một số liệu cho một giao diện OSPF cụ thể, giá trị đó được sử
> dụng để xác định chi phí của các tuyến đường được quảng cáo từ giao
> diện đó. Ví dụ: nếu tất cả các bộ định tuyến trong mạng OSPF sử dụng
> giá trị số liệu mặc định và bạn tăng số liệu trên một giao diện lên 5,
> tất cả các đường dẫn thông qua giao diện đó đều có số liệu được tính
> toán cao hơn mặc định và không được duyệt.
>
> \- Khi nhiều tuyến đường có chi phí bằng nhau đến cùng một điểm đến
> trong bảng định tuyến, một bộ multipath chi phí bằng nhau (ECMP) được
> hình thành. Nếu có một bộ ECMP cho tuyến đường đang hoạt động, phần
> mềm Junos OS sử dụng thuật toán băm để chọn một trong những địa chỉ
> hop tiếp theo trong bộ ECMP để cài đặt trong bảng chuyển tiếp.
>
> **Ví dụ:**
>
> ![](.//media/image80.png)
> 
>
> \- Cho 3 thiết bị định tuyến trong khu vực 0.0.0.0 và giả định rằng
> liên kết giữa R2 và R3 bị tắc nghẽn với lưu lượng truy cập khác. Bạn
> cũng có thể kiểm soát luồng của các gói trên mạng bằng cách gán thủ
> công một số liệu cho một phân đoạn đường dẫn cụ thể. Bất kỳ giá trị
> nào bạn cấu hình đều ghi đè lên giá trị mặc định của việc sử dụng giá
> trị băng thông tham chiếu để tính toán chi phí tuyến đường cho giao
> diện đó. Để ngăn chặn lưu lượng truy cập từ R3 đi trực tiếp đến R2,
> cần điều chỉnh số liệu trên giao giao diện R3 kết nối với R1 để tắt
> tất cả lưu lượng truy cập đi qua R1.

-   Đặt băng thông tham chiếu thành 10g (10 Gbps, được biểu thị bằng
    10.000.000.000 bit) bằng cách bao gồm tuyên bố băng thông tham
    chiếu. Với cấu hình này, OSPF gán cổng Fast Ethernet số liệu mặc
    định là 100 và cổng Gigabit Ethernet là 10. Vì giao diện Gigabit
    Ethernet có số liệu thấp nhất, OSPF chọn nó khi định tuyến các gói.
    Phạm vi là 9600 đến 1.000.000.000.000 bit.

> -\> Cấu hình băng thông tham chiếu?

-   Đặt số liệu thành 5 trên cổng fe-1/0/1 của R3 kết nối với R1 bằng
    cách bao gồm câu trả lời số liệu. Phạm vi từ 1 đến 65.535.

> -\> Cấu hình Số liệu cho Giao diện OSPF cụ thể?

**Giải:**

\- **Cấu hình băng thông tham chiếu:**

-   Cấu hình nhanh CLI:

> set protocols ospf reference-bandwidth 10g

-   Quy trình từng bước:

> user\@host# **set protocols ospf reference-bandwidth 10g**
>
> user\@host# **commit**

-   Kết quả:

> Xác nhận cấu hình bằng cách nhập lệnh **show protocols ospf**.

![](.//media/image81.png)


> \- **Cấu hình số liệu cho Giao diện OSPF cụ thể:**

-   Cấu hình nhanh CLI:

> set protocols ospf area 0.0.0.0 interface fe-1/0/1 metric 5

-   Quy trình từng bước:

> user\@host# edit protocols ospf area 0.0.0.0
>
> user\@host# set interface fe-1/0/1 metric 5
>
> user\@host# commit

-   Kết quả:

> Xác nhận cấu hình bằng cách nhập lệnh **show protocols ospf**
>
> ![](.//media/image82.png)
> 

-   **Tự động điều chỉnh các chỉ số giao diện OSPF dựa trên băng thông**

> \- Bạn có thể chỉ định một tập hợp các giá trị ngưỡng băng thông và
> giá trị số liên quan cho cổng OSPF hoặc cho cấu trúc liên kết trên
> cổng OSPF. Khi băng thông của cổng thay đổi, Junos OS sẽ tự động đặt
> số liệu cổng thành giá trị liên quan đến giá trị ngưỡng băng thông
> thích hợp. Junos OS sử dụng giá trị ngưỡng băng thông được cấu hình
> nhỏ nhất bằng hoặc lớn hơn băng thông cổng thực tế để xác định giá trị
> số liệu. Nếu băng thông cổng lớn hơn bất kỳ giá trị ngưỡng băng thông
> nào được cấu hình, giá trị số liệu được cấu hình cho cổng được sử dụng
> thay vì bất kỳ giá trị số liệu dựa trên băng thông nào được cấu hình.
> Khả năng tính toán lại số liệu cho một cổng khi băng thông của nó thay
> đổi đặc biệt hữu ích cho các cổng tổng hợp.
>
> **Ví dụ:**
>
> \- Ta cần cấu hình giao diện OSPF ae0 cho các số liệu dựa trên bằng
> thông bằng cách bao gồm câu trả lời bandwidth-based-metrics với các
> cài đặt sau:

-   bandwidth - chỉ định ngưỡng băng thông theo bit mỗi giây. Phạm vi từ
    9600 - 1.000.000.000.000.000.000.

-   metric - chỉ định giá trị số liệu để liên kết với một giá trị băng
    thông cụ thể. Phạm vi từ 1 đến 65.535.

**Giải:**

\- Cấu hình:

-   Cấu hình nhanh CLI:

> set protocols ospf area 0.0.0.0 interface ae0.0 metric 5
>
> set protocols ospf area 0.0.0.0 interface ae0.0
> bandwidth-based-metrics bandwidth 1g metric 60
>
> set protocols ospf area 0.0.0.0 interface ae0.0
> bandwidth-based-metrics bandwidth 10g metric 50

-   Các bước thực hiện:

> user\@host# **edit protocols ospf area 0.0.0.0**
>
> user\@host# **set interface ae0 metric 5**
>
> user\@host# **set interface ae0.0 bandwidth-based-metrics bandwidth 1g
> metric 60**
>
> user\@host# **set interface ae0.0 bandwidth-based-metrics bandwidth
> 10g metric 50**
>
> user\@host# **commit**

-   Kết quả:

> Xác nhận cấu hình bằng cách nhập lệnh **show protocols ospf**
>
> ![](.//media/image83.png)
> 
>
> **show ospf interface detail** (OSPFv2)
>
> **show ospf3 interface detail** (OSPFv3)

-   **Kiểm soát lựa chọn tuyến đường OSPF**

> \- Bạn có thể kiểm soát luồng các gói thông qua mạng bằng cách sử dụng
> tùy chọn tuyến đường. Tùy chọn tuyến đường được sử dụng để chọn tuyến
> đường nào được cài đặt trong bảng định tuyến khi một số giao thức tính
> toán các tuyến đường đến cùng một đích. Tuyến đường có giá trị ưu tiên
> thấp nhất được chọn.
>
> \- Theo mặc định, các tuyến OSPF nội bộ có giá trị ưu tiên là 10 và
> các tuyến OSPF bên ngoài có giá trị ưu tiên là 150. Mặc dù các thiết
> bị mặc định phù hợp với hầu hết các môi trường, bạn có thể muốn sửa
> đổi cài đặt mặc định nếu tất cả các thiết bị định tuyến trong mạng
> OSPF của bạn sử dụng các giá trị tùy chọn mặc định hoặc nếu bạn đang
> có kế hoạch di chuyển từ OSPF sang giao thức cổng khác (IGP). Nếu tất
> cả các thiết bị sử dụng các giá trị tùy chọn tuyến đường mặc định, bạn
> có thể thay đổi tùy chọn tuyến đường để đảm bảo rằng đường dẫn thông
> qua một thiết bị cụ thể được chọn cho bảng định tuyến bất cứ khi nào
> có nhiều đường dẫn chi phí bằng nhau đến đích. Khi di chuyển từ OSPF
> sang một IGP khác, việc sửa đổi tùy chọn tuyến đường cho phép bạn thực
> hiện di chuyển một cách có kiểm soát.
>
> **Ví dụ:**
>
> \- Ta có các giả định sau:

-   OSPF đã chạy trong mạng.

-   Muốn di chuyển từ OSPF sang IS-IS

-   Đã cấu hình IS-IS theo yêu cầu mạng và xác nhận nó đang hoạt động
    bình thường

\- Trong ví dụ này, ta tăng các giá trị ưu tiên tuyến OSPF để làm cho
chúng it được ưu tiên hơn các tuyến IS-IS bằng cách chỉ định 168 cho các
tuyến OSPF nội bộ (preference) và 169 cho các tuyến OSPF bên ngoài
(external preference). Các tuyến đường nội bộ IS-IS có ưu tiên 15 (đối
với cấp 1) hoặc 18 (đối với cấp 2) và các tuyến đường bên ngoài có ưu
tiên 160 (đối với Cấp độ 1) hoặc 165 (đối với cấp độ 2). Nói chúng, nó
được ưu tiên để lại giao thức mới ở cài đặt mặc định của nó để giảm
thiểu sự phức tạp và đơn giản hóa bất kỳ bổ sung thiết bị định tuyến nào
trong tương lai vào mạng. Để sửa đổi các giá trị tùy chọn tuyến OSPF,
hãy cấu hình các cài đặt sau:

-   preference - Chỉ định ưu tiên tuyến đường cho các tuyến OSPF nội bộ.
    Theo mặc định, các tuyến OSPF nội bộ có giá trị là 10. Phạm vi từ
    0 - 4.294967.295 (2\^32 - 1).

-   external preference - Chỉ định tùy chọn tuyến đường cho các tuyến
    OSPF bên ngoài. Theo mặc định, các tuyến OSPF bên ngoài có giá trị
    là 150. Phạm vi từ 0 - 4.294968.295 (2\^32 - 1).

**Giải:**

\- Cấu hình:

-   Cấu hình nhanh CLI:

> set protocols ospf preference 168 external-preference 169

-   Các bước thực hiện:

> user\@host# **set protocols ospf preference 168 external-preference
> 169**
>
> user\@host# **commit**

-   Kết quả:

> Xác nhận cấu hình bằng cách nhập lệnh **show protocols ospf**
>
> ![](.//media/image84.png)
> 

**c. Path Selection**

\- OSPF cơ bản sẽ sử dụng chi phí làm thước đo để chọn đường dẫn ngắn
nhất cho mỗi điểm đến, điều này đúng nhưng nó không hoàn toàn chính xác.
OSPF trước tiên sẽ xem xét \"loại đường\" để đưa ra quyết định và thứ
hai xem sét số liệu. Đây là danh sách đường dẫn ưu tiên mà OSPF sử dụng:

-   Intra-Area (O)

-   Inter-Area (O IA)

-   External Type 1 (E1)

-   NSSA Type 1 (N1)

-   External Type 2 (E2)

-   NSSA Type 2 (N2)

\- Sau khi tuyến đường được chọn nó sẽ tìm giá trị đường thấp nhất. Ví
du: \"X\" được học rằng có một intra-area (O) và inter-area (O IA) sau
đó OSPF sẽ luôn luôn chọn intra-area (O) định tuyến, ngay cả khi
inter-area (O IA) định tuyến có giá trị thấp hơn.

\- Lưu ý: Từ khi Cisco IOS ra mắt phiên bản 15.1(2)S, Cisco sử dụng
phương pháp chọn đường đi từ RFC 3101, điều này không còn hiệu lực với
RFC 1587. Điều này có nghĩa là nó ưu tiên các tuyến N1 trước E1 và N2
trước E2. Nói cách khác, danh sách đường dẫn ưu tiên là **O \> O IA \>
N1 \> E1 \> N2 \> E2.**

# Tài liệu tham khảo

> https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/cdp/configuration/15-mt/cdp-15-mt-book/nm-cdp-discover.html
>
> https://vnpro.vn/thu-vien/giao-thuc-cdp-cisco-discovery-protocol-3129.html
>
> https://www.cisco.com/c/en/us/support/docs/routers/10000-series-routers/50421-config-register-use.html
>
> https://networklessons.com/ospf/troubleshooting-ospf-neighbor-adjacency
>
> https://ipwithease.com/ospf-lsa-types/
>
> https://www.firewall.cx/networking-topics/routing/ospf-routing-protocol/1178-ospf-lsa-types-explained.html
>
> https://www.cisco.com/c/en/us/td/docs/iosxr/ncs5xx/segment-routing/72x/b-segment-routing-cg-72x-ncs540/configure-sr-for-ospf.html#task_4D379C0F92814C319A7D5C567C87DF2A
>
> https://vnpro.vn/thu-vien/chuong-7-ospf-3718.html
>
> https://vnpro.vn/thu-vien/chuong-10-giao-thuc-dinh-tuyen-ospf-phan-4-3443.html
>
> https://www.juniper.net/documentation/en_US/junos/topics/topic-map/ospf-traffic-control.html
>
> https://www.juniper.net/documentation/en_US/junos/topics/topic-map/ospf-route-summarization.html
>
> https://study-ccna.com/ospf-summarization/
>
> https://networklessons.com/ospf/ospf-path-selection-explained
