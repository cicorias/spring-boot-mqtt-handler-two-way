# Getting Started

## MQTT for arm
[arm64v8/eclipse-mosquitto](https://hub.docker.com/r/arm64v8/eclipse-mosquitto/)

When on MacBook arm (m1/m2) devices, the mosquitto broker is different.

Run from the root of this repo:
```
docker run -it -p 1883:1883 -p 9001:9001 -v $PWD:/mosquitto/config/  arm64v8/eclipse-mosquitto
```

## NOTES:
need to align on topics correctly -- not correct now

```
# where clients listen
# pattern readwrite $dps/registrations/res/#
# where clients publish
# pattern readwrite $dps/registrations/PUT/iotdps-register/#

user admin
# dps subscribes to these topics
## this is where devices send initial registration requests
topic readwrite $dps/registrations/PUT/iotdps-register/#
## this is where devices send operationa status requests
topic readwrite $dps/registrations/GET/iotdps-get-operationstatus/#
# this is where DPS responds with status
topic readwrite $dps/registrations/res/#


pattern write $dps/registrations/PUT/iotdps-register/%u/#
pattern write $dps/registrations/GET/iotdps-get-operationstatus/%u/#
pattern read $dps/registrations/res/%u/#
```


### Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/2.7.9/maven-plugin/reference/html/)
* [Create an OCI image](https://docs.spring.io/spring-boot/docs/2.7.9/maven-plugin/reference/html/#build-image)
* [Spring Integration Test Module Reference Guide](https://docs.spring.io/spring-integration/reference/html/testing.html)
* [Spring Integration](https://docs.spring.io/spring-boot/docs/2.7.9/reference/htmlsingle/#messaging.spring-integration)

### Guides
The following guides illustrate how to use some features concretely:

* [Integrating Data](https://spring.io/guides/gs/integration/)

