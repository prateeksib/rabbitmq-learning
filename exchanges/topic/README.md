# Topic

- Topic exchange uses routing key as in direct exchange, but it doesn't check for the exact match only the pattern check is needed.
- Routing key may include more than one seperated by `.`.
- Routing key consists of wildcards for matching message's routing key.
- Available wildcards are as follows:
  - _\*_ _(astrick)_: Matches exactly one word.
    example: image.\*, will match `image.jpeg, image.png` etc but not bitmap.image or image.bitmap.jpeg
  - _\#_ _(hash)_: Matches zero or more words.
    example: image.\#, will match `image.jpeg, image.png, image.bitmap.jpeg` etc but not bitmap.image

## Example

- We have created an exchange named `X_topic` with type `topic`.
- Than we bind that exchange to newly created queues named, `Q_topic_1` with routing key `*.image.*`, `Q_fanout_2` with routing key `#.image` & `Q_fanout_3` with routing key `image.#`.
- Than we published the message to the exchange. Which than push the message to specific queue to which the pattern of the routing key matches with the message routing key.

### Topic Exchange Binding

![Binding](https://github.com/prateeksib/rabbitmq-learning/blob/main/images/topic-exchange.png)

### [Producer](https://github.com/prateeksib/rabbitmq-learning/blob/main/exchanges/topic/producer/producer.go)

![Producer](https://github.com/prateeksib/rabbitmq-learning/blob/main/images/topic-producer.png)

### Queued

![Queued](https://github.com/prateeksib/rabbitmq-learning/blob/main/images/topic-queued-msg.png)

### [Consumer](https://github.com/prateeksib/rabbitmq-learning/blob/main/exchanges/topic/consumer/consumer.go)

![Consumer](https://github.com/prateeksib/rabbitmq-learning/blob/main/images/topic-consumer.png)

### Consumed Messages

![Consumed Messages](https://github.com/prateeksib/rabbitmq-learning/blob/main/images/topic-consumed-msg.png)
