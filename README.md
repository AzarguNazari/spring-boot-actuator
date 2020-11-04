# spring-boot-actuator
Spring actuator helps the spring boot serivces to be monitored and manage. Spring actuator provides rest endpoint of all information about services, such as beans instance, logging, health check, which services are healthy, jmx status of underlying JDK, and many other useful materics that would help the monitoring of microservices easier.

Spring boot acutaor can be applied to a spring boot service through depedency of `spsring-boot-starter-actuator`.

## Endpoint
Spring boot provides endpoint to let your spring booot service to be monitored. There are buillt-in endpoints that provide information where you can also add your own custom endpoint. You can enable or disable the endpoints manually through properites. The endpoints are available under /actuator.

The following endpoints are avaialble:
- auditevents
- beans
- caches
- conditions
- configprops
- env
- flyway
- health
- httptrace
- info
- integrationgraph
- loggers
- liquibase
- metrics
- mappings
- scheduledtasks
- sessions
- shutdown
- threaddump
- heapdump
- jolokia
- logfile
- prometheus




## How to enable shutdown endpoint?
`management.endpoint.shutdown.enabled=true`
`management.endpoints.enabled-by-default=false`
`management.endpoint.info.enabled=true`


## Properties of exposure the endpoint
`managemment.endpoints.jmx.exposure.exclude=*`
`masnagemment.endpoints.jmx.exposure.include=*`
`management.endpoints.web.exposure.exclude=heath, log`
`management.endpoints.web.exposure.include=info,health`




## How to secure the endpoints?
```
@Configuration(proxyBeanMethods = false)
public class ActuatorSecurity extends WebSecurityConfigurerAdapter{
  @Override
  protected void configure(HttpSecurity http) throws Exception{
     http.requrestMatcher(EndpointRequest.toAnyEndpoint()).authorizeRequest(request -> request.anyRequest().hasRole("ENDPOINT_ADMIN"));
     http.httpBasic();
  }
}
```

## Bean cache time to live
`management.endpoint.beans.cache.time-to-live=10s`





















https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html

- spring boot admin
- spring boot client
- spring boot actuator
