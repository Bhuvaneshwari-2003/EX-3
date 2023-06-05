### 19CS406-EX-3 IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To write a python program to perform sliding window protocol

## ALGORITHM:

1. Start the program.

2. Get the frame size from the user

3. To create the frame based on the user request.

4. To send frames to server from the client side.

5. If your frames reach the server it will send ACK signal to client otherwise it will send NACKsignal to client.

6. Stop the program

## PROGRAM:

## CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',8080))
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
## SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8080))
while True:
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
 ```
 ## OUTPUT:
## CLIENT SIDE:

![image](https://github.com/Bhuvaneshwari-2003/EX-3/assets/94828604/23c9a9a8-80a6-4186-aeec-23f84312b4d1)

## SERVER SIDE:

![image](https://github.com/Bhuvaneshwari-2003/EX-3/assets/94828604/d3fe28c4-a8bb-447a-8fd9-a844fe9e1621)

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed.
