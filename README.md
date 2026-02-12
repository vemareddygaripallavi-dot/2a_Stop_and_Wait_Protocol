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
server.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Server is waiting for connection...")
conn, addr = s.accept()
print("Connected with", addr)

while True:
    frame = conn.recv(1024).decode()
    
    if not frame:
        break
        
    print("Received Frame:", frame)
    
    ack = "ACK"
    conn.send(ack.encode())
    print("Acknowledgment sent")

conn.close()
```
client.py
```
import socket
import time

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames to send: "))

for i in range(n):
    frame = f"Frame {i}"
    s.send(frame.encode())
    print("Sent:", frame)
    
    ack = s.recv(1024).decode()
    print("Received:", ack)
    
    time.sleep(1)

s.close()
```
## OUTPUT
<img width="723" height="257" alt="image" src="https://github.com/user-attachments/assets/3fe1ba17-8708-44c6-ac81-f9789e08ed3f" />
<img width="702" height="242" alt="image" src="https://github.com/user-attachments/assets/60216e55-8aa9-47a2-95dc-a0c8017e6632" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
