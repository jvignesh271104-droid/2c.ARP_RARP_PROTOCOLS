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
```
import socket

# Create socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind to localhost and port
host = '127.0.0.1'
port = 12345
server_socket.bind((host, port))

# Listen for connections
server_socket.listen(1)
print("Server is waiting for connection...")

# Accept client connection
conn, addr = server_socket.accept()
print("Connected to:", addr)

# Receive data
data = conn.recv(1024).decode()
print("Message from client:", data)

# Send response
conn.send("Hello from server!".encode())

# Close connection
conn.close()
server_socket.close()
```
## OUPUT - ARP
<img width="1215" height="309" alt="image" src="https://github.com/user-attachments/assets/d0ec6692-6605-4369-87d8-02045adfef09" />

## PROGRAM - RARP
```
import socket

# Create socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
host = '127.0.0.1'
port = 12345
client_socket.connect((host, port))

# Send message
client_socket.send("Hello from client!".encode())

# Receive response
data = client_socket.recv(1024).decode()
print("Message from server:", data)

# Close connection
client_socket.close()
```
## OUPUT -RARP
<img width="1035" height="131" alt="image" src="https://github.com/user-attachments/assets/9c451bad-fe30-4157-80b3-bd058b32fbeb" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
