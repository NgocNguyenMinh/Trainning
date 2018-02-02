# VMWare Workstation
----
## Mục lục
[1. Cài đặt VMWare, cách tạo máy ảo](#1)

[2. Các cơ chế hoạt động và mô hình cơ bản khi cấu hình với switch ảo (VMnet)](#2)

   - [2.1. Network mặc định khi mới cài đặt VMware](#2.1)

   - [2.2. Chế độ Bridge](#2.2)
   
   - [2.3. Chế độ Host-only](#2.3)

   - [2.4. Chế độ NAT](#2.4)

[3. Các thao tác với VMware](#3)

   - [3.1. Thêm, xóa một vmnet](#3.1)

   - [3.2. Sửa dải IP của một vmnet](#3.2)

   - [3.3. Cấu hình DHCP](#3.3)

   - [3.4. Thêm một card mạng vào máy ảo](#3.4)
----
<a name="1"></a>
# 1. Cài đặt VMWare, cách tạo máy ảo
VMWare Workstation là một phần mềm ảo hóa dùng cho desktop. Ta có thể dễ dàng download và cài đặt. [Link download](https://my.vmware.com/web/vmware/info?slug=desktop_end_user_computing%2Fvmware_workstation_pro%2F12_0)
----
Khi đã cài xong VMWare, để tạo một máy ảo Ubuntu, trước hết ta download file ubuntu-16.04.2-desktop-amd64  tại [đây](http://iso.linuxquestions.org/ubuntu/ubuntu-16.04.2/)

- Mở phần mềm VMWare -> Vào thư mục Home -> Click "Create a New Virtual Machine" để bắt đầu cài đặt máy ảo Ubuntu.
<img src="http://2.pik.vn/2018e9652843-79c1-4676-96ec-6f6bcc882a20.png">

<img src="http://2.pik.vn/2018042a6aa5-f151-427c-be8e-6cb47cfda648.png">

<img src="http://2.pik.vn/2018856d973e-3cf3-4436-b472-733e75002bac.png">

- Chọn file cài đặt, file "iso"
<img src="http://2.pik.vn/2018f17e7c75-0cf7-44e9-917f-403709de340d.png">

- Điền thông tin người sử dụng
<img src="http://2.pik.vn/2018dc598570-d57c-4f7e-b4f5-8732255b7af8.png">

- Điền tên máy ảo và chọn nơi cài đặt máy ảo
<img src="http://2.pik.vn/20186eff0a5a-e201-491e-a6bb-5c208396b8c9.png">

- Cài đặt máy ảo với 1 core xử lý và 1 GB RAM
<img src="http://2.pik.vn/2018a2de3703-3f82-4369-89a4-5b92f14570e7.png">

<img src="http://2.pik.vn/2018cab75da4-876b-467b-8d36-86f345e51c72.png">

<img src="http://2.pik.vn/2018fec041bb-24af-48b1-a4ef-c5a444a1bbff.png">

<img src="http://2.pik.vn/2018b1d12786-c420-49d6-9f4d-12cf08fe8739.png">

<img src="http://2.pik.vn/20187fecf347-a4ff-4182-b5ca-a879c45adde1.png">

<img src="http://2.pik.vn/2018b9ce6f5f-8969-496f-b949-094e2c1dfc25.png">

<img src="http://2.pik.vn/20189bab89bb-2d22-45dc-8281-d8756b94466a.png">

<img src="http://2.pik.vn/2018578f5c24-b3d1-4089-9740-ccc89d99f8ca.png">

<img src="http://2.pik.vn/20181c99ee44-ac84-49b0-9a8d-a0587498d4b4.png">

- Máy ảo Ubuntu đã cài xong, kết quả sẽ hiện lên màn hình
<img src="http://2.pik.vn/20185b7d4662-d635-45b2-8642-5a64728f1a6f.png">

<img src="http://2.pik.vn/2018929e9341-9ba9-4277-b429-30499cf279c6.png">

<a name="2"></a>
# 2. Các cơ chế hoạt động và mô hình cơ bản khi cấu hình với Switch ảo (VMnet) 

<a name="2.1"></a>
## 2.1. Network mặc định khi mới cài VMware

Mỗi VMnet như là một Switch ảo mà VMware tạo ra, việc gán 1 card mạng của máy ảo vào một VMnet giống như việc cầm 1 dây mạng, 1 đầu cắm vào card của máy ảo đó và 1 đầu cắm vào "Switch ảo" có tên VMnet tương ứng

Khi mới cài đặt VMWare, mặc định trong phần Network của máy thật sẽ tạo ra 2 Adapter mạng là VMnet0 và VMnet8, tương đương với việc từ máy thật hiện tại đã được cắm "dây mạng" với 2 "Switch ảo" VMnet0 và VMnet8 => chỉ cần đặt địa chỉ IP cho 2 card mạng này của máy thật cùng dải IP với các máy ảo cũng nối vào 2 "Switch ảo" này thì máy thật và máy ảo có thể kết nối với nhau thông qua một trong 2 card mạng này.

- Card Bridge (VMnet0): Card này sử dụng chính card mạng thật của máy để kết nối ra ngoài Internet (card Ethernet hoặc Wireless). Do đó khi sử dụng card mạng này, IP của máy ảo sẽ cùng với dải IP của máy thật.
- Card NAT (VMnet8): Card này có thể kết nối ra bên ngoài Internet. NAT cho phép một máy ảo truy cập mạng sử dụng địa chỉ IP cùng dải với địa chỉ IP của máy thật.

Để xem các card mạng đã có trong VMWare, ta bật WmWare lên, chọn "Edit" -> "Virtual Network Editor"

<img src="http://2.pik.vn/20184db9426f-58de-4cc2-be65-4e627715297b.png">

Nhận thấy, Card Bridge không có địa chỉ IP, nó sẽ sử dụng dải IP của máy thật. VMWare sẽ tự sinh một dải IP và gán cho VMnet8, trong trường hợp này là 192.168.75.0/24

<a name="2.2"></a>
## 2.2. Chế độ Bridge

Ở chế độ này, card mạng trên máy ảo được gắn vào VMnet0, VMnet0 này liên kết trực tiếp với card mạng vật lý trên máy thật. Máy ảo lúc này sẽ kết nối Internet thông qua card mạng vật lý và có chung lớp mạng (dải IP) với card mạng vật lý.

<img src="http://2.pik.vn/2018d4b259d6-089b-476b-8523-aa62fb5b4470.png">

<a name="2.3"></a>
## 2.3. Chế độ Host-only

Card mạng máy ảo được kết nối với VMnet có tính năng Host-only (VMnet1). Ở chế độ này, các máy ảo không thể kết nối vào mạng vật lý bên ngoài hay Internet thông qua máy thật. IP của máy ảo được cấp bởi DHCP server của VMnet tương ứng (các thiết bị kết nối đến VMnet này sẽ nhận được địa chỉ do DHCP server cấp phát)
-> Như vậy, các máy ảo ở chế độ Host-only có cùng dải IP sẽ kết nối được với nhau nhưng không thể kết nối ra các thiết bị vật lý khác cũng như ra ngoài Internet **bởi nó không được kết nối với card vật lý của máy thật**.

<img src="http://2.pik.vn/2018f7ac7c8f-c345-4ee5-a831-a4a2273a536d.png">

<a name="2.4"></a>
## 2.4. Chế độ NAT (Network address translation)

Card mạng máy ảo kết nối với VMnet8, VMnet8 cho phép máy ảo đi ra mạng vật lý bên ngoài internet thông qua cơ chế NAT. Lúc này lớp mạng bên trong máy ảo khác hoàn toàn với lớp mạng của card vật lý bên ngoài máy thật. IP của card mạng máy ảo sẽ được cấp bởi DHCP server của VMnet8, IP này sẽ qua NAT device và kết nối ra ngoài Internet.
-> Như vậy, Một máy ảo sử dụng địa chỉ IP do DHCP server cấp qua NAT device thành IP có cùng dải với IP máy thật từ đó có thể truy cập ra ngoài Internet.

<img src="http://2.pik.vn/2018198c54ac-a327-4161-ae50-99d9ed4feebb.png">

<a name="3"></a>
# 3. Các thao tác với VMware

<a name="3.1"></a>
## 3.1. Thêm, xóa một vmnet
### Thêm một Vmnet

Click "Virtual Network Editor" chọn:

<img src="http://2.pik.vn/20181089d8cd-54bc-4e03-be2c-c87da3b4fb02.png">

- Bước 1: Chọn Add Network
- Bước 2: Chọn card cần add thêm (VMnet2)
- Bước 3: Click Ok

Lúc này trên cửa sổ Virtual Network Editor sẽ xuất hiện thêm card VMnet2 và được gắn tự động một dải IP như sau:
<img src="http://2.pik.vn/2018ef454020-bf9a-49ae-802e-50b20e276d06.png">

Làm tương tự để add thêm các VMnet khác.

### Xóa một Vmnet
Click "Virtual Network Editor" chọn một vmnet -> Click "Remove Network"

<img src="http://2.pik.vn/2018d6414c26-54cf-413f-a857-7a8bb0061968.png">

<a name="3.2"></a>
## 3.2. Sửa dải IP của một vmnet
Các dải IP mà VMWare tự sinh ra và gắn cho card mạng rất khó nhớ. Ta có thể đổi dải IP này như sau:
Chọn VMnet muốn đổi địa chỉ. Trong dòng Subnet IP chọn dải IP và subnet muốn thay đổi -> Click "Apply và OK"

<img src="http://2.pik.vn/20185464f4f7-800f-48fa-92b6-8d3684fbf7d2.png">

<a name="3.3"></a>
## 3.3. Cấu hình DHCP
Các card mạng này có thể cấp DHCP cho các máy ảo sử dụng nó.
Chọn DHCP Settings -> Chọn dải IP dùng để cấp DHCP

<img src="http://2.pik.vn/2018fc00501c-7b74-4f5c-96de-da741ec4f1fb.png">

<a name="3.4"></a>
## 3.4. Thêm một card mạng vào máy ảo
Show ip trên máy ảo Ubuntu:
<img src="http://2.pik.vn/201879a8b951-e9ea-4ec2-a20a-d9c64a09ee22.png">
 Thấy có sẵn card bridge. Thêm card mạng thứ 2 vào máy ảo bằng cách: Edit Virtual Machine Settings -> Add -> Network
 <img src="http://2.pik.vn/2018953eb90d-2561-4880-9d2e-54121dc66b8c.png">

 <img src="http://2.pik.vn/2018bd500280-54aa-4042-8268-90367e714c4b.png">

 <img src="http://2.pik.vn/201825f6396c-e3a5-466a-8d88-1a1072fbe732.png">

 <img src="http://2.pik.vn/20181a3fedc4-3192-4217-a727-f6bc7540be13.png">




