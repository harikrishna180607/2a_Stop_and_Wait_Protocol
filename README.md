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
## SERVER-SIDE
```
import socket

# Create socket
s = socket.socket()

# Bind host and port
s.bind(('localhost', 8000))

# Listen for client connection
s.listen(1)

print("Server is waiting for connection...")

# Accept connection
c, addr = s.accept()

print("Connected with:", addr)

while True:
    # Get message from server user
    msg = input("Enter a message: ")

    # Send message to client
    c.send(msg.encode())

    # Exit condition
    if msg.lower() == "exit":
        break

    # Receive acknowledgement
    ack = c.recv(1024).decode()

    print("Client:", ack)

# Close connection
c.close()
s.close()

```
## CLIENT-SIDE
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()


```
## OUTPUT
<img width="1916" height="1078" alt="image" src="https://github.com/user-attachments/assets/e109ebdc-1e8b-4ad0-9c2f-b119bcdad8de" />
<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/01047715-ba3c-4499-bf82-37f43d196f5e" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
