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

## MQTT

- 가장 오래된 M2M(Machine to Machine) 통신 프로토콜이다.
- 제한된 네트워크에서 가벼운 M2M 통신을 위해 설계된 pub/sub 메시징 프로토콜이다.
- MQTT 클라이언트는 (다른 클라이언트가 subscribe하거나 향후 subscribe를 위해 보유할 수 있는) MQTT 브로커에 메시지를 게시한다.
- 모든 메시지는 각 topic에 맞게 게시된다. -전송 프로토콜로 TCP를 사용하고 보안을 위해 TLS/SSL을 사용합니다. => client와 broker 간의 connection-oriented이다.s
- Using 3-level QoS(Quality of Service) => for reliable delivery of messages.
- Suitable for large networks of small devices that need to be monitored or controlled from a back-end server on the Internet.

## CoAP

- It is mainly developed to interoperate with HTTP and the RESTful Web through simple proxies.
- MQTT와 다르게 CoAP 는 topic이 아닌 URI를 사용한다.
- Publisher는 URI로 data를 publish하고, subscriber는 URI로 표현된 특정 리소스에 subscribe를 한다.
-

## AMQP

## HTTP
