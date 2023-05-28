# EX-3 IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

## DATE : 23-30-2023


# AIM : To write a python program to perform sliding window protocol


# ALGORITHM :
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client otherwise it
will send NACKsignal to client.
6. Stop the program


# PROGRAM :
## CLIENT
```PYTHON 3

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
## SERVER
```PYTHON 3
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```

# OUTPUT :
## CLIENT
![image](https://github.com/Bhargava-123/EX-3/assets/85554376/3c826ccb-40c4-4930-b9a5-e87641939768)

## SERVER

![image](https://github.com/Bhargava-123/EX-3/assets/85554376/bf79020c-dba9-4a22-9334-b4a83504f750)


# RESULT:

Thus, python program to perform stop and wait protocol was successfully executed.

