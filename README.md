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

## PROGRAM - ARP
# CLIENT 
~~~
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c, addr = s.accept()
address = {"10.155.193.34":"E0-2E-0B-35-48-8C"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
~~~      
## SERVER
~~~
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
~~~    
## OUPUT - ARP
<img width="1920" height="1080" alt="Screenshot (1)" src="https://github.com/user-attachments/assets/b34664ce-7dfb-4d25-ba4b-eeebd1f1aea1" />


## PROGRAM - RARP
## CLIENT
~~~
import socket
s = socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c, addr = s.accept()
address = {"E0-2E-0B-35-48-8C":"E0-2E-0B-35-48-8C"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
~~~
## SERVER
~~~
import socket
s = socket.socket()
s.connect(('localhost',9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("logical Address:", s.recv(1024).decode())
~~~
## OUPUT -RARP
<img width="1879" height="550" alt="Screenshot 2025-09-15 103336" src="https://github.com/user-attachments/assets/f86df80d-f988-44ad-87e2-8a3eb6e72c44" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
