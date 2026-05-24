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
## Client:
```
import socket 
s=socket.socket() 
s.bind(('localhost',4000)) 
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
## Server:
```
import socket 
s=socket.socket() 
s.connect(('localhost',4000)) 
while True:
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
## Client:

<img width="1427" height="146" alt="Screenshot 2026-05-24 223243" src="https://github.com/user-attachments/assets/6fb37215-8994-408a-9402-b8c0f3235820" />

## Server:

<img width="1306" height="224" alt="Screenshot 2026-05-24 223336" src="https://github.com/user-attachments/assets/78e2b9cf-6fb0-4ddd-8c44-2acfe87de388" />

## PROGRAM - RARP

## Client:
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
## Server:
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
## Client:

<img width="1411" height="157" alt="Screenshot 2026-05-24 224118" src="https://github.com/user-attachments/assets/0c946bb3-40ac-4bf1-8592-18bee346fd8c" />

## Server:

<img width="1400" height="169" alt="Screenshot 2026-05-24 224157" src="https://github.com/user-attachments/assets/2eea796b-e5de-432f-ae03-b1179f00b77e" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
