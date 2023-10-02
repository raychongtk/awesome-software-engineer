# Redeisn Your Development Workflow with Mock Service
Today, I will be sharing the idea of a Mock Service in the software development workflow.

It is common that a system to integrate with third-party providers such as payment and communication providers. In normal architecture, a service connects to a provider directly in different environments.

![](../assets/resources/architecture/mock-service-1.png)

## What are the problems in this architecture?

- **Unable to test the error use cases from providers** - Your app cannot test unexpected responses under this architecture because you do not have the right to control the third-party provider.

- **Unable to have end-to-end automated tests** - Your app does not have the capability to test different behaviors with a real provider.

To tackle the listed problems, a mock provider is introduced into the architecture.

![](../assets/resources/architecture/mock-2.png)

This approach allows developers to test and verify the app's behavior in a controlled environment before deploying it to the production environment. The mock provider is designed to respond to requests in the same way as a real provider would, allowing developers to test error cases and edge cases that might not occur during normal operation. By simulating different scenarios, developers can ensure that the app behaves as expected under different conditions, reducing the risk of bugs and issues in production.

## What benefits does this architecture bring to you?

- **Empower developers to test different behaviors** - With a mock provider, we can create our own test assets to mock different behaviors, and that enables developers or QA to run a complete test for different scenarios before rolling out.

- **Enable end-to-end automated tests** - A mock provider can facilitate end-to-end automated tests to ensure the latest code does not break the existing behaviors. We can control the percentage of success or failure rate to cover different scenarios. With end-to-end tests, we can promote refactoring culture in the team and help developers build confidence in shipping code. Also, if there is anything broken, we can send an alert to notify developers.

- **Simulate Chaos** - With the mock service, we can randomly inject chaos into the mock provider to verify whether our services can handle the chaos properly.

## Conclusion
To sum up, integrating with third-party providers in a system is common and it might have different problems during the integration such as hard to simulate unexpected behaviors. By introducing a mock provider to the system architecture, developers can verify the API behaviors in a controlled environment, test different scenarios and error cases, and reduce the dependencies on third-party providers. With that, developers and QA can test whatever they want by simulating the behaviors of a real provider.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>