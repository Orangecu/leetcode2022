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
    


