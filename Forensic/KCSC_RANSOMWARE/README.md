Vừa bật máy ảo lên thì có cửa sổ của encrypt.exe pop up ra, e đoán nó được lập lịch, check trong Task Scheduler thì thấy thật. Nhìn phần mô tả ta được part 1 của flag:

![image](https://user-images.githubusercontent.com/113530029/213938107-ba5738ae-9ca4-4eff-8766-aa14aea2239d.png)

`KCSC{D0nt_sk1p_4nyth1ng_`

kèm theo 1 link dẫn đến bài hướng dẫn tạo ransomware bằng python.

Dễ dàng nhìn thấy trên desktop có file `flag.kcsc` mà mở ra không đọc được ra gì, e thử tạo file để test và run encrypt.exe thì thấy nó bị mã hoá dạng hao hao thế, nên chắc đoạn này hướng đi là phải decrypt ransomware rồi.

Nhưng chưa biết private key để giải. Nên e đã thử dịch ngược encrypt.exe bằng pyinstxtractor. Tuy nhiên lại trả về file không nhận dạng được :v, hên là vẫn đọc được 1 dòng gần đầu nhìn như base64, decode ra thì thấy y xì với publickey từ link lấy từ part 1. Vậy nên e dùng private key ở đó luôn.
Sửa code Decryptor đi 1 tí (extension thành ".kcsc"), run code và mở file flag_decrypted ra, được part 3 của flag:

`_1n_v1ct1m_c0mput3r}`

về Part 2 thì, mở Procmon lên, run encrypt.exe.

Dựa vào hint, e chỉ tập trung vào mục %temp% với filter là `PID is 4852`.

Part 2 là đi đếm số malicious dlls, nên là filter thêm `path endswith .dll` vào nữa.

Tham khảo 1 số bài viết về dll-hijicking, e thêm filter `result is NAME NOT FOUND`.

![image](https://user-images.githubusercontent.com/113530029/213938466-9796c916-3adc-4d81-ac03-0e3eeba1b768.png)

v là rút ngắn còn 10 dlls :v e bruteforce ra flag. Hóng Wu chữa bài này sớm :c

flag: `KCSC{D0nt_sk1p_4nyth1ng_7_1n_v1ct1m_c0mput3r}`
