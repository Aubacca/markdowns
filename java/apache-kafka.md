# Apache Kafka

Apache Kafka is a distributed streaming platform.

- <a href="https://kafka.apache.org/" target="_blank">Homepage  - Apache Kafka</a>
- <a href="https://docs.confluent.io/current/app-development/kafkacat-usage.html" target="_blank">confluent - kafkacat Utility</a>

## Workshop - TVD-KAFKA-DEV

- <a href="https://tvdit.sharepoint.com/sites/bds/bds-bi/public/bigdata/Forms/AllItems.aspx?FolderCTID=0x012000791407513A0947478933C6168CE3CDD1&id=%2Fsites%2Fbds%2Fbds-bi%2Fpublic%2Fbigdata%2FBigDataEducation%2FWorkshops%2FTVD-KAFKA-DEV" target="_blank">Kursunterlagen in Trialog</a>
- <a href="https://github.com/gschmutz/kafka-workshop" target="_blank">Workshop</a>

## Kafka Fundamentals

Komponenten:
- kafka (Kafka Broker)
- kafka Connect (Source Connector, Sink Connector)
- kafka Streams (Stream Processing)
- kafka ksql (Stream Processing)

Weitere Komponenten:
- Records – consists of a key (optional), value and header (timestamp)​
- Topic – a stream of records, feed name​
    * Log – storage (architecture) of topic on disk​
    * Partition – sharding of topic​
- Producer – API to produce a stream of records​
- Consumer – API to consume a stream of records​
- Broker – Kafka server that is part of a Kafka cluster​
- Zookeeper – Does coordination of brokers / cluster topology

## Kurs Memos

- Data at Rest (Daten/Stream speichern, auswerten, Action) vs. Data in Motion (Daten/Stream auswerten, Action und speichern ..)
- Events: Stream Integration (laden von Events) und Stream Analytics (Events auswerten)
- Definition: CDC: Change Data Capture
- Definition: Event Hub === Kafka Broker
- Unified Log: Stream mit einer genauen definierten Reihenfolge der Daten
- Type of Message Queue Models:
    - Queue = one to one
    - Topic = one to many
- Definition: VETRO = Validate, Enrich, Transform, Route, Operate ???
- Zookeeper Ensamble: verwaltet den Hauptverantwortlichen kafka Broker
- kafka Topic: eine Sammlung von Informationen zum gleichen Thema (zb. wie eine Tabelle)
- es gibt leader Partitionen und failover Partitionen
- Serialization / Deserialization: Avro, Protobuf
- Start java via maven: `mvn exec:java@producer -Dexec.args="1000 100 0"`
