# Design for Adaptability
Designing software architecture requires careful consideration of various factors to ensure its effectiveness. In this post, I will share some ideas for creating a software architecture that can adapt to different conditions and resources.

When designing architecture, there are several important aspects to consider:

## Team Resources

It is crucial to take into account the resources available within the team. Even with great architectural ideas, lack of resources can prevent successful execution. For example, a small team cannot build something as complex as Google. Therefore, the architecture design should align with the current team resources and the knowledge level of the engineers involved.

## Time-to-Market (TTM)

The architecture design should be mindful of the overall development time required to bring the product to market. If there are strict time constraints, it would not make sense to implement an architecture that requires significantly more time than available. TTM is a critical factor as it directly impacts revenue generation. If an architecture cannot adapt to this constraint, it should not be considered.

## Business Adaptation

The architecture design should be aligned with the current state of the business. For instance, companies like Airbnb started with a monolithic application and later evolved into microservices and a combination of micro and macroservices. By considering the business scope, the architecture can be tailored to meet the specific needs of the company. Designing an architecture for a significantly higher workload than the current demand would result in unnecessary investment and inefficiencies.

Airbnb Architecture Evolution:

- Monolith (2008 - 2017)
- Microservices (2017 - 2020)
- Micro + Macroservices (2020 - Present)

Ref: https://www.infoq.com/presentations/airbnb-culture-soa/

The evolution of Airbnb's architecture exemplifies how a large tech company adapts its architecture to align with its evolving business needs. As the business grows, the architecture evolves accordingly. This demonstrates the importance of periodically reassessing the existing architecture, removing outdated elements, and adapting it to meet new requirements.

## Conclusion
Creating an excellent architecture begins with establishing a solid foundation. While it's important to plan for future needs, it's equally essential to invest time wisely and prioritize current business demands. Predicting the future is challenging, and dedicating significant resources to shaping the architecture for hypothetical scenarios may not be efficient.

One might argue that designing for future scalability is necessary in order to become a successful company. While this is true, it's important to balance long-term goals with current priorities. The architecture can be designed with future scalability in mind, but implementing it immediately without actual business needs may not be the best approach. In a fast-growing company, it's crucial to allocate resources effectively and adapt the architecture when the business demands it.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>