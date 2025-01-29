# springboot-heapdump

## Why?
https://gmodzelewski.github.io/blog/posts/2025-01-03-news/#volksdaten

This is a test application to test on an OpenShift cluster and prevent this somehow in production environment.

Possible solutions to check:
- via environment variables on the container (could be also used in ACS)
- via Connectivity Link
- via policy with Advanced Cluster Security for Kubernetes (=ACS)
- via Service Mesh


## How?
Start Application:
```shell
mvn spring-boot:run
```

Fetch heap dump and save to locale file named "heapdump". The format is [HPROF](https://docs.oracle.com/javase/8/docs/technotes/samples/hprof.html) and on OpenJ9 it is [PHD](https://eclipse.dev/openj9/docs/dump_heapdump/#portable-heap-dump-phd-format):
```shell
curl 'http://localhost:8080/actuator/heapdump' -O
```
