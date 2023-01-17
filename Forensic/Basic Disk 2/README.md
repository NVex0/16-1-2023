1. Lúc đầu e cũng không biết build number là gì :v, nhìn ví dụ xong thì hiểu là phiên bản windows. Đọc trên mạng thì tìm được SOFTWARE là subkey mô tả các chi tiết UI khác nhau
của hdh. Thế nên e export subkey Software ra để xem thông tin của Windows.
Mở registry viewer, theo path Windows/Windows NT/CurrentVersion -> e thấy được tên ver win là win 10 home single languge, với display ver là 21H1. 
![image](https://user-images.githubusercontent.com/113530029/212902148-7bf02963-6d2c-4036-8933-4fb3e777796a.png)

Khi xem trên wiki thì 
lấy được build number của nó: Win10-19043
![image](https://user-images.githubusercontent.com/113530029/212902449-a134a182-1038-41e4-bc09-ee74c7b23d74.png)

2. Dựa vào hint "Browser History", search mạng thì nó có liên quan tới Cache Data, cộng thêm có 1 bài đọc về forensic liên quan tới nhắm vào 3 file 123 ở Cache_Data, e 
nghĩ nó mật thiết :v, vậy nên e export folder Cache_Data ra rồi dùng ChromeCacheViewer để xem.

Đề có nói là nhận được Doc và Pass, e nghĩ ngay tới file Pass mà mình bỏ qua ở Basic Disk 1. Ban đầu e sort để tìm mấy file txt, nhưng nghĩ txt thì cần gì pass, nên đổi hướng qua
xem các web. Tạo report ra để xem, e chú ý tới pastebin.com, sort theo keyword 'pastebin', tìm 1 lúc là thấy link https://pastebin.com/XaxSi1c1 , thấy có 4 file:
+ 1 file md5 thì bỏ qua.
+ 1 file rick roll.
+ 1 file nhập 'p@$$w0rd3458' thì báo sai pass.
+ file này nhập pass 'p@$$w0rd3458' thì được và ta có được text: hehe_y0u_f0und_it.


-> flag: KCSC{Win10-19043_hehe_y0u_f0und_it}
