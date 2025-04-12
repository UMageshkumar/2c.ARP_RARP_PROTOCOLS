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
client.py
```
import socket 
s=socket.socket() 
s.bind(('localhost', 8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2:45", "165.165.79.1":"8A:BC:E3:FA:65"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode()) 
```
server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost', 8000)) 
while True: 
    ip=input("Enter logical Address: ") 
    s.send(ip.encode()) 
    print("MAC Address", s.recv(1024).decode()) 
```
## OUPUT - ARP
![Screenshot 2025-04-12 105339](https://github.com/user-attachments/assets/53a49a0d-f2a5-4790-8785-0f16a3ff9bab)

## PROGRAM - RARP
client.py
```
import socket 
s=socket.socket() 
s.bind(('localhost', 9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100", "8A: BC:E3:FA": "192.168.1.99"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode()) 
```
server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost', 9000)) 
while True: 
    ip=input("Enter MAC Address: ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode()) 
```
## OUPUT -RARP
![Screenshot 2025-04-12 105911](https://github.com/user-attachments/assets/0711b0cb-19a1-4067-892d-b2f4041f9c5b)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
