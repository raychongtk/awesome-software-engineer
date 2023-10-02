# Payment Event-driven Architecture
Event Driven Design is a popular architectural style and has many benefits if you are building a complex system, especially building a state transitions workflow.

Let’s take the payment order workflow as an example. An order has many states like Pending, Assigned, Processing, Failed, Paid, and Completed. When the order is placed in the system, it will be Pending. After that, the order will be Assigned to one of the payment channels. The status will become Processing when the payment request sends to a third-party gateway. It will be either Failed or successfully Paid when the third-party gateway returns the result to us. Finally, we need to send a callback to our client to complete the order, it will be Completed at this stage.

![](../assets/resources/architecture/payment-event-arch-1.png)

With the requirements above, we can break down the problem into different parts.

1. Handling order creation
2. Assigning payment channel to new orders
3. Sending payment requests to third-party vendors
4. Updating order status and making sure the status sequence
5. Sending callbacks to clients

Okay, so how do we utilize Event Driven Design to help us archive the above goals?

Before talking about Event Driven Design, let's think about the request-response pattern first. Probably it will be something like the one below. Let Order Service orchestrate the order workflow and use direct HTTP calls to invoke other services. (Or Order Service invokes Payment Service, and Payment Service invokes Payment Channel Allocation Service.)

![](../assets/resources/architecture/payment-event-arch-2.png)

When the payment provider callback the Payment Service, it needs to invoke Order Service to update the status.

What are the problems in this architecture? Think about it. Leave your thoughts in the comment section.

With the event-driven design, the architecture might look like the below diagram:

![](../assets/resources/architecture/payment-event-arch-3.png)

Introduce different event topics in the architecture, like order-created for notifying other subscribers that a new order is available in the system. Once subscribers receive a new order created event from the topic, they can do their own job accordingly. For example, the Payment Gateway Allocation Service might need to allocate a payment channel to a new order. 

After that, the Payment Gateway Allocation Service might further publish another event payment-channel-allocated to tell its subscribers that a new order with an allocated payment channel is now available to consume. The Payment Service will then fetch the allocated order from the topic and consume it.

When Payment Service sends the order to third-party providers, it will publish an order-updated event to tell subscribers a payment order is updated.

In this workflow, the Order Service does not need to talk to the Payment Gateway Allocation Service directly and the Payment Gateway Allocation Service does not need to talk to the Payment Service too. Instead, they communicate with each order through events.

In this architecture, when a new payment order is submitted to the system, it is like telling everyone there is a new event about order creation, if you care about order creation, please do your own handling. That said, the upstream services do not need to care about how the downstream service handles the logic after order creation.

What are the benefits of using this architecture?

- Decouple service dependency
- Better availability and scalability

> Can you tell me any drawbacks of event-driven design? Leave comments below to share your thoughts.
>
> <br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>