# LLDP and DHCPv6

## LLDP (Link Layer Discovery Protocol)

> \- LLDP hay còn gọi là giao thức khám phá lớp liên kết, dùng để thu
> thập thông tin các thiết bị lân cận kết nối tới thiết bị để quảng bá
> những thông tin về chúng cho những thiết bị khác trên hệ thống. Giao
> thức này hoạt động ở layer 2 (Layer Data Link). Giao thức không thuộc
> hãng nào, hoạt động tương tự CDP (Cisco Discovery Protocol) của Cisco.
>
> \- Nó là một tiêu chuẩn mở cho các thiết bị mạng để truyền đạt cấu
> trúc lớp liên kết và thông tin kết nối của điểm cuối trên IEEE 802
> (Ethernet) LAN và MAN. LLDP được mô tả trong tài liệu chuẩn IEEE
> 802.1AB, Phát hiện kết nối kiểm soát truy cập trạm và phương tiện. Nó
> cho phép một trạm trên mạng quảng cáo thông tin về khả năng, cấu hình
> và nhận dạng của nó với các trạm hỗ trợ LLDP khác trên cùng một mạng
> vật lý. Thông tin này được lưu trữ trong thiết bị dưới dạng cơ sở
> thông tin quản lý tiêu chuẩn (MIB) theo quy định trong RFC 2922. Một
> hệ thống quản lý mạng có thể truy vấn các MIB này bằng cách sử dụng
> SNMP để mô phỏng hóa cấu trúc của mạng.
>
> \- Mặc định LLDP không được kích hoạt sẵn trên thiết bị, do đó để sử
> dụng LLDP thì chúng ta cần kích hoạt bằng lệnh: **lldp run** trong
> Global Configuration Mode. Để vô hiệu hóa LLDP ta nhập lệnh **no lldp
> run**
>
> \- Ta cũng có thể kích hoạt lldp trên từng cổng như sau:
>
> S1(config)# **int g0/1**
>
> S1(config-if)# **lldp transmit**
>
> S1(config-if)# **lldp receive**
>
> S1(config-if)# **end**
>
> \- Khi dịch vụ được kích hoạt, ta có thể ghi lại thông tin về vị trí,
> địa chỉ quản lý và cổng của thiết bị, cũng như các giao thức cũ mà nó
> hỗ trợ. Thông tin bổ sung, bao gồm các khả năng cấu hình của hệ thống
> và hàng xóm, đước trích xuất tự động từ hệ thống và được lưu trữ trong
> MIB.
>
> \- Để xem thông tin các thiết bị láng giềng ta dùng lệnh **show lldp
> neighbors**
>
> ![](.//media/image1.png)
> 
>
> \- Câu lệnh **show lldp neighbors detail** cho chúng ta biết thông tin
> chi tiết hơn về thiết bị láng giềng, ở đây ta có thể biết thêm các
> port của thiết bị hỗ trợ chuẩn gì. VD: Trong thiết bị láng giềng có hỗ
> trợ chuẩn 1000baseT, như vậy tốc độ ở port có dùng chuẩn đó có thể lên
> đến 1000Gbps.
>
> ![](.//media/image2.png)
> 

## DHCPv6

> **Tổng quát**
>
> \- DHCPv6 (Dynamic Host Configuration Protocol version 6): là giao
> thức cấu hình động máy chủ phiên bản 6. Là một giao thức truyền thông
> để cấu hình các host IPv6 với địa chỉ IPv6, tiền tố IP và các dữ liệu
> cấu hình khác cần thiết để hoạt động trong mạng IPv6. Đây là phiên bản
> IPv6 tương đương DHCPv4.
>
> \- Host IPv6 sử dụng cấu hình tự động không trạng thái có thể yêu cầu
> thông tin khác với địa chỉ IP hoặc tuyến đường. DHCPv6 có thể được sử
> dụng để thu thập thông tin này, mặc dù nó không được sử dụng để cấu
> hình địa chỉ IP. DHCPv6 không cần thiết để cấu hình host với các địa
> chỉ của các máy chủ DNS, vì chúng có thể được cấu hình sử dụng
> Neighbor Discovery Protocol, đây cũng là cơ chế tự động cấu hình không
> trạng thái.
>
> \- Nhiều bộ định tuyến IPv6, VD: router cho mạng trong nhà (HAN), phải
> được định cấu hình tự động mà không cần sự can thiệp của người vận
> hành. Các bộ định tuyến như vậy không chỉ yêu cầu một địa chỉ Ipv6 để
> sử dụng giao tiếp với các bộ định tuyến thượng nguồn (upstream router)
> mà còn cần một tiền tố IPv6 để sử dụng trong việc cấu hình các thiết
> bị ở phía hạ lưu (downstream) của router. DHCPv6 prefix delegation
> cung cấp một cơ chế để cấu hình các router như vậy.
>
> **Các thành phần của DHCPv6**
>
> \- Giống như DHCP cho IPv4, các thành phần của DHCPv6 cũng bao gồm:

-   DHCPv6 Client: Gửi yêu cầu cung cấp các thông tin cấu hình

-   DHCPv6 Server: Cung cấp các thông tin cấu hình

-   DHCP Relay Agent: ĐIểm chuyển tiếp các gói tin giữa client và server
    chúng không thuộc cùng một vùng mạng

**Cấu hình**

> **-** Một DHCPv6 Client sẽ thực hiện chế độ cấu hình tự động bằng cách
> sử dụng DHCPv6 dựa trên các cờ (flag) trong gói tin quảng bá của
> router (RA).

\- DHCPv6 có thể được cấu hình theo 2 dạng:

-   DHCPv6 không trạng thái: Trong trường hợp này, cờ O (O = Other
    Configuration) được thiết lập trong gói tin quảng bá của router
    (Router Advertisement), chỉ dẫn nút tự tạo ra địa chỉ IPv6 cho nó,
    chỉ sử dụng DHCPv6 để lấy các thông số cấu hình khác có sẵn (vd: địa
    chỉ máy chủ DNS, DNS-Suffix, NTP-Server,\...)

-   DHCPv6 có trạng thái: Hoạt động tương đương với hoạt động của một
    nút IPv4 sử dụng DHCPv4 để nhận toàn bộ cấu hình IP của nó. Trong
    trường hợp này, M flag (M = Managed Configuration) được thiết lập
    trong gói tin quảng bá của router, nó chỉ thị cho nút lấy một địa
    chỉ IPv6 từ máy chủ DHCPv6 bên cạnh những thông số khác.

**Nguyên lý hoạt động của DHCPv6**

-   **Chế độ DHCPv6 có trạng thái**

> Chế độ này có được khi cả hai cờ \"M\" và cờ \"O\" trong gói tin quảng
> bá đều được thiết lập là 1. Cách thức trao đổi gói tin DHCPv6 như sau:

1.  Client sẽ gửi một gói tin multicast \"Solicit\" để tìm kiếm máy chủ
    DHCPv6 và yêu cầu cấp phát.

2.  Bất kỳ máy chủ nào đáp ứng yêu cầu của client có thể hồi đáp với một
    gói tin \"Advertise\"

3.  Client lựa chọn một trong các máy chủ và gửi một gói tin \"Request\"
    để yêu cầu cấp phát địa chỉ IPv6 và các thông số khác

4.  Máy chủ đáp ứng với một gói tin \"Reply\", bao gồm địa chỉ và các
    thông số cấu hình để hoàn tất quá trình cấp phát

> Trong trường hợp Rapid Commit có thể thực hiện nhanh hơn với chỉ hai
> gói tin Solicit và Reply.
>
> Trong trường hợp giữa Client và Server còn có thêm điểm chuyển tiếp,
> thực hiện trao đổi gói tin có thêm các bước:
>
> \- Relay-Forw: Dùng để chuyển tiếp các gói tin Solicit và Request từ
> client đến server.
>
> \- Relay-Reply: Dùng để chuyển tiếp các gói tin Advertise và Reply từ
> server đến client.

-   **Chế độ Stateless DHCPv6 không trạng thái**

> Chế độ này được thiết lập khi cờ \"M\" được thiết lập 0 và cờ \"O\"
> được thiết lập 1 trong gói tin quảng bá. Trong mạng IPv6, router được
> cấu hình để cung cấp các địa chỉ prefix cho các máy trạm IPv6, vì vậy
> DHCPv6 chỉ dùng để cấp phát các thông tin cấu hình khác như: máy chủ
> DNS, tên miền và các cấu hình khác mà trong gói tin quảng bá của
> router không có.
>
> Vì các lý do này, chế độ Stateless DHCPv6 chỉ có hai dạng gói tin:

-   Information-Request: Gửi bởi client để yêu cầu các thông số cấu hình
    khác từ máy chủ DHCP (không phải địa chỉ IP)

-   Reply: Gửi bởi server cho client, bao gồm các thông tin về thông số
    cấu hình được yêu cầu cấp phát.

**Thông số hoạt động của giao thức DHCPv6**

\- Các cổng hoạt động:

-   UDP port 546: Các client thực hiện lắng nghe (listen) gói tin DHCP.

-   UDP port 547: Các máy chủ và điểm chuyển tiếp lắng nghe (listen) gói
    tin DHCP.

Các địa chỉ IPv6 multicast được sử dụng với DHCPv6:

-   \"FF02::1:2\": Dùng cho tất cả điểm chuyển tiếp và máy chủ DHCPv6.

-   \"FF05::1:3\": Dùng cho tất cả các máy chủ DHCPv6.

Cách thức nhận biết DHCPv6 Client:

-   DHCPv6 sử dụng DUID (DHCP Unique Identifier) để xác định tính duy
    nhất cho các DHCPv6 Client. Mỗi DHCPv6 client sẽ có một DUID, được
    sử dụng để xác định các thiết bị khi trao đổi gói tin DHCPv6.

# IPv6 Tunnels and OSPFv3 Lab

## a.   IPv6 Tunnels

    **i.  Tổng quan công nghệ đường hầm Tunnel**

> \- Công nghệ đường hầm là một phương pháp sử dụng cơ sở hạ tầng sẵn có
> của mạng IPv4 để thực hiện các kết nối IPv6 bằng cách sử dụng các
> thiết bị mạng có khả năng hoạt động dual-stack tại hai điểm đầu và
> cuối nhất định. Các thiết bị này \"bọc\" gói tin IPv6 trong gói tin có
> header IPv4 và truyền tải đi trong mạng IPv4 tại điểm đầu và gỡ bỏ
> IPv4 Header, nhận lại gói tin IPv6 ban đầu tại điểm đích cuối đường
> truyền IPv4 như hình:
>
> ![](.//media/image3.png)
> 
>
> Giá trị của trường Protocol Field trong IPv4 Header luôn được xác lập
> có giá trị 41 để xác định đây là gói tin IPv6 được bọc trong gói tin
> IPv4. Do vậy để các gói tin có thể truyền đi trên cơ sở hạ tầng mạng
> IPv4, nếu trên đường kết nối có sử dụng firewall, firewall này cần
> phải được thiết lập để cho phép gói tin có giá trị Protocol 41 đi qua.
>
> Điểm kết thúc tunnel có thể được xác định tại host hoặc router tạo nên
> kết nối như sau:

-   Router-to-Router

-   Host-to-Router hoặc Router-to-Host

-   Host-to-Host

> Với nhiều công nghệ tạo tunnel khác nhau, các IPv6 host, hay mạng IPv6
> riêng biệt hiện nay trên Internet đều có thể có kết nối IPv6, đều có
> thể kết nối vào mạng Internet IPv6 để thử nghiệm, tìm hiểu hay thực sự
> trao đổi thông tin. Tất nhiên các host và mạng này phải có kết nối
> Internet IPv4 và lựa chọn một công nghệ tunnel phù hợp.
>
> Như vậy, nếu bạn đang có kết nối với mạng Internet IPv4, bạn chỉ muốn
> thử nghiệm kết nối IPv6 trên một host hay bạn đang có một mạng IPv6,
> đều có thể kết nối được vào IPv6 Internet, hoặc kết nối với mạng IPv6
> khác trên Internet.
>
> **Phân loại công nghệ Tunnel:**
>
> \- Tùy theo công nghệ tunnel, các điểm bắt đầu và kết thúc đường
> tunnel có thể được cấu hình bằng tay bởi người quản trị, hoặc được tự
> động suy ra từ địa chỉ nguồn và địa chỉ đích của gói tin IPv6. Đường
> kết nối tunnel sẽ có dạng kết nối point-to-point hoặc
> point-to-multipoint. Dựa theo cách thức thiết lập điểm đầu và cuối
> đường hầm (tunnel), công nghệ tunnel có thể phân thành hai loại:
> tunnel bằng tay và tunnel tự động.

-   **Tunnel bằng tay (Configured)**

> \- Tunnel bằng tay là hình thức tạo đường hầm kết nối IPv6 trên cơ sở
> hạ tầng mạng IPv4, trong đó đòi hỏi phải có cấu hình bằng tay các điểm
> kết thúc tunnel. Trong tunnel cấu hình bằng tay, các điểm kết cuối
> đường hầm này sẽ không được suy ra từ các địa chỉ nằm trong địa chỉ
> nguồn và địa chỉ đích của gói tin.
>
> \- Trực tiếp cấu hình đường tunnel, công nghệ Tunnel Broker là công
> nghệ tunnel bằng tay.

-   **Tunnel tự động (Automatic)**

> \- Tunnel tự động là công nghệ tunnel trong đó không đòi hỏi phải cấu
> hình địa chỉ IPv4 của điểm bắt đầu và kết thúc tunnel bằng tay. Địa
> chỉ IPv4 của điểm bắt đầu và kết thúc tunnel được rút ra sử dụng giao
> diện ảo tunnel, tuyến (route), địa chỉ nguồn và địa chỉ đích của gói
> tin IPv6.
>
> \- Có nhiều công nghệ tunnel tự động, trong đó có công nghệ tunnel
> hiện không còn được sử dụng nữa.
>
> **Nguyên tắc hoạt động của việc tạo đường hầm trong công nghệ
> tunnel:**

-   Xác định thiết bị kết nối tại các điểm đầu và cuối đường hầm. Hai
    thiết bị này phải có khả năng hoạt động dual-stack.

-   Xác định địa chỉ IPv4 và địa chỉ IPv6 nguồn và đích của giao diện
    tunnel (hai đầu kết thúc tunnel)

-   Trên hai thiết bị kết nối tại đầu và cuối tunnel, thiết lập một giao
    diện tunnel (giao diện ảo, không phải giao diện vật lý) dành cho
    những gói tin IPv6 sẽ được bọc trong gói tin IPv4 đi qua.

-   Gắn địa chỉ IPv6 cho giao diện tunnel.

-   Tạo tuyến (route) để các gói tin IPv6 đi qua giao diện tunnel. Tại
    đó, chúng được bọc trong gói tin IPv4 có giá trị trường Protocol 41
    và chuyển đi dựa trên cơ sở hạ tầng mạng IPv4 và nhờ định tuyến
    IPv4.

    i.  **Cấu hình bằng tay đường hầm Tunnel**

> \- Thông qua thông tin về cấu hình bằng tay đường hầm Tunnel ở trên.
> Thông thường, hình thức tạo đường hầm bằng tay này thường được cấu
> hình để tạo đường hầm giữa router-to-router (hai border router) nhằm
> kết nối hai mạng IPv6 xác định sử dụng cơ sở hạ tầng mạng IPv4. Nó
> cũng có thể được cấu hình giữa router và host để kết nối IPv6 host vào
> một mạng IPv6 từ xa.
>
> ![](.//media/image4.png)
> 
>
> \- Việc cấu hình giao diện tunnel, bao gồm địa chỉ IPv6 gắn cho giao
> diện tunnel, địa chỉ IPv4 của các điểm kết thúc cần được cấu hình bằng
> tay cùng với tuyến sẽ sử dụng giao diện tunnel.
>
> \- Tunnel cấu hình bằng tay tương đương với một đường link vĩnh viễn
> (permanent link) giữa hai miền IPv6 trên cơ sở hạ tầng mạng IPv4, cho
> một kết nối ổn định giữa hai điểm xác định. Dạng kết nối tunnel này là
> kết nối điểm - điểm, tạo nên một đường kết nối ổn định, bảo mật, riêng
> biệt. Tính chất này tương tự như khi ta cấu hình định tuyến tĩnh
> (static route) so với định tuyến động (dynamic route). Tuy nhiên, nó
> đòi hỏi cấu hình, quản trị thụ động. Nếu muốn kết nối tới nhiều điểm,
> sẽ phải tạo nhiều giao diện tunnel và nhiều đường tunnel.
>
> \- Trong trường hợp một tổ chức có hai phân mạng IPv6 tại hai vùng địa
> lý và chỉ có cơ sở hạ tầng IPv4 giữa hai phân mạng này. Trong trường
> hợp đó, để có thể có kết nối IPv6, tạo một tunnel cấu hình bằng tay
> giữa hai router gateway của hai phân mạng có thể là sự lựa chọn tốt
> nhất để có một kết nối ổn định.

**ii. Tunnel Broker**

> \- Tunnel Broker là hình thức tunnel, trong đó một tổ chức đứng ra làm
> trung gian, cung cấp kết nối tới Internet IPv6 cho những thành viên
> đăng ký sử dụng dịch vụ Tunnel Broker do tổ chức cung cấp.
>
> \- Tổ chức cung cấp dịch vụ Tunnel Broker có vùng địa chỉ IPv6 độc
> lập, toàn cầu, xin cấp từ các tổ chức quản lý địa chỉ IP quốc tế, mạng
> IPv6 của tổ chức có kết nối tới Internet IPv6 và những mạng IPv6 khác.
> Thành viên đăng ký và được cấp quyền sử dụng dịch vụ Tunnel Broker sẽ
> nhận được những thông tin từ tổ chức quản lý Tunnel Broker để thiết
> lập đường hầm tunnel từ host hoặc từ router gateway mạng IPv6 của tổ
> chức mình tới mạng của tổ chức duy trì Tunnel Broker, từ đó kết nối
> tới được Internet IPv6 hay những mạng IPv6 khác mà tổ chức duy trì
> Tunnel Broker có kết nối tới như hình:
>
> ![](.//media/image5.png)
> 
>
> Người sử dụng sẽ kết nối tới được IPv6 Internet và các mạng IPv6 khác
> khi đăng ký và được phép sử dụng dịch vụ Tunnel Broker của nhà cung
> cấp. Người sử dụng sẽ được tổ chức cung cấp thông tin để thiết lập
> đường hầm từ host hoặc mạng của mình đến mạng của tổ chức duy trì
> Tunnel Broker và dùng mạng này như một trung gian để kết nối tới các
> mạng IPv6 khác. Người đăng ký sử dụng dịch vụ Tunnel Broker sẽ được
> cung cấp vùng địa chỉ một vùng địa chỉ thuần IPv6, tùy theo nhu cầu sử
> dụng từ không gian địa chỉ IPv6 của nhà cung cấp dịch vụ tunnel broker
> và được chuyển giao một không gian tên miền cấp dưới không gian tên
> miền của nhà cung cấp dịch vụ Tunnel Broker. Đây là địa chỉ và tên
> miền hợp lệ toàn cầu, thành viên của Tunnel Broker có thể sử dụng tên
> miền này để thiết lập IPv6 Website cho phép những mạng IPv6 có kết nối
> tới mạng của nhà cung cấp dịch vụ Tunnel Broker truy cập tới.
>
> \- Đường hầm thiết lập giữa người sử dụng và mạng của nhà cung cấp
> dịch vụ Tunnel Broker được cấu hình trên nguyên lý Tunnel bằng tay.
>
> **Mô hình của Tunnel Broker**
>
> ![](.//media/image6.png)
> 
>
> **Tunnel Broker:**
>
> \- Là những máy chủ dịch vụ làm nhiệm vụ quản lý thông tin đăng ký,
> cho phép sử dụng dịch vụ, quản lý việc tạo đường hầm, thay đổi thông
> tin đường hầm cũng như xóa đường hầm. Trong hệ thống dịch vụ Tunnel
> Broker của nhà cung cấp, máy chủ Tunnel Broker sẽ liên lạc với Tunnel
> Server (dual-stack server) và máy chủ tên miền của nhà cung cấp Tunnel
> Broker để thiết lập đường hầm phía nhà cung cấp dịch vụ Tunnel Broker
> và tạo bản ghi tên miền cho người đăng ký sử dụng dịch vụ Tunnel
> Broker.
>
> \- Người sử dụng thông qua mạng Internet IPv4 sẽ truy cập máy chủ
> Tunnel Broker và đăng ký tài khoản sử dụng dịch vụ Tunnel Broker thông
> qua mẫu đăng ký dưới dạng web.
>
> **Tunnel Server:**
>
> \- Là các router dual-stack làm nhiệm vụ cung cấp kết nối để người
> đăng ký sử dụng dịch vụ kết nối tới để truy cập vào mạng IPv6 của tổ
> chức cung cấp Tunnel Broker. Các router này là điểm kết thúc tunnel
> phía nhà cung cấp dịch vụ Tunnel Broker. Tunnel Server nhận yêu cầu từ
> máy chủ Tunnel Broker và tạo, hoặc xóa đường tunnel phía nhà cung cấp
> Tunnel Broker.

1.  **Liên hệ giữa người dùng, Tunnel Broker, Tunnel Server, máy chủ tên
    miền Đăng ký sử dụng dịch vụ Tunnel Broker**

> \- Nếu người sử dụng chỉ muốn kết nối một host vào mạng IPv6 của nhà
> cung cấp Tunnel Broker, sẽ đăng ký dạng host và yêu cầu cấp một địa
> chỉ (/128). Nếu người sử dụng muốn kết nối một mạng, cần đăng ký và
> Tunnel Broker sẽ cấp cho một vùng địa chỉ theo nhu cầu (thường là
> prefix /64 nếu mạng IPv6 của tổ chức chỉ có một subnet duy nhất hoặc
> prefix /48 nếu mạng IPv6 của tổ chức có nhiều subnet và cần nhiều hơn
> một prefix /64).
>
> **Thiết lập đường hầm phía nhà cung cấp dịch vụ Tunnel Broker:**
>
> \- Khi nhận được thông tin đăng ký và chấp nhận yêu cầu, máy chủ
> Tunnel Broker sẽ liên hệ với Tunnel Server, máy chủ tên miền của nhà
> cung cấp dịch vụ Tunnel Broker để thiết lập đường hầm phía nhà cung
> cấp Tunnel Broker và tạo bản ghi tên miền rồi gửi các thông tin cần
> thiết phục vụ cho người sử dụng tạo đường hầm phía người sử dụng
> (thông qua email, hoặc web form).
>
> **Thông tin được gửi tới người sử dụng thường bao gồm:**

-   Địa chỉ IPv4 phía Client (người sử dụng, địa chỉ này do người sử
    dụng cung cấp cho Tunnel Broker khi đăng ký). Đây sẽ là địa chỉ IPv4
    của đầu tunnel phía người dùng.

-   Địa chỉ IPv4 phía Server (địa chỉ IPv4 của dual-stack router của nhà
    cung cấp Tunnel Broker, là các Tunnel Server). Đây là địa chỉ IPv4
    của đầu tunnel phía nhà cung cấp dịch vụ Tunnel Broker.

-   Địa chỉ IPv6 phía Client. Đây là địa chỉ Ipv6 thuộc vùng địa chỉ
    Ipv6 của nhà cung cấp dịch vụ Tunnel Broker cấp cho người đăng ký để
    sử dụng cho mạng IPv6 và cho kết nối.

-   Địa chỉ IPv6 phía Server (Địa chỉ IPv6 của dual-stack router của nhà
    cung cấp Tunnel Broker).

-   Tên miền nhà cung cấp Tunnel Broker cấp cho người sử dụng. Đây là
    tên miền hợp lệ toàn cầu, đăng ký trên máy chủ tên miền của nhà cung
    cấp dịch vụ Tunnel Broker.

**Thiết lập đường hầm phía người dùng:**

> \- Dựa trên những thông tin nhận được, người sử dụng sẽ cấu hình bằng
> tay trên host hoặc router của mình đường hầm tunnel kết nối với mạng
> của nhà cung cấp dịch vụ. Đây là Tunnel cấu hình bằng tay. Trên các
> HĐH khác nhau và các thiết bị mạng khác nhau có hỗ trợ IPv6 sẽ cung
> cấp các tập hợp lệnh tương ứng để cấu hình tunnel.
>
> \- Trong nhiều trường hợp, tổ chức cung cấp dịch vụ Tunnel Broker xây
> dựng các chương trình Client giúp người dùng không phải trực tiếp gõ
> lệnh để thiết lập tunnel mà chỉ việc cài đặt chương trình và giao tiếp
> với chương trình qua giao diện.

**Một số tổ chức cung cấp dịch vụ Tunnel Broker toàn cầu:**

> \- Hiện nay trên toàn cầu, có rất nhiều tổ chức cung cấp dịch vụ
> Tunnel Broker miễn phí. Bạn có thể tham khảo danh sách sau đây và đăng
> ký sử dụng dịch vụ Tunnel của tổ chức này:

-   http://tunnelbroker.net (Mỹ)

-   http://tb.ipv6.btexact.com (Anh)

-   \...

## OSPFv3

> \- OSPFv3 là phiên bản mới của OSPF được xây dựng để định tuyến cho
> IPv6, được định nghĩa trong RFC-2740 của IETF. Về mặt hoạt động, OSPF
> giữ lại rất nhiều đặc điểm trong hoạt động của OSPFv2 (chạy trong
> IPv4).
>
> \- Là một giao thức Link-state điển hình: các thông tin định tuyến
> được trao đổi là các bản tin LSA, sử dụng giải thuật Dijkstra để tính
> toán đường đi tối ưu đến mọi đích trong mạng.
>
> \- Trên router Cisco, OSPFv3 cũng sử dụng giá trị AD là 110.
>
> \- Metric được tính bằng cost tích lũy trên các interface.
>
> -\...
>
> Điểm khác biệt:
>
> \- Địa chỉ multicast của OSPF là các địa chỉ IPv6: FF02::5 và FF02::6.
>
> \- OSPFv3 đưa ra thêm một số loại LSA mới để tối ưu hóa hoạt động của
> giao thức OSPF.
>
> \- OSPFv3 sử dụng tính năng IP Sec của IPv6 để thực hiện xác thực định
> tuyến, thay vì phải đưa ra các cơ chế xác thực riêng như với OSPFv2.
>
> Tương tự như với OSPFv2 của IPv4, mỗi router khi tham gia OSPFv3 cũng
> cần phải được định danh duy nhất bởi một giá trị gọi là router-id.
> Điểm đặc biệt của OSPFv3 là giá trị router-id này vẫn sử dụng định
> danh của một địa chỉ IPv4. Do đó, khi OSPF được bật trên router, tiến
> trình OSPFv3 sẽ tự động lấy địa chỉ IPv4 cao nhất trong các interface
> đang active (up/up) và ưu tiên cổng loopback.
>
> Trong trường hợp sơ đồ mạng được cấu hình là một chỉ chạy IPv6, OSPF
> sẽ không tự chọn được router-id vì không có địa chỉ IPv4. Lúc đó, tiến
> trình OSPF sẽ phát ra một thông điệp cảnh báo và yêu cầu người quản
> trị phải cấu hình tĩnh giá trị router-id cho router.
>
> Để cấu hình giá trị router-id, thực hiện lệnh \"router-id\" trong mode
> cấu hình OSPFv3:
>
> R(config)# **ipv6 router ospf** *[process-id].ul*

R(config-rtr)# **router-id** *[A.B.C.D].ul*

> OSPFv3 không sử dụng lệnh \"network\" để cho các cổng tham gia định
> tuyến. Người quản trị cần phải lên từng cổng để bật định tuyến OSPFv3
> bằng lệnh:
>
> R(config)# **ipv6 ospf** *[process-id].ul* **area** *[area-id].ul*
>
> VD:
>
> ![](.//media/image7.png)
> 
>
> Thực hiện cấu hình OSPFv3 trên sơ đồ này đảm bảo mọi địa chỉ trên sơ
> đồ thấy nhau.
>
> ![](.//media/image8.png)
> ![](.//media/image9.png)
> 
>
> ![](.//media/image10.png)
> 
>
> -\> Ở cấu hình trên các router được cấu hình tĩnh các giá trị
> router-id:
>
> R1: 1.1.1.1
>
> R2: 2.2.2.2
>
> R3: 3.3.3.3
>
> Các cổng của các router được cấu hình để tham gia OSPF Area 0.
>
> Tiếp tục, dùng lệnh show ipv6 route hoặc show ipv6 route ospf để kiểm
> tra các route OSPF trong bảng định tuyến:
>
> ![](.//media/image11.png)
> 
>
> ![](.//media/image12.png)
> 
>
> ![](.//media/image13.png)
> 

# IPV6 OSPFv3 Lab

## Định tuyến trên IPv6

> \- Tương tự như các IPv4 node, các IPv6 node sử dụng một bảng định
> tuyến IPv6 cục bộ để quyết định cách để truyền packet đi. Các entry
> trong bảng định tuyến được tạo một cách mặc định khi IPv6 khởi tạo và
> các entry khác sẽ được thêm vào khi nhận được các gói tin Router
> Advertisement chứa các prefix và các route, hay qua việc cấu hình tĩnh
> bằng tay.

I.  **Bảng định tuyến IPv6:**

> \- Một bảng định tuyến sẽ có mặt trên tất cả các node chạy giao thức
> IPv6. Bảng định tuyến lưu những thông tin về các subnet của mạng và
> một next hop để có thể đến được subnet đó. Trước khi bảng định tuyến
> được kiểm tra, thì destination cache sẽ được kiểm tra trước xem có
> những entry nào trong đó match với địa chỉ đích có trong IPv6 header
> của packet hay không. Nếu không có thì bảng định tuyến sẽ được sử dụng
> để quyết định:

-   Interface: được sử dụng để truyền gói tin (next hop interface).
    Interface xác định interface vật lý hay luận lý được sử dụng để
    truyền gói tin đến đích của nó hay router tiếp theo.

-   Địa chỉ next hop: với những đích nằm trên cũng một liên kết cục bộ
    thì địa chỉ next hop chính là địa chỉ đích của packet. Với những
    đích không nằm cùng subnet thì địa chỉ next hop chính là địa chỉ của
    một router.

> \- Sau khi interface và địa chỉ next hop được xác định thì node sẽ cập
> nhật destination cache. Các gói tin tiếp theo sẽ được truyền đến đích
> sử dụng cache entry này mà không phải kiểm tra bảng định tuyến.

II. **Các giao thức định tuyến trong IPv6:**

> \- Việc tạo một mạng IPv6 chứa nhiều subnet được kết nối với nhau bởi
> các IPv6 router. Để có thể đến được tất cả các host trong mạng thì các
> route phải tồn tại trên các host và trên các router. Những route này
> có thể là route chung (như một default route) hay một route xác định
> đại diện cho một subnet. Các host thường sử dụng những route được kết
> nối trực tiếp để đến những node lân cận và một default route để đến
> tất cả những vị trí khác. Các router thường sử dụng những route xác
> định để đến những vị trí trong site của nó và những route tóm tắt để
> đến những site khác hay ra internet. Mặc dù việc cấu hình trên các
> host về các route đều được làm tự động qua các gói tin quảng bá từ
> router, nhưng việc cấu hình trên các router thì phức tạp hơn. Một
> router có thể có các route được cấu hình tĩnh hay động qua việc sử
> dụng các giao thức định tuyến.
>
> \- Việc định tuyến tĩnh dựa trên các entry trong bảng định tuyến được
> cấu hình tĩnh và không thay đổi thi cấu trúc thay đổi. Một router với
> bảng định tuyến được cấu hình tĩnh được gọi là một router tĩnh. Nhà
> quản trị mạng phải biết rõ cấu trúc của mạng để có thể tự tay xây dựng
> và cập nhật nội dung bảng định tuyến. Các router tĩnh có thể hoạt động
> tốt trên những mạng nhỏ, nhưng không có khả năng mở rộng cho những
> mạng lớn hay tự động thay đổi khi mạng thay đổi.
>
> \- ĐỊnh tuyến tự động là việc tự động cập nhật bảng định tuyến cho mỗi
> sự thay đổi trên mạng. Router được cấu hình cho việc định tuyến động
> được gọi là dynamic router. Các bảng định tuyến được duy trì tự động
> giữa các router. Các giao thức định tuyến (Routing protocol) đảm nhận
> công việc định tuyến động. Các giao thức định tuyến động có khả năng
> phát hiện được lỗi trên mạng nên định tuyến động là lựa chọn tốt cho
> mạng vừa, lớn, có thể rất lớn.
>
> Routing protocol được dùng giữa các router và được thể hiện bằng các
> luồng thông tin cập nhật lan truyền trên mạng.
>
> \- Các giao thức định tuyến trên IPv6:

-   RIPng cho IPV6

-   OSPF cho IPv6

-   IS-IS cho IPv6

-   BGP-4

-   IDRPv2

-   EIGRP cho IPv6

    a.  ## Định tuyến OSPFv3

> \- OSPF IPv6 là một giao thức link-state được định nghĩa trong RFC
> 2740. OSPF được thiết kế để chạy như một hệ tự trị. OSPF IPv6 được xây
> dựng trên OSPFv2 của IPv4. OSPF cost ở mỗi link được admin gán cho, và
> không phải là duy nhất. Cost đó bao gồm: thời gian trễ, đường truyền,
> cost, và tổng phải nhỏ hơn 65.535.

i.  **OSPF IPv6 có sự thay đổi so với OSPFv2:**

> \- Cấu trúc của gói OSPF được sửa đổi để loại bỏ sự độc lập trong việc
> phân địa chỉ IPv4.
>
> \- Có LSA được định ra để mang địa chỉ IPv6 và prefix.
>
> \- OSPF thường chạy trên mỗi link, chứ không trên mỗi subnet.
>
> \- Phạm vi của network cho việc flooding LSA được tổng quát hóa.
>
> Giao thức OSPF không cung cấp việc ủy quyền. Thay vào đó, OSPF dựa
> trên Authetication header (AH) và Encapsulating Security Payload (ESP)
> header and trailer.

ii. **Hoạt động OSPF IPv6:**

> \- Mỗi router có một LSA để miêu tả trạng thái hiện tại của nó. LSA
> của mỗi OSPF IPv6 router thì hiệu quả cho việc lan truyền khắp nơi
> trên mạng OSPF thông qua mối quan hệ với các neighboring routers được
> gọi là adjacencies. Khi tất cả sự lan truyền của tất cả các LSA ở
> router hiện tại hoàn thành, mạng OSPF được gọi là hội tự (converged).
>
> \- Dựa trên tập hợp các OSPF LSA - được biết là link state database
> (LSDB) - OSPF tính toán đường đi có giá thấp nhất cho mỗi lộ trình, và
> những con đường ấy trở thành OSPF routes trong bảng định tuyến IPv6.
> Để giảm kích thước của LSDB, OSPF cho phép tính toán và tạo ra ở mỗi
> vùng. Một vùng OSPF là một nhóm các segment của mạng liên tiếp nhau.
> Trong tất cả các mạng OSPF, có ít nhất một vùng được gọi là backbone.
> Vùng OSPF cho phép tổng kết hoặc tập hợp các thông tin định tuyến trên
> các vùng OSPF biên. Một router tại vùng biên của vùng OSPF được gọi là
> Area Border Router (ABR).

# Cài đặt hệ thống giám sát Pnetlab (Nagios)

## Giới thiệu tổng quan về Nagios

> \- Nagios Core là một phần mềm mã nguồn mở và giám sát mạng. Nó sẽ
> theo dõi hệ thống, dịch vụ mạng và sẽ cảnh báo khi mà có sự cố xảy ra
> với những gì nó theo dõi. Như là CPU chạy quá tải hay một host bị hỏng
> không còn hoạt động, dịch vụ ssh bị lỗi,\...
>
> \- Nagios core được phát hành từ năm 1999 bởi Ethan Galstad, và lúc đó
> nó có cái tên là Nestaint. Đến năm 2002 được đổi tên thành Nagios và
> năm 2009 nó đã chính thức có tên là Nagios core.
>
> \- Một số chức năng nagios cung cấp:

-   Giám sát tài nguyên máy chủ

-   Giám sát dịch vụ mạng

-   Giám sát phần cứng

-   Giám sát từ xa

-   Cung cấp phương thức cảnh báo khi gặp sự cố

-   ...

## a.  Các khái niệm trong Nagios core

**i.  Plugins:**

> \- Là một lớp trừu tượng giữa nagios server và host hay service
>
> \- Là một dòng lệnh hay có thể là một đoạn script
>
> \- Plugins có chức năng kiểm tra host và service rồi trả lại kết quả
> cho nagios server.

**ii. **Web server:**![](.//media/image14.png)
    > 

> \- Là nơi lưu trữ các file, các thành phần của website (file html,
> css, ảnh,\...)
>
> \- Là nơi cung cấp dữ liệu của website cho người dùng muốn truy cập và
> sử dụng. Nó sẽ cung cấp dữ liệu cho người dùng thông qua Internet.

**iii.  **DATABASE (DB):**

> \- DB bao gồm DATA và DBMS
>
> \- DATA: Là loại dữ liệu của nagios server. Dữ liệu này là thông tin
> của các client sau khi được kiểm tra
>
> \- DBMS là hệ quản trị cơ sở dữ liệu. Được thiết kế nhằm mục đích quản
> lý dữ liệu dễ dàng hơn, bảo mật cao hơn. Theo mặc định thì DATA của
> nagios server sẽ được lưu trữ trong file nhưng có thể lưu trữ nó ở
> trong một hệ quản trị cơ sở dữ liệu.
>
> \- Trên DB người dùng sẽ dễ dàng thao tác với dữ liệu được lưu trữ
> trong file
>
> \- Trong nagios có hỗ trợ 2 DB là mysql và postgreSQL.

**iv. CGI (Common Gateway Interface):**

> ![](.//media/image15.png)
> 
>
> \- CGI hay còn được gọi là giao diện dòng lệnh nó cung cấp giao thức
> để web server sử dụng.
>
> \- Web Server thường gửi thông tin biểu mẫu cho một quy trình xử lý dữ
> liệu và có thể gửi lại thông báo xác nhận. Quá trình đó được gọi là
> CGI.
>
> \- CGI có thể được viết nên từ ngôn ngữ nào đó như: C, perl,
> shell,\...

## Ưu điểm và nhược điểm của Nagios core

> **- Ưu điểm:**

-   Là một phần mềm mã nguồn mở và miễn phí

-   Giám sát tập trung

-   Có thể tích hợp được nhiều ngôn ngữ khác nhau

-   Có một cộng đồng phát triển plugins lớn, vì vậy có rất nhiều các
    plugins đã có sẵn.

> **- Nhược điểm:**

-   Giao diện đồ họa lâu đời

-   Không có khả năng tự phát hiện host khi được thêm vào. Người quản
    trị sẽ phải cấu hình thủ công tất cả các host và các service. Việc
    này ảnh hưởng đến khả năng mở rộng quy mô khó khăn.

## Luồng hoạt động của Nagios core

> ![](.//media/image16.png)
> 
>
> \- Bước 1: Client sẽ sử dụng giao thức http để tạo yêu cầu thông tin
> website cho nagios server
>
> \- Bước 2: Web server sẽ sử dụng CGI để lấy thông tin từ nagios server
>
> \- Bước 3: Nagios server sẽ xem lại file cache. Nếu trong đó có thông
> tin mà client yêu cầu thì nó sẽ lập tức trả lại kết quả. Nếu không có
> nagios sẽ tạo ra một plugins để kiểm tra lại thông tin mà client yêu
> cầu
>
> \- Bước 4: Plugins sẽ check thông tin theo yêu cầu và sau đó trả lại
> thông tin lại cho nagios server
>
> \- Bước 5: Sau khi được nhận thông tin từ plugins thì nagios server sẽ
> lưu trữ thông tin đó vào một file hoặc một DB do cài đặt của người
> quản trị. Và đồng thời nó sẽ lưu trữ thông tin này vào file cache nếu
> người quản trị có sử dụng chức năng của file này
>
> \- Bước 6: Nagios sẽ xác định những việc phải làm dựa trên thông tin
> được trả về từ nagios. Có cần cảnh báo hay không và đánh giá trạng
> thái của các host hay service. Rồi sau đó trả lại thông tin cho
> webserver
>
> \- Bước 7: Web server sẽ sử dụng lại giao thức http trả lại thông tin
> mà client yêu cầu.

# Tài liệu tham khảo 

https://vi.wikipedia.org/wiki/Link_Layer_Discovery_Protocol#:\~:text=Giao%20th%E1%BB%A9c%20LLDP%20(Link%20Layer,2%20(Layer%20Data%20Link).

https://studfile.net/preview/5367052/page:42/

https://nhvd.xyz/2020/12/06/phat-hien-lang-gieng/

https://kcntt.duytan.edu.vn/Home/ArticleDetail/vn/128/4920/lldp-la-gi

https://ladigi.vn/dhcpv6-la-gi-chi-tiet-ve-dhcpv6-moi-nhat-2021

https://waren.vn/chuyen-de/cong-nghe-duong-ham-tunnel-chuyen-de-dao-tao-ipv6-phan-15.html

https://thegioimang.vn/dien-dan/threads/t%C3%ACm-hi%E1%BB%83u-v%C3%A0-c%E1%BA%A5u-h%C3%ACnh-ripng-v%C3%A0-ospfv3-trong-ipv6.2242/

https://www.forum.vnpro.org/forum/ccnp-enterprise/advanced-routing/27019-ospfv3

https://news.cloud365.vn/huong-dan-su-dung-nrpe-cua-nagios-de-giam-sat-mot-may-linux/

https://news.cloud365.vn/huong-dan-cai-dat-nagios-core-4-x-tren-centos-7/

https://news.cloud365.vn/gioi-thieu-tong-quan-ve-nagios-core/

https://news.cloud365.vn/huong-dan-canh-bao-qua-mail-khi-su-dung-nagios/
