---
title: TCP
publish: true
date created: 2026-11-24
tags:
  - backend
  - Sah
---
**TCP (Transmission Control Protocol)** is a communication protocol that allows two devices to exchange data reliably over a network, such as the Internet or a local network.

In simple terms, TCP makes sure that when one device sends data to another, the data arrives **correctly, completely, and in the right order**.

## **1. Why do we need TCP?**

Imagine you're sending a message consisting of 3 parts:

```
Hello → How → Are you?
```

When data travels through a network, packets might:

- Arrive in the wrong order.
    
- Get lost.
    
- Arrive more than once.
    

TCP handles these problems to make communication reliable.

## **2. How does TCP work?**

[TCP 3-Way Handshake](https://images.openai.com/static-rsc-4/6gwA6gBGeNzuFPpuXdmiAs-vlhGCbPmLWBgI_4xJCZxasydLAwYwM8FCbvaLpPhutfzcMhfoVnohyupfP_Nzx5KP3BexROJjP8T2Ai6setOQ53pzUai8U3spaoDWIONhaiEVa9wLnsHUh8d2wIsoUNo_L2cSoErWphUHRcaQFPA?purpose=inline)

[blog.jargoniseasy.com](https://blog.jargoniseasy.com/tcp-3-way-handshake?utm_source=chatgpt.com)

Before exchanging data, TCP establishes a connection using a process called the **Three-Way Handshake**.

There are three steps:

1. **SYN:** Client says: "I want to establish a connection."
    
2. **SYN-ACK:** Server replies: "I received your request, and I'm ready."
    
3. **ACK:** Client confirms: "Great, let's communicate."
    

Now the connection is established, and they can exchange data.

## **3. Main characteristics of TCP**

|Feature|Explanation|
|---|---|
|Reliable|Ensures data is delivered successfully.|
|Connection-oriented|Establishes a connection before sending data.|
|Ordered|Delivers data in the correct order.|
|Error detection|Detects corrupted data.|
|Retransmission|Resends lost data.|
|Flow control|Prevents overwhelming the receiver.|

## **4. TCP vs UDP**

You might also hear about UDP (User Datagram Protocol).

Both are transport-layer protocols, but they work differently.

|TCP|UDP|
|---|---|
|Reliable delivery|No delivery guarantee|
|Connection-oriented|Connectionless|
|Maintains packet order|No ordering guarantee|
|More overhead|Less overhead|
|Often higher latency|Often lower latency|

Examples:

- **TCP:** Web browsing (HTTP/HTTPS), SSH, database connections.
    
- **UDP:** Online gaming, live video streaming, DNS queries.
    

## **5. Where does TCP fit in networking?**

Think of network communication as layers:

[[Networking Theory] Understanding TCP/IP: The Backbone of the Internet | by Kyle Law | Medium](https://images.openai.com/static-rsc-4/_ar_igZVIYPtExgIE0zS_2KR8Oz6UenzAunKBRvojJoqAIm4rNFgdVYswip7W9WkQArmXhq5qwqrMP1XaP5R643kr5HzNgVGHNuML2YOLp2XlPCqO7_f9IAS9JC48nEg5WS4oiFl6d30ySdY2eg2LTnGNyDUh68FK5oNSL1giog?purpose=inline)

[medium.com](https://medium.com/%40kylelzk/networking-theory-understanding-tcp-ip-the-backbone-of-the-internet-c435f50d7a9a?utm_source=chatgpt.com)

TCP belongs to the **Transport Layer**.

For example, when your application connects to PostgreSQL:

```
Your Application
       |
       | SQL request
       v
    PostgreSQL
       |
       | TCP connection
       v
   Network (IP)
       |
       v
   Other Machine
```

PostgreSQL commonly uses TCP port **5432**.

When you connect to your local PostgreSQL server using:

```
psql -h localhost -p 5432 -U postgres
```

TCP is typically used to establish communication between your client and PostgreSQL.

**The most important thing to remember:**

- IP is responsible for addressing and routing packets to the destination.
    
- TCP is responsible for reliable communication between applications on the two devices.
    
- A port identifies the particular application or service receiving the communication.
    

A useful next concept to learn is **the difference between an IP address, a port, and a TCP connection**, because these three concepts are fundamental to understanding SSH, Docker networking, and database connections.



---
[[Backend]]