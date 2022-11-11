#Project

## Project connections    
    
    Client -> Media service
            -> New service 
             -> Analytic service -> Notification service

### Network connection - Layers

    Network Connections View
     Host A -> Router -> Router -> Host B

     TCP/IP Model
     Application -> transport -> Network -> Network Access and return


    
OSI Model- Data & Layers (7层协议)

    Data    -> Application (HTTP, FTP, SSH, DNS)
            -> Presentation (SSL, MPEG, JPEG)
            -> Session (Socket, API)
    Segments -> Transport (TCP, UDI)

    Packets -> Network (IP, ICMP, IGMP)
    Frams -> Data Link (Mac, Ethernet, Swich)
    Bits -> Physical (Fiber, Wireless, Repeater)

IPv4 (only 32 bits) (Bad)
IPv6 (128 bits) (Good)

### TCP -three way HandShake (need response to build connection) 200ms
Slow but reliable transfers   
Email, web browsing

    Sender                          Receiver
    Send SYN ---------------------> Receive SYN
    Receive ACT <------------------ Return SYN ACK
    Send Application Data --------> Receive Data

### UDP  (Just send anything, no need to check) 100ms
Fast but Non guaranteed transfers
VoIP
Music Streaming

    Sender                          Receiver
    Receive Request <-------------- Send Request
    Respond ----------------------> Receive Respond
    Respond ----------------------> Receive Respond
    Respond ----------------------> Receive Respond

### TCP- 4 Wat HandShake (Same from 3 way but with end) 

### UDP-QUIC 0ms

    Sender                          Receiver
    Send -------------------------> Receive
    



```python
courseRoomNumbers={'CS101':'3004','CS102':'4501','CS103':'6755',

'NT110':'1244','CM241':'1411'}

instructorCourse={'CS101':'Haynes','CS102':'Alvarado',

'CS103':'Rich','NT110':'Burke','CM241':'Lee'}


courseMeetingtime={'CS101':'8:00 a.m','CS102':'9:00 a.m',

'CS103':'10:00 a.m','NT110':'11:00 a.m',

'CM241':'1:00 p.m'}


courseNumber=input("Enter the Course Number: ")


print("Course's Room Number:",courseRoomNumbers[courseNumber])


print("Instructor:",instructorCourse[courseNumber])

print("Meeting Time:",courseMeetingtime[courseNumber])


```