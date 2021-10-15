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
> ![](.//media/image1.png)
> 
>
> **Câu 1**: Cấu hình hostname trên R1 và SW1 như trong hình
>
> ![](.//media/image2.png)
> 
>
> ![](.//media/image3.png)
> 
>
> **Câu 2**: Cấu hình địa chỉ IP 172.29.199.1/24 trên R1 e0/0
>
> ![](.//media/image4.png)
> 
>
> **Câu 3**: Cấu hình VLAN 200 trên SW1 và đặt tên cho nó là CDP_VLAN.
> Cấu hình cổng VLAN 200 trên SW1 với địa chỉ IP 172.29.199.2/24. Gán
> cổng Ethernet0/2 trên SW1 cho VLAN này.
>
> ![](.//media/image5.png)
> 
>
> ![](.//media/image6.png)
> 
>
> ![](.//media/image7.png)
> 
>
> **Câu 4**: Kích hoạt CDP trên cả R1 và SW1. Định cấu hình R1 và SW1 để
> gửi các gói CDP cứ sau 10 giây.
>
> ![](.//media/image8.png)
> 
>
> ![](.//media/image9.png)
> 
>
> **Câu 5**: Sử dụng CDP và xem thông tin chi tiết về SW1 từ R1. Làm
> quen với thông tin cung cấp.
>
> ![](.//media/image10.png)
> 

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
> ![](.//media/image11.png)
> 
>
> **Câu 1:** Cấu hình bất kỳ tên máy mong muốn nào trên thiết bị của bạn
>
> ![](.//media/image12.png)
> 
>
> **Câu 2:** Xác minh cài đặt hiện tại của thanh ghi cấu hình bằng lệnh
> hiển thị phiên bản
>
> ![](.//media/image13.png)
> 
>
> ![](.//media/image14.png)
> 
>
> **Câu 3:** Thay đổi giá trị thanh ghi cấu hình thành 102 và lưu cấu
> hình của bạn. Xác minh rằng đăng ký cấu hình mới của bạn sẽ được sử
> dụng sau khi thiết bị của bạn đã được khởi động lại
>
> ![](.//media/image15.png)
> 
>
> ![](.//media/image16.png)
> 
>
> ![](.//media/image17.png)
> 
>
> ![](.//media/image18.png)
> 

# Troubleshooting OSPFv2 Neighbor Adjacencies

Ta có mô hình mạng sau:

![](.//media/image19.png) 

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
> ![](.//media/image20.png) 

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

![](.//media/image21.png) 

![](.//media/image22.png)
![](.//media/image23.png)


![](.//media/image24.png)
![](.//media/image25.png)


**Câu 2: Backbone OSPF**

Cấu hình OSPFv2 với id 1 trên tất cả link và loopback area0

![](.//media/image26.png)


![](.//media/image27.png)


![](.//media/image28.png)


![](.//media/image29.png)


![](.//media/image30.png)


![](.//media/image31.png)


Nếu ta nhìn vào LSDB của R1 ta có thể thấy LSA loại 2 cho từng DR trên
mạng đa truy cập trong phân loại và LSA loại 1 cho mỗi router có mạng
được kết nối của chúng.

![](.//media/image32.png)


![](.//media/image33.png)


![](.//media/image34.png)


**Câu 3: Area1**

Cấu hình hostname, basic IP trên R5

Cấu hình OSPF trong area 1 như vùng bình thường

Cấu hình OSPF trong area 1 với câu lệnh mạng càng cụ thể càng tốt

Tắt giao thức OSPF trên các giao diện không cần thiết

![](.//media/image35.png)


![](.//media/image36.png)


Cấu hình trên R5:

![](.//media/image37.png)


Kiểm tra R5 đã bảng định tuyến OSPF đầy đủ và có thể ping tới các địa
chỉ loopback0 khác:

![](.//media/image38.png)


**Câu 4: Area 2 STUB**

Cấu hình hostname, basic IP trên R6 và R10

Cấu hình OSPF trên area 2 là stub area

Cấu hình OSPF trên area 2 càng rõ ràng càng tốt

Loại bỏ giao thức OSPF trên các cổng không cần thiết

Tóm tắt mạng khách 10.6.200.0/24 và 10.6.201.0/24 thành 1 địa chỉ khi đi
qua ABR R2 trong Area 0

![](.//media/image39.png)


![](.//media/image40.png)


![](.//media/image41.png)


![](.//media/image42.png)
![](.//media/image43.png)


Kiểm tra rằng các router đã có thể ping địa chỉ lo0 của các thiết bị
khác

![](.//media/image44.png)


Bây giờ ta có thể xác nhận rằng R1 chỉ tóm tắt định tuyến 10.6.200.0/23
từ R2 trong vùng Area 0 LSDB:

![](.//media/image45.png)
![](.//media/image46.png)


Điều quan trọng cần biết là lý do tuyến đường này là LSA loại 3, không
phải vì nó đã tóm tắt trên R2 mà bởi vì nó vượt qua từ một đường không
phải đường trục vào đường trục. Như ta có thể thấy trên R3:

![](.//media/image47.png)


**Câu 5: Area 4 Totally Stub**

Cấu hình hostname, basic IP trên R11

Cấu hình OSPF trên area 4 là totally stub area

Cấu hình OSPF trên R11 chỉ cần cấu hình cổng

Loại bỏ giao thức OSPF trên các cổng không cần thiết

![](.//media/image48.png)


![](.//media/image49.png)


![](.//media/image50.png)


Hãy lưu ý rằng chỉ LSA loại 1 và 2 xuất hiện trong khu vực hoàn toàn sơ
khai và một LSA loại 3. Giá trị mặc định từ ABR:

![](.//media/image51.png)


**Câu 6: EIGRP**

Cấu hình hostanme, basic IP trên R7-9

Cấu hình EIGRP AS 100 nhử thể hiện trong sơ đồ

Bao gồm lo0 của R7-9 trong giao thức EIGRP

![](.//media/image52.png)


![](.//media/image53.png)


![](.//media/image54.png)


![](.//media/image55.png)


Đảm bảo định tuyến đầy đủ được quảng bá trong domain EIGRP:

![](.//media/image56.png)


![](.//media/image57.png)


![](.//media/image58.png)


**Câu 7: NSSA**

Cấu hình định tuyến OSPFv2 trong area 3 là NSSA giữa tất cả các router

Cấu hình OSPF với câu lệnh nhất định trên R3,R4 và R7

Điều hướng tất cả EIGRP AS 100 định tuyến thành OSPF trên R7

Điều hướng tất cả OSPF định tuyến thành EIGRP trên R7

![](.//media/image59.png)


![](.//media/image60.png) 

![](.//media/image61.png)


![](.//media/image62.png)


Xác nhận R9 đã có tất cả định tuyến OSPF là EIGRP External

![](.//media/image63.png)
![](.//media/image64.png)


**Câu 8: External connectivity**

Cấu hình eBGP giữa R1 trong AS 1 và R99 trong AS 99

Trên R99 thêm định tuyến mặc định để truyền trong BGP hướng tới R1

Đảm bảo R1 thêm tuyến mặc định vào miền OSPF

Nhưng tuyến mặc định chỉ nên tồn tại trong miền OSPF nếu nó có mặt trên
R1

![](.//media/image65.png)


![](.//media/image66.png)


![](.//media/image67.png)


Nếu bạn nhìn vào R5 sẽ thấy tất cả intra-area LSA, inter-area LSA và
external LSA:

![](.//media/image68.png)


![](.//media/image69.png)


Nếu bạn nhìn vào một khu vực hoàn toàn sơ khai như khu 4 trên R11, bạn
sẽ chỉ thấy LSA trong khu vực và một LSA loại 3 duy nhất là tuyến đường
mặc định:

![](.//media/image70.png)


# Segment Routing OSPF Basic

a.  **Mục tiêu Lab:**

> Mục tiêu của bài Lab này là để học và hiểu về cách thức cấu hình
> Segment Routing trong IGP (OSPF)

b.  **Sơ đồ Lab:**

> ![](.//media/image71.png) 
>
> **Câu 1:** Cấu hình hostname và địa chỉ IP cho các cổng của các Router
> trong mô hình
>
> ![](.//media/image72.png)
> 
>
> R2
>
> ![](.//media/image73.png)
> 
>
> ![](.//media/image74.png)
> 
>
> **Câu 2:** Cấu hình Segment Routing Global Block cho mỗi Router theo
> bảng sau:
>
> ![](.//media/image75.png)
> 
>
> ![](.//media/image76.png)
> 
>
> R2
>
> ![](.//media/image77.png)
> 
>
> ![](.//media/image78.png)
> 
>
> **Câu 3:** Cấu hình OSPF Routing trong 4 Router và kích hoạt Segment
> Routing trên vùng OSPF
>
> ![](.//media/image79.png)
> 
>
> R2
>
> ![](.//media/image80.png)
> 
>
> ![](.//media/image81.png)
> 
>
> **Câu 4:** Kiểm tra khả năng kết nối giữa R1 và R4 và phân tích cơ sở
> dữ liệu OSPF trên một trong cách Router

# OSPF Route LSA Filtering STUB NSSA

a.  **Mục tiêu Lab:**

> Mục tiêu của bài Lab này là để hiểu về sự hoạt động OSPF và cấu hình
> trên các router Cisco. Ngoài ra các công nghệ kiểm tra bao gồm các
> vùng Stub/NSSA và định tuyến và LSA filtering.

b.  **Sơ đồ Lab:**

> ![](.//media/image82.png)
> 

**Câu 1:** Cấu hình hostname và địa chỉ IP trên tất cả Router theo mô
hình mạng

![](.//media/image83.png)
![](.//media/image84.png)


![](.//media/image85.png)
![](.//media/image86.png)


**Câu 2**: Sử dụng lệnh với mạng x.x.x.x y.y.y.y area \<area> để cấu
hình OSPF, cấu hình như trên sơ đồ mạng. Tất cả các vùng nên được cấu
hình các vùng OSPF bình thường ngoại trừ vùng 4, là vùng được cấu hình
NSSA. Xác nhận lại cấu hình.

![](.//media/image87.png)


![](.//media/image88.png)


![](.//media/image89.png)


![](.//media/image90.png)


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

> ![](.//media/image91.png) 
>
> **Câu 1**: Cấu hình hostname và địa chỉ IP trên tất cả router giống
> như trong mô hình mạng
>
> ![](.//media/image92.png)
> ![](.//media/image93.png)
> 
>
> ![](.//media/image94.png)
> ![](.//media/image95.png)
> 
>
> **Câu 2**: Cấu hình backbone OSPF trên vùng LAN giữa R1 và R4
>
> ![](.//media/image96.png)
> 
>
> ![](.//media/image97.png)
> 
>
> **Câu 3**: Cấu hình OSPF area 1 giữa R1, R2 và R3. Đừng quảng bá mạng
> con 150.3.3.0/24 trên R3 qua OSPF
>
> ![](.//media/image98.png)
> 
>
> ![](.//media/image99.png)
> 
>
> ![](.//media/image100.png)
> 
>
> **Câu 4**: Cấu hình OSPF area 2 giữa R1, R3 và R4. Đừng quảng bá mạng
> con 150.3.3.0/24 trên R3 qua OSPF
>
> ![](.//media/image101.png)
> 
>
> ![](.//media/image102.png)
> 
>
> ![](.//media/image103.png)
> 
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
