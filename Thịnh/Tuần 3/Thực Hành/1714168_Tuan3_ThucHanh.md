# DMVPN Phase 3 with IPSec

> **a. Mục tiêu Lab**
>
> \- Bài Lab tập trung để hiểu việc triển khai và cấu hình DMVPN trong
> bộ định tuyến Cisco IOS. Các công nghệ bổ sung được thử nghiệm bao gồm
> DMVPN với IPSec.
>
> **b. Mô hình Lab**
>
> \- Mô hình mạng sau:
>
> ![](.//media/image1.png)
> 
>
> **Câu hỏi:**
>
> \- Tạo một mạng DMVPN giữa R1 - R5 theo các yêu cầu sau:

-   R1 - R4 là các DMVPN Spoke

-   R5 là DMVPN Hub, và NHRP Next-Hop Server (NHS)

-   Tạo cổng Tunnel0 như một multipoint GRE tunnel

-   Nguồn của tunnel từ cổng Ethernet0/0 của các router

-   Sử dụng địa chỉ IP với định dạng 155.1.0.Y/24, trong đó Y là số của
    router

-   Sử dụng 1 là ID mạng NHRP

-   Sử dụng NHRPAUTH là chuỗi xác thực NHRP

-   Sử dụng 2 là GRE tunnel key

-   Đảm bảo các spoke có thể gửi gói tin multicast đến hub, và ngược lại

-   Ngăn các tunnel endpoint từ việc thực hiện phân mãng IPSec, cấu hình
    GRE tunnel\'s IP MTU thành 1400 bytes và thiết lập chúng để điều
    chỉnh TCP MSS cho phù hợp

\- Cấu hình IGP routing thông qua DMVPN tunnel theo các yêu cầu sau:

-   Kích hoạt RIPv2 trên DMVPN tunnel của R1 - R5

-   Tất cả đường dẫn nên là cổng passive ngoại trừ DMVPN tunnel

-   Quảng bá các mạng Loopback0 của các router trong RIP

-   Cấu hình R5 quảng bá định tuyến mặc định qua RIPv2 đến các DMVPN
    spoke

\- Cấu hình IPSec thông qua DMVPN tunnel theo các yêu cầu sau:

-   Sử dụng ISAKMP Policy với các yêu cầu sau:

    -   Pre-Shared Key: DMVPN_PSK

    -   Encryption: AES 128 Bit

    -   Hash: SHA 256 Bit

    -   Diffie-Hellman Group: 16

    -   R5 nên sử dụng một Pre-Shared Key đơn cho tất cả các DMVPN cùng
        loại.

-   Sử dụng Crypto IPSec Profile đặt tên là DMVPN_PROFILE với các yêu
    cầu sau:

    -   Mã hóa gói tin sử dụng AES 256 Bit

    -   Xác thực gói tin sử dụng SHA 512 Bit

    -   Sử dụng chế độ chuyển đổi ESP để tiết kiệm chi phí đóng gói bổ
        sung

\- Khi hoàn thành, đảm bảo R1 - R5 có thể đi đến các mạng Loopback0 của
nhau thông qua mạng DMVPN.

**Cấu hình:**

\- Trên R1:

![](.//media/image2.png)


![](.//media/image3.png)


![](.//media/image4.png)


\- Trên R2:

![](.//media/image5.png)


![](.//media/image6.png)


![](.//media/image7.png)


\- Trên R3:

![](.//media/image8.png)


![](.//media/image9.png)


![](.//media/image10.png)


\- Trên R4:

![](.//media/image11.png)


![](.//media/image12.png)


\- Trên R5:

![](.//media/image13.png)


![](.//media/image14.png)


# DMVPN Phase 3 without IPSec

> **a. Mục tiêu Lab**
>
> \- Bài Lab tập trung để hiểu việc triển khai và cấu hình DMVPN trong
> bộ định tuyến Cisco IOS. Các công nghệ bổ sung được thử nghiệm bao gồm
> DMVPN không có IPSec.
>
> **b. Mô hình Lab**
>
> \- Mô hình mạng sau:
>
> ![](.//media/image15.png)
> 
>
> **Câu hỏi:**
>
> \- Tạo một mạng DMVPN giữa R1 - R5 theo các yêu cầu sau:

-   R1 - R4 là các DMVPN Spoke

-   R5 là DMVPN Hub, và NHRP Next-Hop Server (NHS)

-   Tạo cổng Tunnel0 như một multipoint GRE tunnel

-   Nguồn của tunnel từ cổng Ethernet0/0 của các router

-   Sử dụng địa chỉ IP với định dạng 155.1.0.Y/24, trong đó Y là số của
    router

-   Sử dụng 1 là ID mạng NHRP

-   Sử dụng NHRPAUTH là chuỗi xác thực NHRP

-   Sử dụng 2 là GRE tunnel key

-   Đảm bảo các spoke có thể gửi gói tin multicast đến hub, và ngược lại

\- Cấu hình IGP routing thông qua DMVPN tunnel theo các yêu cầu sau:

-   Kích hoạt RIPv2 trên DMVPN tunnel của R1 - R5

-   Tất cả đường dẫn nên là cổng passive ngoại trừ DMVPN tunnel

-   Quảng bá các mạng Loopback0 của các router trong RIP

-   Cấu hình R5 quảng bá định tuyến mặc định qua RIPv2 đến các DMVPN
    spoke

\- Khi hoàn thành, đảm bảo R1 - R5 có thể đi đến các mạng Loopback0 của
nhau thông qua mạng DMVPN.

**Cấu hình:**

\- Trên R1:

![](.//media/image16.png)


\- Trên R2:

![](.//media/image17.png)


\- Trên R3:

![](.//media/image18.png)


\- Trên R4:

![](.//media/image19.png)


\- Trên R5:

> ![](.//media/image20.png)
> 
>
> Lưu ý rằng mặc dù DMVPN là một đường hầm đa điểm, nhưng nó không phải
> là một đường hầm đa hướng. Điều này có nghĩa là địa chỉ IP nguồn GRE
> và địa chỉ IP đích GRE luôn đồng nhất với nhau. Tuy nhiên, Multicast
> được hỗ trợ bên trong đường hầm, nhưng về cơ bản là một unicast được
> sao chép, tương tự như cách multicast được hỗ trợ qua Frame Relay hoặc
> ATM PVC kế thừa. Hỗ trợ Multicast được thêm vào DMVPN bằng cách các
> spoke ánh xạ thủ công multicast tới địa chỉ NBMA của hub bằng lệnh ip
> nhrp map multicast, trong khi hub ánh xạ multicast dưới dạng động.
> Điều này tương tự với từ khóa broadcast ở cuối câu lệnh Frame Relay
> hoặc ATM.

# DMVPN Phase 1 with Static Mapping

**a. Mục tiêu Lab**

> \- Bài Lab tập trung để hiểu việc triển khai và cấu hình DMVPN trong
> bộ định tuyến Cisco IOS. Các công nghệ bổ sung được thử nghiệm bao gồm
> DMVPN - Phase 1 với Static Mapping.
>
> **b. Mô hình Lab**
>
> \- Mô hình mạng sau:
>
> ![](.//media/image21.png)
> 

**Câu hỏi:**

\- Cloud đại diện cho Internet, các router này phải ping và đến được các
cổng E0/0 của tất cả router trong mô hình này.

> \- Cấu hình DMVPN Phase 1 với: R1 là HUB, R2-3-4 là các Spoke. Sử dụng
> 10.1.1.x/24, trong đó x là số của router. Nếu cấu hình chính xác, tất
> cả các router này có thể đi đến tất cả tunnel ở điểm cuối. Ta nên cấu
> hình static mapping với Lab này.
>
> **Cấu hình:**

DMVPN:

\- DMVPN là sự kết hợp của mGRE và NHRP (Giao thức phân giải Next Hop)
và IPSec (Tùy chọn). DMVPN có thể được thực hiện ở Giai đoạn 1, Giai
đoạn 2 hoặc Giai đoạn 3.

\- Có hai loại GRE:

-   GRE

-   mGRE

\- GRE là một liên kết logic điểm-điểm được định cấu hình với nguồn
Tunnel, đích Tunnel và đóng gói Tunnel. Khi đích đến của Tunnel được
định cấu hình, nó liên kết Đường hầm với một điểm cuối cụ thể, điều này
làm cho các đường hầm này trở thành đường hầm điểm-điểm, điều này có
nghĩa là nếu có 200 điểm cuối, mỗi điểm cuối cần phải định cấu hình 199
Đường hầm GRE.

\- Với mGRE (Đóng gói định tuyến chung đa điểm), cấu hình bao gồm nguồn
đường hầm và chế độ đường hầm, đích của đường hầm không được định cấu
hình. Do đó, đường hầm có thể có bất kỳ hoặc nhiều điểm cuối và chỉ một
giao diện đường hầm duy nhất được sử dụng. Các điểm cuối có thể được
định cấu hình là GRE hoặc mGRE.

\- Nhưng điều gì sẽ xảy ra nếu các spoke giao tiếp với nhau, đặc biệt là
với bản chất NBMA của mGRE? Làm thế nào chúng ta sẽ thực hiện được điều
đó? Trong một hub và Frame-Relay đã nói, nếu một spoke cần giao tiếp với
một spoke khác, thì cần phải cấu hình ánh xạ Frame-Relay, có ánh xạ nào
mà chúng ta cần cấu hình trong mGRE không?

\- mGRE không có khả năng đó và đây là lý do tại sao một giao thức khác
được kết hợp, nó được gọi là NHRP (Next Hop Resolution Protocol).

Hãy cấu hình R1 (Router trung tâm) với Static Mapping:

\- Cấu hình đường hầm, cho dù tĩnh hay động, có thể được chia thành hai
giai đoạn cấu hình; trong giai đoạn đầu, cấu hình mGRE đã hoàn tất, điều
này bao gồm ba lệnh: địa chỉ IP của đường hầm, nguồn đường dẫn và chế độ
đường hầm.

Trên R1:

![](.//media/image22.png)


\- Trong giai đoạn thứ hai của cấu hình, NHRP được cấu hình, cấu hình
này bao gồm ba lệnh NHRP: ID mạng NHRP cho phép NHRP trên giao diện
đường hầm đó, ánh xạ NHRP ánh xạ địa chỉ IP đường hầm của các spoke tới
IP vật lý (NBMA-IP) địa chỉ các các spoke, điều này cần được thực hiện
cho mỗi spoke và cấu hình tùy chọn của ánh xạ NHRP của đa hướng tới địa
chỉ IP vật lý của các spoke cho phép đa hướng và cho phép các IGP sử
dụng đa hướng qua giao diện đường hầm. Trong tác vụ này, ánh xạ
Multicast tới NBMA-IP không được cấu hình vì tác vụ không yêu cầu nó.

![](.//media/image23.png)


Để xác thực cấu hình:

![](.//media/image24.png)


Trên R2:

\- Vì trong cấu hình DMVPN Phase 1, các spoke router phải được cấu hình
là điểm-điểm, cấu hình bao gồm nguồn đường hầm và đích đường hầm, và vì
đích đường hầm được cấu hình, nó chỉ liên kết đường hầm đó với đích đó,
điều này làm cho đường hầm là đường hầm điểm-điểm và không phải đường
hầm đa điểm. Sau khi các lệnh đường hầm được cấu hình, bước tiếp theo
hoặc bước cuối cùng là cấu hình NHRP. Trong cấu hình này, NHRP được bật
trước tiên và sau đó một ánh xạ duy nhất được định cấu hình cho địa chỉ
IP đường hầm trung tâm.

![](.//media/image25.png)


Để xác thực cấu hình:

![](.//media/image26.png)


Trên R3:

![](.//media/image27.png)


Trên R4:

![](.//media/image28.png)


# Vận hành giám sát hoạt động của PNETLab (Zabbix)

> ![](.//media/image29.png)
> 
>
> Bước 1: Cài đặt Zabbix repository
>
> \- Ở bước này bạn copy các lệnh sau để cài đặt:
>
> wget
> https://repo.zabbix.com/zabbix/5.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.4-1+ubuntu20.04_all.deb
>
> dpkg -i zabbix-release_5.4-1+ubuntu20.04_all.deb
>
> apt update
>
> ![](.//media/image30.png)
>
> ![](.//media/image31.png)
> 
>
> ![](.//media/image32.png)
> 
>
> Bước 2: Cài đặt Zabbix server, frontend, agent
>
> \- Sau đó bạn hãy cài đặt một số dịch vụ cần thiết như là
> zabbix-server-mysql, zabbix-frontend-php,\...
>
> apt install zabbix-server-mysql zabbix-frontend-php zabbix-nginx-conf
> zabbix-sql-scripts zabbix-agent
>
> Bước 3: Cài đặt và cấu hình máy chủ MySQL
>
> \- Để Zabbix hoạt động thì bắt buộc phải có một máy chủ cơ sở dữ liệu.
> Zabbix có hỗ trợ cả PostgreSQL. Ta sẽ dùng MySQL làm máy chủ cơ sở dữ
> liệu.
>
> \- Cài đặt MySQL:
>
> apt install mysql-server
>
> \- Khởi động MySQL:
>
> systemctl enable mysql
>
> systemctl restart mysql
>
> systemctl status mysql
>
> \- Cấu hình MySQL:
>
> mysql_secure_installation
>
> Bước 4: Tạo Database cho Zabbix
>
> \- Khi máy chủ MySQL đã sẵn sàng. Bạn hãy tạo một username và userdb
> như sau. Lưu ý hãy thay P\@ssw0rd bằng mật khẩu bạn đặt.
>
> \# mysql -uroot -p
>
> 1714168
>
> mysql> create database zabbix character set utf8 collate utf8_bin;
>
> mysql> create user zabbix\@localhost identified by \'P\@ssw0rd\';
>
> mysql> grant all privileges on zabbix.\* to zabbix\@localhost;
>
> mysql> quit;
>
> ![](.//media/image33.png)
> 
>
> Bước 5: Import Database
>
> \- Bạn hãy nhập lệnh bên dưới để nhập cơ sở dữ liệu vào database vừa
> tạo
>
> zcat /usr/share/doc/zabbix-sql-scripts/mysql/create.sql.gz \| mysql
> -uzabbix -p zabbix
>
> ![](.//media/image34.png)
> 
>
> Bước 6: Cấu hình Database vào Zabbix server
>
> \- Bạn hãy mở file /etc/zabbix/zabbix_server.conf, uncomment và sửa
> dòng DBPassword (với mật khẩu đã tạo ở bước 4)
>
> ![](.//media/image35.png)
> 
>
> Bước 7: Cấu hình PHP cho Zabbix frontend
>
> \- Bạn hãy mở file /etc/zabbix/nginx.còn sau đó uncomment dòng listen
> và server_name
>
> ![](.//media/image36.png)
> 
>
> Bước 8: Khởi động Zabbix server và agent
>
> systemctl restart zabbix-server zabbix-agent nginx php7.4-fpm
>
> systemctl enable zabbix-server zabbix-agent nginx php7.4-fpm
>
> Bước 9: Mở port firewall
>
> \- Bạn cần mở port firewall cho các dịch vụ
>
> \- Đối với Firewalld
>
> firewall-cmd \--add-service=http,https \--permanent
>
> firewall-cmd \--add-port=10051/tcp,10050/tcp \--permanent
>
> firewall-cmd \--reload
>
> Bước 10: Cấu hình Zabbix frontend
>
> \- Đầu tiên mình sẽ tạo một Virtual host cho admin. Để khi truy cập từ
> hostname cũng sẽ hoạt động. Mình sẽ sử dụng lệnh vi để soạn thảo. Và
> tạo file với tên zabbix.conf
>
> vi /etc/nginx/sites-available/zabbix.conf
>
> \- Sau đó copy tất cả các cấu hình sau dán vào file vừa tạo. Và lưu ý
> thay dòng server_name bằng tên hostname của bạn.
>
> server 
>
> listen 80;
>
> server_name **zabbix.lan**;
>
> #charset koi8-r;
>
> access_log /var/log/nginx/zabbix.domain.local.access.log;
>
> error_log /var/log/nginx/zabbix.domain.local.error.log;
>
> location / 
>
> root /usr/share/zabbix/;
>
> index index.php index.html index.htm;
>
> \# include the \"?\$args\" part so non-default permalinks doesn\'t
> break when using query string
>
> try_files \$uri \$uri/ /index.php?\$args;
>
> 
>
> location \~ \\.php\$ 
>
> root /usr/share/zabbix/;
>
> fastcgi_index index.php;
>
> \# With php-fpm (or other unix sockets):
>
> fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
>
> fastcgi_param SCRIPT_FILENAME \$document_root\$fastcgi_script_name;
>
> fastcgi_param SCRIPT_NAME \$fastcgi_script_name;
>
> include fastcgi_params;
>
> 
>
> 
>
> \- Tạo symlink
>
> ln -s /etc/nginx/sites-available/zabbix.conf /etc/nginx/sites-enabled/
>
> \- Khởi động lại dịch vụ nginx:
>
> systemctl restart nginx
>
> \- Sau đó truy cập vào http://server_ip_or_name để thiết lập ở giao
> diện.
>
> \- Giao diện thiết lập Zabbix, bạn hãy click Next step để thực hiện
> theo hướng dẫn trên màn hình.
>
> ![](.//media/image37.png)
> 
>
> \- Zabbix check một số yêu cầu, nếu hiện OK có nghĩa mọi thứ đã hoạt
> động bình thường.
>
> ![](.//media/image38.png)
> 
>
> \- Ở bước này bạn nhập vào Password User Zabbix đã tạo ở Bước 4.
>
> ![](.//media/image39.png)
> 
>
> \- Phần Name bạn có thể đặt tên bất kỳ
>
> ![](.//media/image40.png)
> 
>
> \- Phần time zone bạn hãy chọn múi giờ mà bạn sử dụng. Ở đây mình chọn
> múi giờ +7
>
> ![](.//media/image41.png)
> 
>
> \- Tiếp tục nhấn Next step
>
> ![](.//media/image42.png)
>
> ![](.//media/image43.png)
> 
>
> \- Ở khung đăng nhập, bạn hãy nhập vào thông tin mặc định của Zabbix
> là: Admin/zabbix
>
> ![](.//media/image44.png)
> 
>
> \- Khi đăng nhập thành công. Bạn sẽ thấy giao diện như sau:
>
> ![](.//media/image45.png)
> 
>
> **Tài liệu tham khảo**
>
> https://cuongquach.com/zabbix-la-gi-tim-hieu-he-thong-zabbix.html
>
> https://dotrungquan.info/huong-dan-cai-dat-zabbix-5-4-tren-ubuntu-20/
