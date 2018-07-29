# Python Client Tcp

## Introduction

This python module is for creating a tcp client. The code allows for the client to receive and send ints,shorts, and strings. The messages are formated in the way that there are two bytes before the actual contents of the message. The first byte is the size of the message and the second is a null byte.

## How to use

1. Successfully import the module into your python project

```python
from clientNet import *
```

2. Connect to your server

```python
sock = tcp_connect("127.0.0.1",3000)
```
Note: An exception will be thrown if the connection fails. Also tcp_connect returns a socket object that you must keep to be able to send and receive messages.

3. Read or write messages 

### Reading messages

```python
packet_cases = {
        0 : function1,
        1 : function2
}
def function1:#func 1 is going to be if string was received
  print(readstring())

def function2:#func 2 is going to be if int was received
  print(str(readint())
```
```python
if (receivemessage(sock) > 0):
   packetID = readbyte() #it is helpful to have the first byte of your message be what type of message it is
   packet_cases[packetID]()
```
### Writing messages
```python
def sendString(text):
  global sock
  messageid = 0
  clearbuffer() #always want to clearbuffer before sending new message
  writebyte(messageid)
  writestring(text)
  sendmessage(sock)
```
