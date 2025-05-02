# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM:
To write a python program for simulating ARP/RARP protocols using TCP.

## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.


## PROGRAM - ARP
Client:

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

Server:

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address:")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

## OUPUT - ARP
Client:

![CNarpclient](https://github.com/user-attachments/assets/66cc0238-7877-4291-b0c8-f004a6e92916)

Server:

![CNarpserver](https://github.com/user-attachments/assets/e208a529-37e9-4cc6-a404-b8fc151b2d8b)

## PROGRAM - RARP
Client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

Server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP
Client:

![CNrarpclient](https://github.com/user-attachments/assets/2d26d807-939f-42c3-bc79-cb14f1d739fb)

Server:

![CNrarpserver](https://github.com/user-attachments/assets/83de4b12-998a-4d6a-8ddc-4566fde34e8f)

## RESULT:
Thus, the python program for simulating ARP/RARP protocols using TCP was successfully 
executed.
