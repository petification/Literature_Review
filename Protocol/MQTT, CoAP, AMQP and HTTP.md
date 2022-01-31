# Thesis :

# Choice of Effective Messaging Protocols for IoT

# Systems : MQTT, CoAP, AMQP and HTTP

<br /><br />

```Javascript
궁금한 부분 :
HTTP 가 Single Protocol 인 이유
IoT가 Single Protocol에 의존할 수 없는 이유
```

```Javascript
1차구분

- To address applications requiring fast and reliable business transactions
    - AMQP

- To address applications requiring data collection(e.g. sensor update) in constrained network
    - MQTT
    - CoAP

- To address applications requiring communicating over the Internet such as RESTful client/server
    - HTTP
    - CoAP
```

---

# About Protocol

### MQTT

```python
- 가장 오래된 M2M(Machine to Machine) 통신 프로토콜이다.
- 제한된 네트워크에서 가벼운 M2M 통신을 위해 설계된 pub/sub 메시징 프로토콜이다.
- MQTT 클라이언트는 (다른 클라이언트가 subscribe하거나 향후 subscribe를 위해 보유할 수 있는) MQTT 브로커에 메시지를 게시한다.
- 모든 메시지는 각 topic에 맞게 게시된다. -전송 프로토콜로 TCP를 사용하고 보안을 위해 TLS/SSL을 사용합니다. => client와 broker 간의 connection-oriented 이다.
- Using 3-level QoS(Quality of Service) => for reliable delivery of messages.
- Suitable for large networks of small devices that need to be monitored or controlled from a back-end server on the Internet.
```

### CoAP

```python
- It is mainly developed to interoperate with HTTP and the RESTful Web through simple proxies.
- MQTT와 다르게 CoAP 는 topic이 아닌 URI를 사용한다.
- Publisher는 URI로 data를 publish하고, subscriber는 URI로 표현된 특정 리소스에 subscribe를 한다.
- CoAP는 전송 프로토콜로 UDP를 사용하고, 보안을 위해 DTLS를 사용한다. 따라서 clients와 server는 적은 신뢰도의 connectionless datagram방식을 통해 통신한다.
- QoS를 지원하기 위해 "confirmable(전송에 대한 ACK받음)" 레벨과 "non-confimable(아무것도 안받음)" 레벨을 사용한다.
```

### AMQP

```python
- 가벼운 M2M 프로토콜이다.
- Reliability, security, provisioning and interoperability
- Request/Response 및 Publish/Subscribe 구조를 모두 지원한다.
- AMQP에서는 Publisher 혹은 Consumer 가 지정된 이름으로 "exchange"를 만든 후 해당 이름을 브로드캐스팅 해야한다.
- 서로를 구분하기 위해 "exchange"에 지정된 이름을 사용한다.
- "exchange"에서 수신한 메시지는 "binding"이라는 과정을 통해 queue와 일치되어야 한다.
- AMQP 는 전송프로토콜로 TCP를 사용하며, 보안을 위해 TLS/SSL 그리고 SASL을 사용한다. => client와 broker 간의 connection-oriented이다.
- 두가지 레벨의 QoS를 지원 : Unsettle Format(not reliable) & Settle Format(reliable)
- 신뢰성이 AMQP의 가장 큰 특징
```

### HTTP

```python
- 주로 web messaging protocol로 사용된다.
- HTTP는 request/response RESTful Web architecture를 지원한다.
- CoAP와 유사하게 URI 방식을 사용하며, 서버에서 URI를 통해 데이터를 제공하면 client는 URI를 통해 데이터를 공급 받는다.
- Text-based protocol 이다.
- HTTP는 전송 프로토콜로 TCP를 사용하며, 보안을 위해 TLS/SSL을 사용한다. => client와 server 간의 connection-oriented이다.
- 별도의 명시적인 QoS를 가지고있지 않으며, 이를 위한 support를 필요로한다.
```

---

# The Comparison between each Protocol : MQTT, CoAP, AMQP and HTTP

### 1. Message Size vs Message Overhead

- MQTT, AMQP and HTTP run on TCP => 연결 및 연결종료에 오버헤드가 존재
- MQTT는 가볍고 메시지당 2바이트의 가장 작은 헤더크기를 가지지만 TCP 연결 요구 사항은 전체 오버헤드를 증가시켜 메시지 크기를 증가시킴.
- AMQP는 reliability, security, provisioning and interoperability를 보장하기에 오버헤드가 크다.
- HTTP는 IoT가 아닌 Web을 위해 설계되었기에 최대의 오버헤드 및 메시지 크기를 가진다.
- CoAP runs on UDP => 연결에 별다른 오버헤드가 따르지 않는다.

![Message size and overhead.jpg](//images/Message size and overhead.jpg)
