# Pub/Sub Practical Guide: Use Case
The Pub/Sub pattern is widely used in large complex architecture and serves different purposes. In this article, I will summarize the scenarios in that a message queue can be applied.

## Decouple service dependency and Asynchronous

To understand how Pub/Sub architecture benefit to this scenario, it is necessary to study a little about the architecture without Pub/Sub.

![](../assets/resources/architecture/order-creation-1.png)

In this architecture, Order Service is tightly coupled with the other 3 services by invoking APIs. It causes 3 problems:

- Order Service needs to have a code change if now we don’t need to depend on Statistics Service
- The other 3 services’ response times are all accumulated to the Order Service response time
- Order Service needs to handle service unavailable issues for its dependencies

Now, how does Pub/Sub solve these problems?

![](../assets/resources/architecture/decouple-service-dependency-1.png)

We change the architecture to include Pub/Sub. Now, the Order Service will always publish an event if there is a new order. Interested parties subscribe to the topic and handle the event with their own logic.

If the statistics service no longer cares about order creation, it can remove the subscription and the order service does not change any code.

Since it is asynchronous now, the response times from other services will not accumulate to the Order Service and also the Order Service no longer needs to handle service unavailable issues for its dependencies, instead, it will be handled by the Pub/Sub.

> Can you guess what are the problems here after we adopt Pub/Sub architecture? Leave your thoughts in the comment below

## Avoid service being overwhelmed

Pub/Sub can also avoid overwhelming a service. Imagine we have 5K requests per second at peak hours and the notification service can only process 3K requests per second. If we allow the service to process all requests simultaneously, it will overwhelm the service.

![](../assets/resources/architecture/overwhelmed-1.png)

By introducing Pub/Sub, we can temporarily store the requests in the message broker and consume the messages later. With this design, we can also have a stable consumption rate and avoid service overwhelming. In off-peak hours, the traffic is low and we can consume message backlog steadily.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>