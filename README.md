##### Commands:
Launch Confluent Platform by running
- $ docker-compose up -d

##### Create a topic:
- $ docker-compose exec broker kafka-topics --create --topic example-topic --bootstrap-server broker:9092 --replication-factor 1 --partitions 1

##### Start a Console consumer:
- $ docker-compose exec broker bash
- $ kafka-console-consumer --topic example-topic --bootstrap-server broker:9092 

##### Start a producer (new terminal tab):
- $ docker-compose exec broker bash
- $ kafka-console-producer --topic example-topic --broker-list broker:9092

##### Key-value Pairs:
- Exit consumer and producer
- To enable sdending full key-value pairs from the command line you add two properties to your console producer, `parse.key` and `key-seperator`
- `kafka-console-producer --topic example-topic --broker-list broker:9092\
  --property parse.key=true\
  --property key.separator=":"`
- Enter records one at a time or all together:
`key1:what a lovely
key1:bunch of coconuts
foo:bar
fun:not quarantine`

- Start a consumer:
`kafka-console-consumer --topic example-topic --bootstrap-server broker:9092 \
 --from-beginning \
 --property print.key=true \
 --property key.separator="-"`

##### Clean up:
- Stop console producers and consumers with `CTRL+C`
- Close the container shells with `CTRL+D`
- Shiut down the stack by running: `docker-compose down`