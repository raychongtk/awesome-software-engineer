# Backward Compatibility Thinking
Every software engineer should keep Backward Compatibility in mind during software development. If you want to provide a reliable service to others, you need to consider Backward Compatibility in your every change.

So, what is Backward Compatibility? Actually, Backward Compatibility is not that fancy. It is just a term to describe that old data should compatible with the new code.
>
>This short statement implies a lot of things:
>
>Why do we need to ensure old data compatible with new code?
>
>Why do we have old data in the system?
>
>What will happen if we don’t support backward compatibility?
>
>Is backward compatibility only affecting developers?

Can you answer these questions?

Why is backward compatibility so important to us especially building a product? The reason why we need to handle backward compatibility in our system is that there is a tricky moment exists during a deployment.

When the new code is up, it is supposed to receive the latest data no matter from the data store or from the API consumer. But it is just an ideal situation. In reality, the API consumers are sending old data according to the old API contract or the data has not been migrated after deploying the code. In this situation, you must provide backward compatibility in your code. Otherwise, your system will fail when accepting old data and it might cause unreliable API and loss of trust from others.

With backward compatibility provided, the system can:

- **Provide reliable API** to other consumers
- **Avoid system failure internally**, sometimes it is not API contract change but system logic/data change. We need to ensure our update is compatible with the previous version
- **Build customer trust** in your company

Let’s study a real scenario that happened in my project. Here is some context about the scenario.

We migrate new data to an existing database table which introduces more columns and the columns are part of the logic in the new code. Assume now we have A, B, C, D, and E columns. D and E are newly added.

We have a cache for the said data schema. Only A, B, and C are in the cache.

We deploy our code to production with new logic that depends on D and E. After deploying, the incoming requests failed.

![](../assets/resources/software-design/backward-compatible-0.png)

What? Why?

I started tracing our code and turns out I found that the problem happen because of caching. Here is the workflow of the code:
1. The app tries to get the data either from the cache or the database by using the Cache-aside pattern. (Cache Patterns)
2. The data exists in the cache and is read from the cache
3. Remember, we don’t have D and E in the cache 😨
4. We use D and E in our code for some logical decision and turns out it causes NullPointerException 😰😱

Imagine if your system needs to serve a large number of requests and now all the requests come and it fails. It can be terrible.😣 

> Now, you know where is the problem. Do you know how can we avoid this issue? Leave your thoughts in the comment section.

My takeaway from this accident:

- **As a code reviewer**, you might need to help think deeper when people introduce new fields into the existing data model.
- **As a developer**, you might need to think about any potential risks when introducing a new field. If you are not sure, maybe you can consult a more experienced developer.
- **As a tech leader**, you might need to help improve the skills of the whole team in order to understand the engineering fundamentals and summarize the failure and avoid the accident happen again.

Failure is not terrible but it is terrible if the same failure happens again and again. When there is any failure, fix it and summarize your failure and improve yourself.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>