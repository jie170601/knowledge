用消息队列的原因
- 解耦
- 异步
- 削峰

erlang语言开发，实现了amqp

分发消息策略：
- 简单模式
- 工作队列
- 发布订阅
- 路由模式
- 通配符模式

集群：多台rabbitmq服务器组成一个集群，形成一个逻辑[[rabbitmq#Broker|Broker]]

支持STOMP，MQTT

# Broker
消息队列服务进程，包括[[rabbitmq#Exchange|Exchange]]和[[rabbitmq#Queue|Queue]]

# Exchange
消息队列交换机，按一定的规则将消息路由转发到某个队列。交换机是个关键组件，决定了消息发送到哪个队列，一共有4种交换机。
## direct
路由键和队列一一对应，完全匹配

## fanout 
消息会发布到绑定在交换机上的所有队列上，其实就是发布订阅模式

## topic
用通配符匹配路由到对应的队列，通配符前需要有`.`符号，通配符有两种：
- `*` 只能匹配一个词
- `#` 匹配一个或者多个词

## header
根据请求头来匹配路由，分为`全部匹配`和`部分匹配`


# Queue
消息队列，存储消息的队列

# 消息幂等
rabbitmq实现消息[[幂等]]的方式，rabbitmq不支持，[[activemq]]可以[[activemq#消息去重|消息去重]]