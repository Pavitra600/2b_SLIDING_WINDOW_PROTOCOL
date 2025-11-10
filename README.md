# EX.2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
    To implement the sliding window protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
```
CLIENT: 
 
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
size=int(input("Enter number of frames to send : ")) 
l=list(range(size)) 
s=int(input("Enter Window Size : ")) 
st=0 
i=0 
while True: 
    while(i<len(l)): 
            st+=s 
            c.send(str(l[i:st]).encode()) 
            ack=c.recv(1024).decode() 
            if ack: 
                print(ack) 
                i+=s 
```
```
SERVER: 
 
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:    
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode()) 
```
## OUTPUT:
### CLIENT:
<img width="758" height="209" alt="Screenshot 2025-10-25 134137" src="https://github.com/user-attachments/assets/05354327-1e7a-491e-8767-4656a3c566f5" />

### SERVER:

<img width="757" height="177" alt="Screenshot 2025-10-25 134150" src="https://github.com/user-attachments/assets/eed746c9-bbd4-4a93-9d4d-9ddb48e9740f" />

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed
