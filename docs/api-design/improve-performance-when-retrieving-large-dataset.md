# Improve Performance When Retrieving Large Dataset
In the realm of software development, backend systems store vast amounts of data, and it is the responsibility of software engineers to design APIs that retrieve this data from databases.

When dealing with small datasets, some novice engineers may design APIs that fetch all the data from the database in a single operation. This approach works fine with small data sizes since it doesn't lead to performance issues.

![](../assets/resources/api/api-pagination-1.png)

However, when the database contains millions of records, retrieving all the data in one go can result in slow query performance or even OOM. Slow API responses not only hinder user experience but also undermine the reliability of the API, potentially eroding customer trust.

![](../assets/resources/api/api-pagination-2.png)

To address this issue and improve performance, a recommended solution is to redesign the API using pagination.

![](../assets/resources/api/api-pagination-3.png)

In this enhanced design, a large dataset is divided into smaller chunks, and the data is retrieved incrementally using pagination. For instance, the first API call fetches the first 8 records from the initial page. If users need to access the second page, another API call is made to retrieve that specific page.

![](../assets/resources/api/api-pagination-4.png)

By adopting this approach, the API retrieval performance can be optimized. In contrast to the previous method, which retrieved the entire dataset at once, the improved design fetches only 8 records per API call, effectively controlling the data size and enhancing performance.

> 💡 Do you know what’s the hidden performance issue with using this type of pagination? Share your thoughts in the comment section!

In summary, pagination is a technique that divides large datasets into manageable pages, improving retrieval performance, controlling data size, and enhancing the user experience when dealing with substantial amounts of data.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>