
```
def maxfunc(string):
    numb = "0123456789"
    array = []
    for i in string:
        if i in numb:
            array.append(int(i))

    # sort
    def partition(array, start, end):
        pivot = array[start]
        low = start + 1
        high = end

        while True:
            while low <= high and array[high] >= pivot:
                high = high - 1

            while low <= high and array[low] <= pivot:
                low = low + 1

            if low <= high:
                array[low], array[high] = array[high], array[low]
            else:
                break

        array[start], array[high] = array[high], array[start]

        return high

    def quick_sort(array, start, end):
        if start >= end:
            return

        p = partition(array, start, end)
        quick_sort(array, start, p - 1)
        quick_sort(array, p + 1, end)

    quick_sort(array, 0, len(array) - 1)
    
    out = ""
    for i in array:
        out += str(i)
    return out[::-1]
    #Tới đây là hàm trả về số lớn nhất.
    
import socket

host = "146.190.115.228"
port = 10464
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_address = ((host, port))
s.connect(server_address)

#Đoạn này thì xong được case đầu tiên thì nó nhận cả cái dòng hiện điểm nữa . Nên e code bẩn hàm này để bỏ qua cái dòng điểm đấy :(
def selectline(string):
    tmp = string.split(" ")
    for i in tmp:
        count = 0
        for j in i:
            if j.isdecimal():
                count += 1
        if count > 3:
            return i
        
while True:
    receive = s.recv(1024).decode("utf8")
    print(receive)
    sending = selectline(receive)
    sending2 = maxfunc(sending) + "\n"
    print(sending2)
    s.send(sending2.encode("utf8"))
s.close()
