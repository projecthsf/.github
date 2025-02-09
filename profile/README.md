# Project HSF

Project HSF is a framework to help simplifies API integration by eliminating the need for manual client generation and JSON response parsing.

## 1. Dependency
```xml
<dependency>
    <groupId>io.github.projecthsf</groupId>
    <artifactId>spring-hsf</artifactId>
    <version>2.0.0</version>
</dependency>
```
## 2. How to use
### a. Api Interface:
```java
public interface CustomerApi {
    int getCount(int groupId);
}
```

### b. Api Provider (Server):
```java
@HsfProvider
public class CustomerApiImpl implements CustomerApi {
    @Override
    public int getCount(int groupId) {
        return 50;
    }
}
```

### c. Api Consumer (Client):

#### - Config bean:
```java
@Configuration
public class HsfConsumerConfig {
    @HsfConsumer
    private CustomerApi customerApi;
}
```
#### - And use from controllers/services:
```java
@RestController
@RequiredArgsConstructor
public class CustomerController {
    private final CustomerApi customerApi;

    @GetMapping("/customer/count")
    public Integer getCount() {
        return customerApi.getCount(1);
    }
}
```

[HSF Demo](https://github.com/projecthsf/spring-hsf-demo)

## 4. Documents:

[HSF Overview](https://github.com/projecthsf/spring-hsf/blob/main/docs/overview.md)

[HSF Application Properties](https://github.com/projecthsf/spring-hsf/blob/main/docs/properties.md)

[HSF Consumer](https://github.com/projecthsf/spring-hsf/blob/main/docs/consumer.md)

[HSF Provider](https://github.com/projecthsf/spring-hsf/blob/main/docs/provider.md)

[Report an issue](https://github.com/projecthsf/spring-hsf/issues)

