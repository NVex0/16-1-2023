Dựa vào hint, e dùng FTK Imager mở file, rồi export subkey ra để xem trên Registry Viewer.
với subkey SYSTEM, theo path ControlSet001/Control/ComputerName lấy được hostname của nó: DESKTOP-6MS14UO
![Screenshot (3108)](https://user-images.githubusercontent.com/113530029/212831282-34516352-3233-4ed1-bffa-e2b5f17b96fa.png)

Tiếp là phần 2, đề có đề cập tới việc xoá thư mục, check Recycle Bin thấy có 4 file, 1 cái rỗng. 2 file có nội dung base64 mà decode ra thì 1 cái được link yt với 1 cái giống với ví dụ ở đề :v. Nên ta được part 2. Ban đầu e thử hết cả 3 cái nhưng nhìn qua Basic Disk 2 thì bỏ được cái file Pass.txt, còn lại thì suy như trên.

Giống với phần 1, phần 3 e tìm theo path ControlSet001/Control/TimeZoneInformation và lấy được thời gian là SE Asia Standard Time. 
![image](https://user-images.githubusercontent.com/113530029/212831956-9addcbe5-c6f8-47b3-ab64-5d2b7d8aa692.png)

Search google -> UTC +8.
-> phần 3: UTC8.

=> flag: KCSC{6MS14UO_Kaxeetxe-Cause_I'd_die_for_you_You_know_I'd_still_die_for_you_UTC8}
