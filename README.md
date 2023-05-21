# microservices
microservices playground
Thanks to: https://www.youtube.com/playlist?list=PLSVW22jAG8pBnhAdq9S8BpLnZ0_jVBj0c

# Eureka Discovery Server

![image](https://user-images.githubusercontent.com/5994206/236574939-cac56abf-2c3e-4c47-952c-b5d0b55b0289.png)

# API Gateway
product-service port is updated as 0. When we start it, Eureka automatically assigns an available port, 54409, as it is seen in the below.

<img width="1295" alt="image" src="https://user-images.githubusercontent.com/5994206/236575417-ee1d1702-64a5-4876-aef4-5e31838f5dc4.png">

That shows this service is available via this port.

<img width="687" alt="image" src="https://user-images.githubusercontent.com/5994206/236575835-1c44bd38-4bf1-4b2e-b578-fecc32528384.png">


![image](https://user-images.githubusercontent.com/5994206/236576812-691cdf29-85bd-45c4-b626-a2b7a5c100b6.png)

We can use the following properties to use eureka server like this url: http://localhost:8080/eureka/web

## Discovery Server Route

spring.cloud.gateway.routes[2].id=discovery-server

spring.cloud.gateway.routes[2].uri=http://localhost:8761

spring.cloud.gateway.routes[2].predicates[0]=Path=/eureka/web

spring.cloud.gateway.routes[2].filters[0]=SetPath=/

We get eureka web page with plain html without static web resources like CSS, javascript.

![image](https://user-images.githubusercontent.com/5994206/236643252-479c2551-d84a-4198-9699-d6d263e5c893.png)

With this properties we get the page with html with static resources.

## Discovery Server Static Resources Route

spring.cloud.gateway.routes[3].id=discovery-server-static

spring.cloud.gateway.routes[3].uri=http://localhost:8761

spring.cloud.gateway.routes[3].predicates[0]=Path=/eureka/**

![image](https://user-images.githubusercontent.com/5994206/236643317-a78c0bcf-5913-4ebe-bc64-6659a53b2595.png)

## Circuit Breaker
After reaching 5 failed request, circuit breaker state is changed to "HALF_OPEN".

<img width="878" alt="image" src="https://github.com/galip/microservices/assets/5994206/3493eefa-a668-4297-94a8-ca64501af181">

