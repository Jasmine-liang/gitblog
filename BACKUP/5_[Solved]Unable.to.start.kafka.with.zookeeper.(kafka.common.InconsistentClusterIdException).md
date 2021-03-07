# [[Solved]Unable to start kafka with zookeeper (kafka.common.InconsistentClusterIdException)](https://github.com/Jasmine-liang/gitblog/issues/5)

## Problem shooting
Go to `/var/log/kafka`, find the **ERROR** message in the newest generated file.
## Solution
[ Unable to start kafka with zookeeper (kafka.common.InconsistentClusterIdException)](https://stackoverflow.com/questions/59481878/unable-to-start-kafka-with-zookeeper-kafka-common-inconsistentclusteridexceptio)
Delete` /var/lib/kafka/meta.properties
`
And it worked for me:)