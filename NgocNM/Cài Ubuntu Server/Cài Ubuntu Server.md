# Cách cài đặt Ubuntu 14.04 LTS server
----
**Bước 1:**  Tạo một máy ảo VMware mới 

<img src="./Picture/1.png"/>
-
<img src="./Picture/2.png"/>
-
<img src="./Picture/3.png"/>
-
<img src="./Picture/4.png"/>
-
<img src="./Picture/5.png"/>
-
<img src="./Picture/6.png"/>
-
<img src="./Picture/7.png"/>


- Sau khi ấn Finish, ta đã tạo thành công một máy ảo để cài đặt Ubuntu Server. Nó sẽ tự động Start và đưa chúng ta đến phần cài đặt.

**Bước 2:**  Cài đặt Ubuntu Server 14.04 và các thiết lập

*Chú ý: Để di chuyển giữa các phần khác nhau khi cài đặt, ta dùng phím TAB. Còn để lựa chọn một option, ta dùng phím SPACE*

- Các bước đầu chọn ngôn ngữ và bàn phím ta để như mặc định.

<img src="./Picture/8.png"/>
-
<img src="./Picture/9.png"/>
-
<img src="./Picture/10.png"/>
-
<img src="./Picture/11.png"/>
-
<img src="./Picture/12.png"/>
-
<img src="./Picture/13.png"/>

- Tiếp theo, đặt password đủ phức tạp và dài trên 8 kí tự

<img src="./Picture/14.png"/>
-
<img src="./Picture/15.png"/>
-
<img src="./Picture/16.png"/>
-
<img src="./Picture/17.png"/>
-
<img src="./Picture/18.png"/>
-
<img src="./Picture/19.png"/>
-
<img src="./Picture/20.png"/>

- Tiếp đến là phân vùng để cài đặt. Vì ở đây chúng ta dùng máy ảo nên thoải mái sử dụng toàn bộ phân vùng để cài đặt cho nhanh, nhưng nếu máy ai có dữ liệu thì nên dùng Gparted phân vùng kĩ càng, rồi Manual tạo phân vùng boot "/" và phân vùng swap trước khi cài đặt.

<img src="./Picture/21.png"/>
-
<img src="./Picture/22.png"/>
-
<img src="./Picture/23.png"/>
-
<img src="./Picture/25.png"/>
-
<img src="./Picture/26.png"/>

- Nếu không dùng Proxy thì phần này để trống.

<img src="./Picture/27.png"/>

- Tự động cài đặt các Update liên quan đến bảo mật.

<img src="./Picture/28.png"/>

- Cài Open-SSH để chút nữa ta sẽ SSH vào server. Cài Grub để hoàn thành việc cài đặt.

<img src="./Picture/29.png"/>
-
<img src="./Picture/30.png"/>
-
<img src="./Picture/31.png"/>

- Sau khi đã cài xong Ubuntu server, ta login bằng Username và Password đã tạo

<img src="./Picture/32.png"/>