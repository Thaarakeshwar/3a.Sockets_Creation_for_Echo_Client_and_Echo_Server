# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS

## NAME : Thaarakeshwar

## REG NUMBER : 212225040466

# AIM

To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.

## ALGORITHM:

1. Import the necessary modules in python.
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.

## PROGRAM

server.py
```c
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")

c, addr = s.accept()
print(f"Connected to {addr}")

while True:
    client_message = c.recv(1024).decode()
    if not client_message or client_message.lower() == 'exit':
        print("Client disconnected.")
        break
    print(f"Client: {client_message}")
    reply = input("Server (you): ")
    c.send(reply.encode())
    if reply.lower() == 'exit':
        break

c.close()
s.close()
```

client.py

```c
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    message = input("Client (you): ")
    s.send(message.encode())
    if message.lower() == 'exit':
        break
    server_reply = s.recv(1024).decode()
    if not server_reply or server_reply.lower() == 'exit':
        print("Server disconnected.")
        break
    print(f"Server: {server_reply}")

s.close()
```

## OUPUT

![Uploading image.png…]()


## RESULT

Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
