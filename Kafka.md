#kafka 
Kafka

fanout the read, model to fanout the raw data. (Using multiple consumer groups) https://kafka.apache.org/documentation.html


decouple the write


2 phase commit??
outbox pattern (cdc + data streaming changes to Kafka)
Saga pattern

Saga orchestrator (watching for the updates in the db, checking for the failure and notices)

Kafka supports asyncapi as well.