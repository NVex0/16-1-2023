Theo đề bài, lấy byte của 2 ảnh ra, cái nào khác nhau thì lấy -> flag.
```
with open("/home/kali/Downloads/1.jpg", "rb") as f1:
    data1 = f1.read()
with open("/home/kali/Downloads/2.jpg", "rb") as f2:
    data2 = f2.read()
flag = ""
for i in range(len(data1)):
    if data1[i] != data2[i]:
        tmp = data1[i] ^ data2[i]
        flag += chr(tmp)
print(flag)
