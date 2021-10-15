**Báo Cáo Công Việc Tuần 1**

# Tổng quát kết quả Pnetlab #tổng-quát-kết-quả-pnetlab .list-paragraph

  -------------------------------------------------------------------------
  **STT**   **Nội dung công việc**           **Kết quả**
  --------- -------------------------------- ------------------------------
  1         Cisco Discovery Protocol         Hoàn thành

  2         Changing the Configuration       Hoàn thành
            Register on IOS devices          

  3         Trouble shooting OSPFv2 Neighbor Chưa hoàn thành
            Adjacencies                      

  4         OSPF LSA Types and Functions     Hoàn tành

  5         Segment Routing OSPF Basic       Hoàn thành

  6         OSPF Route LSA Filtering STUB    Chưa hoàn thành (câu 3, 4, 5,
            NSSA                             6)

  7         OSPF Summarization and Path      Chưa hoàn thành (câu 5, 6, 7)
            Control                          

  8         Cài đặt hệ thống Pnetlab trên    Chưa hoàn thành
            Server khoa CNTT                 
  -------------------------------------------------------------------------

# Cisco discovery protocol

a.  **Mục tiêu Lab:**

-   Mục tiêu nhằm học và hiểu được cách kích hoạt CDP và điều chỉnh CDP
    timers.

-   Hiểu được CDP là kĩ năng cơ bản. CDP là một giao thức độc quyền của
    Cisco có thể được sử dụng cho khám phá thiết bị cũng như khắc phục
    sự cố kết nối Internet. Là một kỹ sư Cisco, bạn sẽ biết cách kích
    hoạt và sử dụng CDP trong mạng Internet phát hiện và xử lý sự cố.

b.  **Sơ đồ Lab:**

> Sơ đồ mạng Lab được minh họa như hình dưới:
>
> ![](.//media/image1.png)width="4.615227471566055in"
> height="2.7399660979877516in"
>
> **Câu 1**: Cấu hình hostname trên R1 và SW1 như trong hình
>
> ![](.//media/image2.png)width="3.06292760279965in"
> height="1.0105577427821522in"
>
> ![](.//media/image3.png)width="3.03125in"
> height="1.2921675415573053in"
>
> **Câu 2**: Cấu hình địa chỉ IP 172.29.199.1/24 trên R1 e0/0
>
> ![](.//media/image4.png)width="4.854166666666667in"
> height="1.402833552055993in"
>
> **Câu 3**: Cấu hình VLAN 200 trên SW1 và đặt tên cho nó là CDP_VLAN.
> Cấu hình cổng VLAN 200 trên SW1 với địa chỉ IP 172.29.199.2/24. Gán
> cổng Ethernet0/2 trên SW1 cho VLAN này.
>
> ![](.//media/image5.png)width="5.354166666666667in"
> height="1.3448337707786526in"
>
> ![](.//media/image6.png)width="3.17752624671916in"
> height="0.8959580052493439in"
>
> ![](.//media/image7.png)width="5.239584426946632in"
> height="1.4432906824146983in"
>
> **Câu 4**: Kích hoạt CDP trên cả R1 và SW1. Định cấu hình R1 và SW1 để
> gửi các gói CDP cứ sau 10 giây.
>
> ![](.//media/image8.png)width="4.1672484689413825in"
> height="1.7398261154855643in"
>
> ![](.//media/image9.png)width="4.135994094488189in"
> height="1.6773173665791776in"
>
> **Câu 5**: Sử dụng CDP và xem thông tin chi tiết về SW1 từ R1. Làm
> quen với thông tin cung cấp.
>
> ![](.//media/image10.png)width="5.031944444444444in"
> height="4.17403980752406in"

# Changing the Configuration Register on IOS devices

a.  **Mục tiêu Lab:**

-   Mục tiêu nhằm học và hiểu được cách thay đổi giá trị đăng ký cấu
    hình trên các thiết bị Cisco.

-   Thay đổi đăng ký cấu hình là kĩ năng cơ bản. Đăng ký cấu hình thường
    là đã thay đổi khi thực hiện quy trình khôi phục mật khẩu trên thiết
    bị Cisco IOS. Các thiết lập trong thanh ghi cấu hình được sử dụng để
    thay đổi hành vi mặc định của các thiết bị Cisco IOS. Như một kỹ sư
    của Cisco, cũng như trong kỳ thi CCNA của Cisco, bạn sẽ phải biết
    cách thay đổi và xác minh số đăng ký cấu hình.

b.  **Sơ đồ Lab:**

> Sơ đồ mạng Lab được minh họa như hình dưới:
>
> ![](.//media/image11.png)width="5.219478346456693in"
> height="2.5836942257217848in"
>
> **Câu 1:** Cấu hình bất kỳ tên máy mong muốn nào trên thiết bị của bạn
>
> ![](.//media/image12.png)width="5.145834426946632in"
> height="1.385094050743657in"
>
> **Câu 2:** Xác minh cài đặt hiện tại của thanh ghi cấu hình bằng lệnh
> hiển thị phiên bản
>
> ![](.//media/image13.png)width="4.833334426946632in"
> height="2.2824070428696412in"
>
> ![](.//media/image14.png)width="4.8125in"
> height="1.7987707786526683in"
>
> **Câu 3:** Thay đổi giá trị thanh ghi cấu hình thành 102 và lưu cấu
> hình của bạn. Xác minh rằng đăng ký cấu hình mới của bạn sẽ được sử
> dụng sau khi thiết bị của bạn đã được khởi động lại
>
> ![](.//media/image15.png)width="3.4900699912510937in"
> height="0.531324365704287in"
>
> ![](.//media/image16.png)width="4.738888888888889in"
> height="2.2237510936132985in"
>
> ![](.//media/image17.png)width="4.766147200349956in"
> height="0.40562992125984254in"
>
> ![](.//media/image18.png)width="3.7291666666666665in"
> height="0.8160520559930009in"

# Troubleshooting OSPFv2 Neighbor Adjacencies

Ta có mô hình mạng sau:

![](.//media/image19.png)width="6.5in" height="2.779166666666667in"

Trong đó có 12 lỗi được giấu dưới 7 router. Ta cần tìm và sửa lỗi chúng.
Nếu như tất cả các lỗi sau được sửa thì PC1 có thể ping được PC2.

a.  **Interface is down**

b.  **Interface not running the OSPF process**

c.  **Timers mitmatched**

d.  **Area numberes mitmatched**

e.  **Area type mismatched**

f.  **Different subnets**

g.  **Passive interfaces**

h.  **Authentication information mismatched**

i.  **ACLs blocked**

j.  **MTU mismatched**

k.  **Duplicated router ID**

l.  **Network type mismatched**

# OSPF LSA types and functions

a.  **Mục tiêu Lab:**

-   Giúp hiểu về OSPF và các loại LSA khác nhau mà nó sử dụng.

b.  **Sơ đồ mạng:**

> Sau đây là sơ đồ mạng:
>
> ![](.//media/image20.png)width="6.5in" height="4.13125in"

**Câu 1: Basic IP**

> Cấu hình các thiết bị area0 với hostanme và địa chỉ IP
>
> Cấu hình kết nối IP cơ bản giữa các thiết bị area0
>
> Tất cả thiết bị nên sử dụng số Router riêng của chúng như là octet
> cuối cùng trong 1 mạng con
>
> VD: Mạng giữa Router 1 và 2 là 10.1.2.0/24 và R1 nên được cấu hình với
> địa chỉ IP 10.1.2.1/24 và R2 với địa chỉ IP 10.1.2.2/24.
>
> Tất cả các cổng loopback0 nên sử dụng địa chỉ 155.R.R.R/32 trong đó R
> là số của router.
>
> VD: R2 nên có cổng lo0 với địa chỉ 155.2.2.2/32

![](.//media/image21.png)width="5.25in" height="3.635176071741032in"

![](.//media/image22.png)width="2.1374365704286964in"
height="1.59375in"![](.//media/image23.png)width="2.1145833333333335in"
height="1.6036045494313211in"

![](.//media/image24.png)width="2.14418416447944in"
height="1.40625in"![](.//media/image25.png)width="1.8125in"
height="1.4876629483814523in"

**Câu 2: Backbone OSPF**

Cấu hình OSPFv2 với id 1 trên tất cả link và loopback area0

![](.//media/image26.png)width="4.416666666666667in"
height="0.6065813648293963in"

![](.//media/image27.png)width="4.521464348206474in"
height="0.6146686351706037in"

![](.//media/image28.png)width="4.51104658792651in"
height="0.5938331146106737in"

![](.//media/image29.png)width="4.479792213473316in"
height="0.5938331146106737in"

![](.//media/image30.png)width="3.6110148731408573in"
height="2.90625in"

![](.//media/image31.png)width="3.6104166666666666in"
height="2.8001804461942257in"

Nếu ta nhìn vào LSDB của R1 ta có thể thấy LSA loại 2 cho từng DR trên
mạng đa truy cập trong phân loại và LSA loại 1 cho mỗi router có mạng
được kết nối của chúng.

![](.//media/image32.png)width="4.729166666666667in"
height="2.657503280839895in"

![](.//media/image33.png)width="2.2916666666666665in"
height="2.571707130358705in"

![](.//media/image34.png)width="2.4629035433070867in"
height="1.46875in"

**Câu 3: Area1**

Cấu hình hostname, basic IP trên R5

Cấu hình OSPF trong area 1 như vùng bình thường

Cấu hình OSPF trong area 1 với câu lệnh mạng càng cụ thể càng tốt

Tắt giao thức OSPF trên các giao diện không cần thiết

![](.//media/image35.png)width="4.427082239720035in"
height="2.658082895888014in"

![](.//media/image36.png)width="3.854704724409449in"
height="0.40630686789151355in"

Cấu hình trên R5:

![](.//media/image37.png)width="3.3645833333333335in"
height="2.2687390638670166in"

Kiểm tra R5 đã bảng định tuyến OSPF đầy đủ và có thể ping tới các địa
chỉ loopback0 khác:

![](.//media/image38.png)width="3.2083333333333335in"
height="2.6360345581802274in"

**Câu 4: Area 2 STUB**

Cấu hình hostname, basic IP trên R6 và R10

Cấu hình OSPF trên area 2 là stub area

Cấu hình OSPF trên area 2 càng rõ ràng càng tốt

Loại bỏ giao thức OSPF trên các cổng không cần thiết

Tóm tắt mạng khách 10.6.200.0/24 và 10.6.201.0/24 thành 1 địa chỉ khi đi
qua ABR R2 trong Area 0

![](.//media/image39.png)width="5.187501093613299in"
height="2.9060411198600176in"

![](.//media/image40.png)width="4.688153980752406in"
height="0.9897211286089239in"

![](.//media/image41.png)width="4.979168853893263in"
height="0.46990376202974626in"

![](.//media/image42.png)width="2.3413123359580053in"
height="2.8958333333333335in"![](.//media/image43.png)width="2.6666666666666665in"
height="2.720237314085739in"

Kiểm tra rằng các router đã có thể ping địa chỉ lo0 của các thiết bị
khác

![](.//media/image44.png)width="5.020832239720035in"
height="1.7905839895013123in"

Bây giờ ta có thể xác nhận rằng R1 chỉ tóm tắt định tuyến 10.6.200.0/23
từ R2 trong vùng Area 0 LSDB:

![](.//media/image45.png)width="2.7402777777777776in"
height="2.5477176290463692in"![](.//media/image46.png)width="2.614582239720035in"
height="1.4425284339457567in"

Điều quan trọng cần biết là lý do tuyến đường này là LSA loại 3, không
phải vì nó đã tóm tắt trên R2 mà bởi vì nó vượt qua từ một đường không
phải đường trục vào đường trục. Như ta có thể thấy trên R3:

![](.//media/image47.png)width="3.78125in"
height="2.120201224846894in"

**Câu 5: Area 4 Totally Stub**

Cấu hình hostname, basic IP trên R11

Cấu hình OSPF trên area 4 là totally stub area

Cấu hình OSPF trên R11 chỉ cần cấu hình cổng

Loại bỏ giao thức OSPF trên các cổng không cần thiết

![](.//media/image48.png)width="5.031952099737532in"
height="2.792055993000875in"

![](.//media/image49.png)width="3.9901399825021873in"
height="0.6875962379702537in"

![](.//media/image50.png)width="3.261794619422572in"
height="2.0729166666666665in"

Hãy lưu ý rằng chỉ LSA loại 1 và 2 xuất hiện trong khu vực hoàn toàn sơ
khai và một LSA loại 3. Giá trị mặc định từ ABR:

![](.//media/image51.png)width="3.2194444444444446in"
height="2.7997670603674543in"

**Câu 6: EIGRP**

Cấu hình hostanme, basic IP trên R7-9

Cấu hình EIGRP AS 100 nhử thể hiện trong sơ đồ

Bao gồm lo0 của R7-9 trong giao thức EIGRP

![](.//media/image52.png)width="4.229166666666667in"
height="2.6265354330708663in"

![](.//media/image53.png)width="3.156248906386702in"
height="1.6548108048993875in"

![](.//media/image54.png)width="3.1770833333333335in"
height="1.6461570428696413in"

![](.//media/image55.png)width="3.2083333333333335in"
height="1.2697889326334209in"

Đảm bảo định tuyến đầy đủ được quảng bá trong domain EIGRP:

![](.//media/image56.png)width="5.104167760279965in"
height="0.9972615923009623in"

![](.//media/image57.png)width="3.6666666666666665in"
height="2.5303302712160978in"

![](.//media/image58.png)width="4.614580052493438in"
height="0.9444564741907262in"

**Câu 7: NSSA**

Cấu hình định tuyến OSPFv2 trong area 3 là NSSA giữa tất cả các router

Cấu hình OSPF với câu lệnh nhất định trên R3,R4 và R7

Điều hướng tất cả EIGRP AS 100 định tuyến thành OSPF trên R7

Điều hướng tất cả OSPF định tuyến thành EIGRP trên R7

![](.//media/image59.png)width="5.209060586176728in"
height="3.1983628608923884in"

![](.//media/image60.png)width="3.375in" height="0.6144455380577428in"

![](.//media/image61.png)width="3.2916666666666665in"
height="1.0831200787401576in"

![](.//media/image62.png)width="3.706522309711286in"
height="1.6145833333333333in"

Xác nhận R9 đã có tất cả định tuyến OSPF là EIGRP External

![](.//media/image63.png)width="2.343748906386702in"
height="1.830793963254593in"![](.//media/image64.png)width="1.8536811023622046in"
height="1.84375in"

**Câu 8: External connectivity**

Cấu hình eBGP giữa R1 trong AS 1 và R99 trong AS 99

Trên R99 thêm định tuyến mặc định để truyền trong BGP hướng tới R1

Đảm bảo R1 thêm tuyến mặc định vào miền OSPF

Nhưng tuyến mặc định chỉ nên tồn tại trong miền OSPF nếu nó có mặt trên
R1

![](.//media/image65.png)width="3.6145833333333335in"
height="4.080424321959755in"

![](.//media/image66.png)width="3.6666666666666665in"
height="2.441373578302712in"

![](.//media/image67.png)width="3.7083333333333335in"
height="1.3400568678915135in"

Nếu bạn nhìn vào R5 sẽ thấy tất cả intra-area LSA, inter-area LSA và
external LSA:

![](.//media/image68.png)width="2.934152449693788in"
height="2.7916666666666665in"

![](.//media/image69.png)width="2.9270833333333335in"
height="1.695181539807524in"

Nếu bạn nhìn vào một khu vực hoàn toàn sơ khai như khu 4 trên R11, bạn
sẽ chỉ thấy LSA trong khu vực và một LSA loại 3 duy nhất là tuyến đường
mặc định:

![](.//media/image70.png)width="4.353832020997375in"
height="2.6464457567804023in"

# Segment Routing OSPF Basic

a.  **Mục tiêu Lab:**

> Mục tiêu của bài Lab này là để học và hiểu về cách thức cấu hình
> Segment Routing trong IGP (OSPF)

b.  **Sơ đồ Lab:**

> ![](.//media/image71.png)width="6.5in" height="2.342361111111111in"
>
> **Câu 1:** Cấu hình hostname và địa chỉ IP cho các cổng của các Router
> trong mô hình
>
> ![](.//media/image72.png)width="3.584809711286089in"
> height="1.5104166666666667in"
>
> R2
>
> ![](.//media/image73.png)width="3.9375in"
> height="2.7830096237970254in"
>
> ![](.//media/image74.png)width="3.9583333333333335in"
> height="1.8257425634295712in"
>
> **Câu 2:** Cấu hình Segment Routing Global Block cho mỗi Router theo
> bảng sau:
>
> ![](.//media/image75.png)width="3.9276312335958004in"
> height="0.9063768591426071in"
>
> ![](.//media/image76.png)width="4.261011592300962in"
> height="1.0313943569553805in"
>
> R2
>
> ![](.//media/image77.png)width="4.281847112860892in"
> height="0.8438681102362204in"
>
> ![](.//media/image78.png)width="4.2714293525809275in"
> height="0.8855402449693788in"
>
> **Câu 3:** Cấu hình OSPF Routing trong 4 Router và kích hoạt Segment
> Routing trên vùng OSPF
>
> ![](.//media/image79.png)width="4.3125in"
> height="2.0510673665791774in"
>
> R2
>
> ![](.//media/image80.png)width="4.135415573053368in"
> height="1.809773622047244in"
>
> ![](.//media/image81.png)width="4.104166666666667in"
> height="1.6081627296587926in"
>
> **Câu 4:** Kiểm tra khả năng kết nối giữa R1 và R4 và phân tích cơ sở
> dữ liệu OSPF trên một trong cách Router

# OSPF Route LSA Filtering STUB NSSA

a.  **Mục tiêu Lab:**

> Mục tiêu của bài Lab này là để hiểu về sự hoạt động OSPF và cấu hình
> trên các router Cisco. Ngoài ra các công nghệ kiểm tra bao gồm các
> vùng Stub/NSSA và định tuyến và LSA filtering.

b.  **Sơ đồ Lab:**

> ![](.//media/image82.png)width="6.480071084864392in"
> height="5.552858705161855in"

**Câu 1:** Cấu hình hostname và địa chỉ IP trên tất cả Router theo mô
hình mạng

![](.//media/image83.png)width="2.0185597112860894in"
height="1.875in"![](.//media/image84.png)width="2.03125in"
height="1.8827285651793526in"

![](.//media/image85.png)width="2.018024934383202in"
height="2.3125in"![](.//media/image86.png)width="2.4583333333333335in"
height="1.425197944006999in"

**Câu 2**: Sử dụng lệnh với mạng x.x.x.x y.y.y.y area \<area> để cấu
hình OSPF, cấu hình như trên sơ đồ mạng. Tất cả các vùng nên được cấu
hình các vùng OSPF bình thường ngoại trừ vùng 4, là vùng được cấu hình
NSSA. Xác nhận lại cấu hình.

![](.//media/image87.png)width="2.9270833333333335in"
height="2.9144674103237094in"

![](.//media/image88.png)width="3.1979166666666665in"
height="1.9423359580052493in"

![](.//media/image89.png)width="3.4791666666666665in"
height="2.6391108923884516in"

![](.//media/image90.png)width="4.261011592300962in"
height="1.1980839895013122in"

**Câu 3**: Cấu hình định tuyến tĩnh trên R4 và redistribute chúng là
Loại 1 External routes:

192.168.1.0/24 via 150.4.4.254

192.168.2.0/24 via 150.4.4.254

Tiếp theo, cấu hình mạng OSPF mà truyền địa chỉ ở dạng LSA loại 5 mô tả
các lưu lượng nên được truyền đến R3 (ASBR Loại 5 LSA) và không đến R4
(ASBR Loại 7 LSA). Mặt khác, đảm bảo rằng các địa chỉ được truyền của
loại 5 LSA được chỉnh đến 0.0.0.0. Xác nhận lại cấu hình.

**Câu 4**: Cấu hình cổng Loopback11 trên R11 với địa chỉ IP
11.11.11.11/32. Redistribute cổng này thành OSPF sử dụng loại metric mặc
định và các giá trị metric. Sau khi route redistribute, cấu hình OSPF
cho tất cả router có thể ping được mạng con từ mạng con LAN của chúng.
VD: thừ địa chỉ 150.x.x.x. Xác nhận cấu hình.

**Câu 5**: Cấu hình OSPF để mạng con 150.3.3.0/24 kết nối đến R3 LAN
cũng như mạng con 150.4.4.0/24 kết nối đến R4 LAN và không được quảng bá
đến bất kỳ vùng nào khác. Đừng sử dụng ACL hoặc prefix-list dựa vào các
giao thức filtering khi thực hiện quá trình này. Tuy nhiên, đảm bảo rằng
R1 và R2 vẫn có thể ping 150.3.3.3 cũng như 150.4.4.4. Xác nhận lại cấu
hình.

**Câu 6**: Cấu hình OSPF để mạng con 150.1.1.0/24 và 150.2.2.0/24 chỉ
không được quảng bá ở vùng 3. Chúng vẫn nên được quảng bá ở các vùng
khác. Đùng sử dụng bất kỳ distribute list nào khi hoàn thành câu này.
Xác nhận lại cấu hình.

# OSPF Summarization and Path Control

a.  **Mục tiêu Lab:**

> Bài Lab này tập trung iểu về cách thức hoạt động của OSPF và cấu hình
> trên các router Cisco. Thêm vào đó các công nghệ kiểm tra bao gồm
> Summarization và Path Control

b.  **Sơ đồ Lab:**

> ![](.//media/image91.png)width="6.5in" height="3.615972222222222in"
>
> **Câu 1**: Cấu hình hostname và địa chỉ IP trên tất cả router giống
> như trong mô hình mạng
>
> ![](.//media/image92.png)width="2.511599956255468in"
> height="1.0729166666666667in"![](.//media/image93.png)width="1.9375in"
> height="1.111884295713036in"
>
> ![](.//media/image94.png)width="2.5392825896762905in"
> height="1.8541666666666667in"![](.//media/image95.png)width="2.75in"
> height="0.9284798775153106in"
>
> **Câu 2**: Cấu hình backbone OSPF trên vùng LAN giữa R1 và R4
>
> ![](.//media/image96.png)width="4.625645231846019in"
> height="0.625087489063867in"
>
> ![](.//media/image97.png)width="4.552718722659668in"
> height="0.635505249343832in"
>
> **Câu 3**: Cấu hình OSPF area 1 giữa R1, R2 và R3. Đừng quảng bá mạng
> con 150.3.3.0/24 trên R3 qua OSPF
>
> ![](.//media/image98.png)width="3.5729166666666665in"
> height="0.9317300962379702in"
>
> ![](.//media/image99.png)width="3.46875in"
> height="2.090240594925634in"
>
> ![](.//media/image100.png)width="3.8229166666666665in"
> height="2.039438976377953in"
>
> **Câu 4**: Cấu hình OSPF area 2 giữa R1, R3 và R4. Đừng quảng bá mạng
> con 150.3.3.0/24 trên R3 qua OSPF
>
> ![](.//media/image101.png)width="4.073485345581802in"
> height="0.6146686351706037in"
>
> ![](.//media/image102.png)width="4.1047397200349955in"
> height="0.739686132983377in"
>
> ![](.//media/image103.png)width="4.15625in"
> height="0.9086176727909011in"
>
> **Câu 5**: Cấu hình các mạng sau trên cổng LAN của R3:

1.  172.16.12.0/24

2.  172.16.13.0/24

3.  172.16.14.0/24

4.  172.16.15.0/24

> Tiếp theo, thêm mạng con 150.3.3.0/24 là Loại 2 External LSA. Các mạng
> con 172.16.x.x/24 nên được thêm vào OSPF ở dạng Loại 1 External LSA.
> Có thể sử dụng 1 prelix list hoặc ACL để thực hiện. Xác nhận lại cấu
> hình.
>
> **Câu 6**: Quảng bá định tuyến đơn cho các mạng con 172.16.x.x/24 kết
> nối đến cổng LAN trên R3. Định tuyến đơn nên được gắn tag 3333. Địa
> chỉ tóm tắt không nên được thể hiện trong OSPF area 0. Tuy nhiên, nó
> nên ở OSPF area 1 và 2. Xác nhận lại cấu hình
>
> **Câu 7**: Cấu hình OSPF để R3 ưu tiên đường đi qua R2 đến OSPF
> backbone. Vd: 10.0.1.0/24 nên được cấu hình ưu tiên đường đi qua R2
> đến mạng con 150.3.3.0/24. Nó nên được hoàn thành mà không điều chỉnh
> băng thông cổng. Xác nhận lại cấu hình.

# Cài đặt hệ thống Pnetlab trên Server khoa CNTT
