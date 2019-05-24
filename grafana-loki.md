Started 3/18
open sourced 6 months ago

Loki: Like prometheus but for logs

Simple and cost effective to operate
Integrated with existing observability tools
Cloud native and airplane mode - was built on a plane

Loki doesn't index the text, instead groups into streams and indexes labels
i.e. you can use it to point to a stream of logs

very simple to scale, index is normally quite small

agent runs on node called prom tail

Airplane mode:
1 command runs loki
can be all run offline
stubs for using embedded / in memory db
Optionally microservices if you want - There's an option to split it out in a cloud native 10 microservice setup, but lots more difficult, grafana run it in production like this...

What's new
LogQL Filter Chaining
Extracting labels from logs
Live tailing, Context

Show context -> grep -c 10 - sooo cool

What's next:
Grafana labs is using it in prod for 6 months, its lost some data, but now it's pretty stable. 0.1 beta coming very soon
LogQL aggregations service side
Loki will never be for business analytics
It's for developers to debug errors
Add alerts and rules using aggregations
Remove dependency on nosql
First beta ASAP



