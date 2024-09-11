# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
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
P
## PROGRAM - ARP
## CLIENT
```python
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
```
## SERVER
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## OUTPUT - ARP
## CLIENT
<img width="453" alt="image" src="https://github.com/user-attachments/assets/36e7111f-5788-414c-a0a0-f15eb5038799">

## SERVER
<img width="458" alt="image" src="https://github.com/user-attachments/assets/ca122510-6034-4651-8d38-d51e10bfdd12">

## PROGRAM - RARP
## CLIENT
```python
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
## SERVER
```python
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
## CLIENT
<img width="455" alt="image" src="https://github.com/user-attachments/assets/0de8e1eb-66b2-49d4-801d-00966045ea9b">

## SERVER
<img width="454" alt="image" src="https://github.com/user-attachments/assets/a7afb067-2d17-4209-b00c-6f433446d60e">


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
