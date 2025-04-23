# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
client.py
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames to send: "))

for i in range(n):
    frame = f"Frame {i+1}"
    s.send(frame.encode())
    print("Sent:", frame)

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.send("END".encode())
s.close()

server.py

import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Server is running...")

conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if data == "END":
        break
    print("Received:", data)
    conn.send("ACK".encode())

conn.close()
s.close()
```
## OUTPUT
![Screenshot 2025-04-23 221358](https://github.com/user-attachments/assets/6b660814-149a-417b-9600-86fc82a09313)
![Screenshot 2025-04-23 221405](https://github.com/user-attachments/assets/b7b764a5-8f4d-4622-ae47-2dbf8cd0b8a6)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
