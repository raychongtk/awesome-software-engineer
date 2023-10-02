# Architecture Mystery
Working as a software engineer, you might always hear people talking the word “architecture”. But, what is architecture? I think the first word that comes into your mind is microservices architecture.

Of course, microservice is an architectural pattern. But it is too vague. When talking about architecture, usually, we can refer to different granularities and layers, roughly including:

- System
- Subsystem
- Module
- Function

With these layers in mind, we can describe architecture from different angles. The example below explains the architecture of a supply chain system in different granularities.

![](../assets/resources/architecture/architecture-mystery-1.png)

## System
System level architecture describes the system as a whole. At this level, we can see all subsystems are listed and their dependencies. For example, a supply chain system might have an API Platform, Supply Chain Visualization, User, Transaction, Trade Item, and so on. All these subsystems together form the supply chain system.

## Subsystem
Subsystem level architecture describes the subsystem capabilities and what modules the system provided. As you can see, System and subsystem levels are quite similar. The difference between them is the granularity.

## Module
Module level describes the actual functionalities that the subsystem provided.

## Function
Function level describes the actual code implementation for the functions.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>