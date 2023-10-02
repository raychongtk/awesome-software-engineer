# Consistency and Availability
When talking about Consistency and Availability, data replication is one of the topics that we can discuss.

Data replication is one of the ways to increase availability. The more you replicate, the higher availability. Conversely, the more you replicate, the less consistent. 

In most systems, we prefer availability over consistency. If the system is not available, then no matter how consistent it is, people will not use it. Instead, if the system is highly available with a good user experience, even if we sacrifice a little bit of data consistency, people will still love it.

To further discuss this topic, let’s take the following scenario as an example. Imagine we are working on a heavy-read system. Now, A service is the data provider for B, C, D, and E services.

## Embrace Consistency

In a consistency system, every time when we read A service’s data in B, C, D, and E services, they need to invoke A service to get the necessary data.

> What if now A service is down? We can’t read the necessary data anymore and B, C, D, and E services are all gone too.

If we change the design a little bit, the output will be totally different.

## Embrace Availability

![](../assets/resources/architecture/availability-1.png)

In this design, we get the necessary data from A service first when writing data for B, C, D, and E services. 

Now, moving to read data scenario. Since we already have a copy of A’s data, B, C, D, and E services do not need to invoke A service to get the data anymore.

> What if A service is down? It will only affect the writing data scenario but the reading data scenario will still be functioning. In a heavy-read system, this design helps a lot. When reading data, we don’t need to depend on the data provider. Also, A service does not have to handle the read traffic from B, C, D, and E services.

### What’s the trade-off for this design?

- More storage is needed for the data copy
- Data inconsistent when the data in A service is updated

Compared to the impact that the first design bring to us, the trade-off of the second design seems reasonable and we can tolerate it in most scenarios.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>