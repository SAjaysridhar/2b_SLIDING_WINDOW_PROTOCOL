# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT:
```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 

size=int(input("Enter number of frames to send : ")) 
l=list(range(size)) 

ws=int(input("Enter Window Size : ")) 

st=0 
i=0 

while True: 
    while(i < len(l)): 
        st = i + ws   # corrected index
        
        c.send(str(l[i:st]).encode()) 
        
        ack = c.recv(1024).decode() 
        
        if ack: 
            print(ack) 
            i += ws
```
SERVER:
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode()) 
```

## OUPUT
CLIENT:
<img width="941" height="947" alt="image" src="https://github.com/user-attachments/assets/8399ba4f-ff04-43e4-97b4-c6b4659090e1" />

SERVER:
<img width="931" height="916" alt="image" src="https://github.com/user-attachments/assets/c93c80d8-7c47-47cb-a494-34071b7590ef" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
