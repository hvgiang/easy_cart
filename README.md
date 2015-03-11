Welcome to Easy Cart CMS
=======================

[TOC]


## Giới thiệu

Đây là một ứng dụng sẽ giúp bạn tạo lập nhanh một shop bán hàng online cho bản thân mà không cần phải biết về ngôn ngữ lập trình hay kiến thức về SQL. Được xây dựng trên nền tảng Zend 2.

## Cách cài đặt

À cái này thì chưa biết

## Cài đặt cho developers

Nếu bạn nào đã biết sử dụng `git` thì không cần phải nhắc lại nữa
Còn nếu bạn vẫn chưa biết tới em nó thì có thể tham khảo tại
[http://git-scm.com](http://git-scm.com) hoặc vào [http://git-scm.com/downloads](http://git-scm.com/downloads) để tải em nó về. Cách cài đặt thì giống hệt với cách cài các phần mềm khác. Nếu không biết cài thì các bạn vui lòng nhờ bạn bè hoặc người yêu (người thường xuyên bạn bắt cài windows hoặc IDM) cài giúp.

Sau khi đã cài đặt được `GIT-SCM` thì các bạn bật GIT BASH ( nếu không biết thì vui lòng nhờ người cài giúp bật hộ).
Các bạn nhập lệnh

```
git clone https://github.com/phpgang/easy_cart.git <duong_dan_thu_muc>
```
Nếu bạn không nhập đường dẫn thư mục thì git sẽ tự động tạo một thư mục là easy_cart vào thư mục bạn đang đứng.
Nếu muốn clone luôn vào thư mục hiện tại (không tạo thư mục con) thì các bạn dí dấu chấm (.) vào chỗ đường dẫn thư mục nhé.

Trong lúc clone git sẽ yêu cầu bạn nhập tài khoản github vào thì các bạn vui lòng xuất trình đầy đủ.

Rồi Done.

### Kéo Zend Framework

Sau khi clone xong thì các bạn di chuyển vào thư mục vừa clone về gõ tiếp
```
php composer.phar install
```

Composer sẽ kéo thư viện ZF2 vào cho bạn.


### Cài đặt VitualHost cho Apache
-----------------------------

Cách này dùng cho bạn nào sử dụng Xampp, còn AppServer, WampServer thì các bạn cũng làm tương tự nhé.
vào trong thư mục cài đặt XAMPP `xampp/apache/conf/extra`
thêm đoạn dưới vào file `httpd-vhosts.conf` trong đó:

* `/path/to/zf2-tutorial/public` là đường dẫn tới thư mục public của thư mục bạn vừa clone về ví dụ bạn clone vào `D:/repos/easy_cart` thì đường dẫn của bạn sẽ là `D:/repos/easy_cart/public`.
* domain_name chính là domain mà bạn sẽ dùng để truy cập vào site này. Bạn đặt là gì cũng được kể cả là google.com.vn


```

# Cái này hình như dành cho apache 2.2 thì phải
<VirtualHost *:80>
    ServerName domain_name
    DocumentRoot /path/to/zf2-tutorial/public
    SetEnv APPLICATION_ENV "development"
    <Directory /path/to/zf2-tutorial/public>
        DirectoryIndex index.php
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

# Còn nếu bạn nào dùng Apache 2.4
<VirtualHost *:80>
	ServerAdmin webmaster@facebook-dev.vn
    DocumentRoot "/path/to/zf2-tutorial/public"
    ServerName domain_name
    ErrorLog "logs/easy-cart.local-error.log"
    CustomLog "logs/easy-cart.local-access.log" common
	<Directory "/path/to/zf2-tutorial/public">
		Options FollowSymLinks
		AllowOverride All
        DirectoryIndex index.php
        Require all granted
    </Directory>
</VirtualHost>
```

Bạn khởi động lại apache là xong phần cấu hình cho apache rồi.

Giờ bạn vào dùng tổ hợp phím WINDOWS + R ( để mở hộp thoại run - ai biết cách khác cũng được miễn là mở được run lên)
Gõ vào đó  là:

```
%windir%/system32/drivers/etc/hosts
```
bạn thêm dòng này vào cuối
```
# 127.gì.gì.gì cũng được. Vì đầu 127 là trỏ vào chính máy đó. nên bạn đặt là gì cũng được miễn là số không âm và nhỏ hơn 255
# 
# domain_name là cái domain bạn cấu hình trong apache. nếu bạn đặt là google.com.vn bạn gõ google.com.vn vào đó. Nhưng bạn không còn tra cứu thông tin từ google được nữa nhé.
127.0.0.1 domain_name 
```

Giờ bạn vào trình duyệt gõ http://domain_name và cảm nhận.

À hơi xấu 1 tý. Nhưng chạy được rồi.

### Kéo thư viện JS và CSS

Giò thì bạn cài NodeJs lên nếu chưa có thì vào [http://nodejs.org/](http://nodejs.org) để tải về
Xong thì gõ:
```
npm install -g bower
```

Di chuyển vào trong thư mục `public` của repo và gõ:

```
bower install
```

Rồi refesh lại trình duyệt. Đỡ xấu hơn rồi :).
