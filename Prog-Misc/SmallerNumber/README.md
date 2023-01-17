Giống bài sô lớn nhất :c, cũng lấy data về để làm rồi gửi đi.
```
def sosanh(array):
    fin = []
    for i in array:
        count = 0
        for j in array:
            if int(j) < int(i):
                count += 1
        fin.append(count)
    return fin

import socket
host = "146.190.115.228"
port = 10454
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_address = ((host, port))
s.connect(server_address)
nloop = 0
start = 8
while True:
    receive = s.recv(1024).decode("utf8")
    print(receive)
    receive = receive[start:-7]
    arr = receive.split(",")
    print(arr)
    tmp = sosanh(arr)
    sending = "["
    for i in tmp:
        sending += str(i) + ", "
    sending = sending[:-2]
    sending += "]\n"
    print(sending)
    s.send(sending.encode("utf8"))
    ######
    nloop += 1
    start = 33 + len(str(nloop))
s.close()
