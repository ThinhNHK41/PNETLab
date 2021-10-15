# I. Tổng quan
## 1. PNETLab
PNETLab (Packet Network Emulator Tool Lab) là một nền tảng cho phép người dùng chia sẻ và tải xuống những bài lab của cộng đồng.
Bao gồm PNETLab Box và PNETLab store:
-	PNETLab Box ( có 2 modes: Offline và Online ) : Là một thiết bị ảo được cài đặt tại máy và các bài Lab sẽ được chạy trên nó.
-	PNETLab Store : là một nền tảng web cùng với rất nhiều bài Lab miễn phí ở nhiều hạng mục khác nhau như networking, database, system, … 

## 2. Những phần mềm và nền tảng ảo hỗ trợ
- VMware Workstation 12.5 or later.
-	VMware Player 12.5 or later.
-	VMware ESXi 6.0 or later.
-	Ubuntu Server 16.04 LTS as platform for bare metal (roadmap).
-	Google Cloud Platform.

## 3. Phần cứng và hệ thống không hỗ trợ
-	AMD CPU based PC or Server.
-	VirtualBox virtualization.
-	Citrix XenServer.
-	Microsoft HyperV.
-	Ubuntu 17.X or 18.x as platform.

## 4. Một số đặc điểm
-	Có phiên bản Offline
-	Miễn phí
-	Hỗ trợ Lab Store, Device Soter, …
-	Hỗ trợ nhiều hệ điều hành (Cisco, Juniper, Arista,…)
-	Quyền người dùng
-	Các đặc điểm hỗ trợ làm Lab (Task, Timer,…)
-	Không giới hạn số Node ở mỗi Lab
-	3D Model
-	Có thể quản lý lượng RAM, CPU, HDD sử dụng cho từng thiết bị
-	Cấu hình Proxy
-	Icon đẹp, có thể tùy chỉnh
-	Hỗ trợ Wireshark Capture, Telnet, Hot connections, NAT cloud,…

# II. Cơ chế hệ thống của PNETLab
1. Hệ thống <br>
  Gồm 2 mode: Offline Mode và Online Mode
  ![image](https://user-images.githubusercontent.com/92511177/137289589-a35358e1-f63c-48b5-8289-4f9d69377b87.png)<br>
Online Mode:
-	Cần Internet để làm việc.
-	Cần phải đăng ký.
-	Hỗ trợ tất cả các hàm số của PNETLab.
-	Có thể tải xuống và sử dụng tất cả bài Lab trên hệ thống cửa hàng.
-	Có thể chia sẻ hoặc bán các bài Lab trên cửa hàng.
-	Giới hạn 10 tài khoản ( Có thể nâng cấp ) <br><br>
Offline Mode:
-	Không cần Internet để làm việc.
-	Không cần đăng ký. Đăng nhập bằng tài khoản mặc định (admin/pnet)
-	Hỗ trợ tất cả các hàm số của PNETLab.
-	Chỉ có thể tải và sử dụng Open Labs trên cửa hàng.
-	Không thể chia sẻ hoặc bán các bài lab trên cửa hàng.
-	Giới hạn 10 tài khoản ( Có thể nâng cấp nhưng cần Internet)
<br>
-	Khi nhấn vào Online Mode : Online Mode sẽ được kích hoạt và Offline Mode sẽ bị vô hiệu. Chế độ mặc định sẽ được chuyển thành Online.
<br>
-	Khi nhấn vào Offline Mode : Offline Mode sẽ được kích hoạt và Online Mode sẽ bị vô hiệu. Chế độ mặc định sẽ được chuyển thành Offline. Tài khoản mặc định sẽ là : admin/pnet.

![image](https://user-images.githubusercontent.com/92511177/137291596-e142e5e3-5f02-4b6b-a012-4faacd462597.png)
<br>
Để quản lý System Mode: **System -> System Mode**

![image](https://user-images.githubusercontent.com/92511177/137291703-38d9b473-8750-4f7d-bd75-26299ddca838.png)

-	Người dùng có thể tùy chỉnh chế độ đăng nhập mặc định, vô hiệu hoặc kích hoạt các chế độ.
<br> Hệ thống cũng hỗ trợ chuyển chế độ bằng câu lệnh:
-	Để thay đổi chế độ mặc định sử dụng câu lệnh : mode default online hoặc mode default offline.
-	Để cài lại mật khẩu offline sử dụng câu lệnh : mode reset offline.
-	Để cài lại chế độ của hệ thống sang nguyên bản sử dụng câu lệnh : mode reset all.

2. Quản lý tài khoản Offline

Tạo Role và tài khoản người dùng tại : Accounts
-	Có thể tạo tối đa 10 tài khoản.
-	Tài khoản Offline sẽ có tag    và tài khoản Online sẽ có tag 🌍. Bạn không thể tùy chỉnh tài khoản Online
-	Để thêm tài khoản nhấn vào nút Add ➕
-	Cần ít nhất là username, password và role
-	Có thể đặt thời gian kích hoạt hoặc hết hạn cho từng tài khoản.

![image](https://user-images.githubusercontent.com/92511177/137292405-661c6934-c1fa-44ed-9f5a-c41fa30ac6f1.png)

![image](https://user-images.githubusercontent.com/92511177/137292389-404a702b-94b2-4792-8efc-bba6667f523c.png)

3. Quản lý tài khoản Online
Cũng như tài khoản Offline, để tạo tài khoản Online và Role : Accounts

![image](https://user-images.githubusercontent.com/92511177/137292594-d558420b-056c-448c-bf1a-1ed6701e4bfb.png)
-	Có thể tạo tối đa 10 tài khoản.
-	Tài khoản Offline sẽ có tag    và tài khoản Online sẽ có tag 🌍. Bạn không thể tùy chỉnh tài khoản Online
-	Để thêm tài khoản nhấn vào nút Add ➕
-	Cần email, và role.
-	Có thể đặt thời gian kích hoạt hoặc hết hạn cho từng tài khoản.

# III. Hướng dẫn cài đặt và cấu hình
Sau khi tải về file OVA của Pnetlab ta tiến hành cài đặt trên VMWare
1.	Open file OVA trên VMWare

![image](https://user-images.githubusercontent.com/92511177/137292980-42b88591-be91-4736-9922-db4334215359.png)

![image](https://user-images.githubusercontent.com/92511177/137292959-738939b1-0007-4862-9acc-fea067e435b6.png)

2.	Sau khi mở file OVA ta vào mục Edit lại một vài thông số

![image](https://user-images.githubusercontent.com/92511177/137293053-c2ee5b40-0b79-46f1-9bba-486100b4ad99.png)

Tùy vào lượng RAM mà chọn cấu hình RAM phù hợp

![image](https://user-images.githubusercontent.com/92511177/137293081-b5e14834-115d-4a33-9d4a-0a586f89d109.png)

Mục Processcors check vào Mục Virtulize Intel VT-x…

![image](https://user-images.githubusercontent.com/92511177/137293116-ebb93a51-3a09-4c85-8d59-1232e72232ec.png)

Mục Network Adapter chọn NAT

![image](https://user-images.githubusercontent.com/92511177/137293142-0df1ad71-a87c-403f-a141-bb0c4d1606bb.png)

Sau khi hoàn tất -> OK và Start máy ảo lên

![image](https://user-images.githubusercontent.com/92511177/137293192-59e252be-9022-42ce-9a24-31d31f07aaef.png)

Đăng nhập với tài khoản mặc định là root/pnet

![image](https://user-images.githubusercontent.com/92511177/137293239-77dca6a5-2604-4e11-8e7e-fb4fad936f39.png)

Nhập mật khẩu cho tài khoản root

![image](https://user-images.githubusercontent.com/92511177/137293298-e8752cc3-ae17-496f-bc26-e73d155279c1.png)

![image](https://user-images.githubusercontent.com/92511177/137293312-22e05c54-0bfe-44a5-8cdd-68bee049be5e.png)

Đặt tên máy ảo

![image](https://user-images.githubusercontent.com/92511177/137293338-ce2fb0d2-024c-4739-8c04-7912a01941ea.png)

Cấu hình DNS domain name

![image](https://user-images.githubusercontent.com/92511177/137293366-d71d84eb-a66c-40bc-8798-36e5c6e7b61f.png)

Cấu hình địa chỉ ip của PNETLab, có thể để DHCP hoặc Static

![image](https://user-images.githubusercontent.com/92511177/137293410-7c1a785f-f7e3-4d32-b9fc-085e68e34efb.png)

Cấu hình máy chủ đồng bộ thời gian cho PNETLab

![image](https://user-images.githubusercontent.com/92511177/137293458-e2a5be24-2d03-48a7-8f1e-93d2b69b2e8e.png)

Cấu hình Proxy cho PNETLab

![image](https://user-images.githubusercontent.com/92511177/137293493-a5372448-5240-4fbd-b831-6200edc366e8.png)

Sau khi cấu hình xong các tùy chọn thì PNETLab sẽ khởi động lại
Màn hình đăng nhập sau khi PNETLab khởi động lại

![image](https://user-images.githubusercontent.com/92511177/137293531-fbe5ce60-4cbf-4a02-8b2f-28dfc2114be3.png)

3.	Ta cần đăng nhập vào và SSH đến địa chỉ của PNETLab

![image](https://user-images.githubusercontent.com/92511177/137293656-69b09cef-83e5-4c98-9ab5-068bf785e5aa.png)

![image](https://user-images.githubusercontent.com/92511177/137293685-3c994d4b-be12-4b4d-98b4-36015f659714.png)

4.	Sau khi đăng nhập thành công ta tiến hành cập nhật và nâng cấp các gói tin theo các lệnh sau:

![image](https://user-images.githubusercontent.com/92511177/137293737-f68f05f3-73d9-4983-bcdc-769a5ec8c462.png)

![image](https://user-images.githubusercontent.com/92511177/137293751-37b33454-e83e-4274-874b-64fd2fe86398.png)

Chọn Y để đồng ý

![image](https://user-images.githubusercontent.com/92511177/137293780-a2f4d6f7-be8b-4d64-82e1-fe9c4598305d.png)

5.	Sau khi cập nhật xong ta vào trình duyệt web nhập địa chỉ IP của PNETLab sau đó đăng ký tài khoản

![image](https://user-images.githubusercontent.com/92511177/137293830-cafe5e82-3fe6-43b7-ac7a-c26f34dbe220.png)

![image](https://user-images.githubusercontent.com/92511177/137293855-0c239161-12b6-400e-8075-43d81315dd59.png)

6.	Sau đó bạn download các Image Cisco IOL cho PNETLab

![image](https://user-images.githubusercontent.com/92511177/137293905-2e8d8255-66fa-4540-938f-5364809874f3.png)

Ta sử dụng WinSCP để upload các file Image vào đường dẫn /opt/unetlab/addons/iol/bin/

![image](https://user-images.githubusercontent.com/92511177/137293965-2c924577-e5fe-4384-a1e5-c0069e1bb063.png)

Mục bên trái là đường dẫn các Image cần thêm vào PNETLab, bên phải là đượn dẫn đến thư mục /opt/unetlab/addons/iol/bin/ chứa các Image để sử dụng cho PNETLab

![image](https://user-images.githubusercontent.com/92511177/137294009-539c3225-d6ce-40f1-9844-1d4c6e83f74a.png)

Ta chọn các Image cần thêm và chọn Upload

![image](https://user-images.githubusercontent.com/92511177/137294048-894b88e8-4a31-44cd-b029-29061a3e2855.png)

Sau khi Upload xong ta vào SSH sử dụng lần lượt các lệnh sau để xác thực:
Chuyển đến thư mục sau

![image](https://user-images.githubusercontent.com/92511177/137294120-139afaef-8f87-474c-9e7f-2592b1a18540.png)

Thêm quyền execute cho file CiscoIOUKeygen.py và tạo key cho IOU:

![image](https://user-images.githubusercontent.com/92511177/137294157-4db77306-0d01-4b02-904b-99f68f851ae3.png)

Fix lại phân quyền:

![image](https://user-images.githubusercontent.com/92511177/137294189-22a68170-00a2-42ec-8c71-4f2cfbba12f4.png)
Sau đó truy cập vào địa chi PNETLab và tiến hành làm LAB

7.	Sau khi ta truy cập vào địa chỉ PNETLab và đăng nhập tài khoản đã tạo ở trên

![image](https://user-images.githubusercontent.com/92511177/137294250-99e14c59-1a61-4c10-9587-1c139aae9f25.png)
Ta có thể tự tạo bài lab cho chính mình (có thể tìm kiếm thêm các Image thiết bị để thêm vào PNETLab) hoặc có thể vào mục Download Labs để tải về và làm các bài Lab của cộng đồng.

![image](https://user-images.githubusercontent.com/92511177/137294292-e0d4ded1-b3ea-4454-b2c2-d980e91f556b.png)

Sau khi bạn Open Lab đầu tiên bạn nên mở chế độ HTML Console ở thanh bên trái màn hình để có thể cấu hình được thiết bị:

![image](https://user-images.githubusercontent.com/92511177/137294323-06bdae74-0f71-43c1-8eaf-c9a8cc6be637.png)
Nếu như bạn không thể chạy được các thiết bị và ấn vào Edit thiết bị thì bị lỗi không tìm thấy Image như sau:

![image](https://user-images.githubusercontent.com/92511177/137294356-e079695a-189c-4eb2-90e7-a3c23635be22.png)

Lúc đó bạn có thể lên mạng tìm file và thêm vào PNETLab thông qua WinSCP như trên hoặc dùng lệnh sau trên SSH để có thể thêm file:

![image](https://user-images.githubusercontent.com/92511177/137294399-9d1bb983-8d32-4049-9fc9-55b1074ed0cd.png)

Sau đó Reload lại trang Web là được. Hoặc vẫn không được thì xóa Lab đi tải lại là được.
Nếu vẫn gặp tình trạng lỗi thì bạn cần khởi động lại Pnetlab sau đó cấp quyền theo các lệnh sau:
> cd /opt/unetlab/addons/iol/bin/
> chmod +x CiscoIOUKeygen.py
>python CiscoIOUKeygen.py
>/opt/unetlab/wrappers/unl_wrapper -a fixpermissions
Sau đó khởi động lab là được.

# IV. Tài liệu tham khảo
https://pnetlab.com/pages/main
<br>
https://ictsaigon.vn/huong-dan-cai-dat-eve-ng/#:~:text=%C4%90%E1%BA%A7u%20ti%C3%AAn%20ta%20gi%E1%BB%9Bi%20thi%E1%BB%87u,%E1%BA%A3o%20t%C3%A1ch%20bi%E1%BB%87t%20b%C3%AAn%20trong.
<br>
https://nguyenvanlong.blog/quan-tri-mang/cong-cu/tong-hop-hon-100gb-tai-nguyen-lab-cho-eve-ng-va-cach-su-dung/















