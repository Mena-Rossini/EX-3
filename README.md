# EX-3 IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

## Date : 20-03-2023

## AIM:
To write a python program to perform sliding window protocol

ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client otherwise it
will send NACKsignal to client.
6. Stop the program


## PROGRAM:

### CLIENT:
```
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
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
 ```
## OUTPUT:

### CLIENT:
![242639258-b8fbf260-0373-4c59-b4ab-83dd6a23bee8](https://github.com/Mena-Rossini/EX-3/assets/102855266/765e0ec7-b3f4-47f6-95a3-826daf0967ef)


### SERVER:
![242639172-33c60487-ba3b-4474-bf6d-4b80cdd91a82](https://github.com/Mena-Rossini/EX-3/assets/102855266/cd4c95ef-d75e-41cc-a2cc-7e990d904085)


## RESULT:
Thus, python program to perform sliding window protocol was successfully executed.
