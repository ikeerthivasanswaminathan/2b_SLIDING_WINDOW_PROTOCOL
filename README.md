# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

## AIM
To write a python program to perform implementation of sliding window protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program

## PROGRAM

**client.py**
```
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

**server.py**
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 

while True:    
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```

## OUTPUT

**Client Ouput**

![ex 2b client](https://github.com/NaliniG007/2b_SLIDING_WINDOW_PROTOCOL/assets/148937372/146d844e-4000-4519-8691-223b119f7763)

**Server Output**

![ex 2b server](https://github.com/NaliniG007/2b_SLIDING_WINDOW_PROTOCOL/assets/148937372/1d84848d-1f37-45a9-92d0-03cb87bcec39)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
