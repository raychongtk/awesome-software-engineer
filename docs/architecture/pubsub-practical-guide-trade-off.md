# Pub/Sub Practical Guide: Trade-off
Pub/Sub makes an architecture to be resilient to failures and increases system availability in a high-traffic situation. But, it also brings us several drawbacks. In this article, I will walk you through the potential drawbacks of Pub/Sub architecture.

Applying Pub/Sub architecture to a system might have the following trade-offs:

## Latency

![](../assets/resources/architecture/pubsub-latency-1.png)

Introducing a Pub/Sub to a system will increase latency. The diagram shows the difference between direct connection and indirect connection. Originally, Service 1 only communicate with Service 2 directly through REST or RPC. After applying Pub/Sub, the request is submitted to Message Broker first, and then wait for Service 2 to consume the messages. This introduces latency to the system and it will be obvious when traffic is high.

## Development Complexity

![](../assets/resources/architecture/pubsub-complexity-1.png)

Before applying Pub/Sub architecture, the development complexity between 2 services is HTTP request where HTTP client is common in any architecture, so we can ignore the complexity. Now, after introducing Pub/Sub to the system, we bring extra complexity to the architecture. Not every developer is familiar with Pub/Sub architecture in-depth. If there are any issues related to the Pub/Sub architecture, does anyone in the team know how to solve them? If not, it will bring unknowns to the architecture.

## DevOps Complexity

![](../assets/resources/architecture/pubsub-devops-1.png)

Bringing Pub/Sub to the system architecture also increase DevOps complexity. DevOps engineers need to manage the complexity that the Pub/Sub brings to the architecture including creating a cluster and managing topics and partitions. Without knowing the technology in-depth, it is hard to manage the complexity reasonably.

## Conclusion
To sum up, Pub/Sub is good but we still need to manage the complexity. By knowing the trade-off, we can make better decisions when creating an architecture. In general, applying Pub/Sub to architecture will bring latency, development complexity, and DevOps complexity to us, apply it wisely and consider the trade-offs to see if the team can pay for it.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>