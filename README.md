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
server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
client.py
```
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
## OUPUT - ARP
server
<img width="882" height="257" alt="2c server arp" src="https://github.com/user-attachments/assets/e78f9933-a15d-472b-8ace-4e8da89e1d28" />

client
<img width="877" height="205" alt="2c client arp" src="https://github.com/user-attachments/assets/e6b659ae-56f4-49f5-8daa-9c31f1968d48" />

## PROGRAM - RARP

server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```

client.py
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
## OUPUT -RARP
server
<img width="898" height="271" alt="2c server rarp" src="https://github.com/user-attachments/assets/d61e77a3-af1f-4357-9ab5-7068398cd1d5" />

client
<img width="808" height="298" alt="2c client rarp" src="https://github.com/user-attachments/assets/34abbed0-d2f4-43c2-97ee-0b5a6c1cc92c" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
