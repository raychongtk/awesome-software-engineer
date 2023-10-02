# Cache Delete Strategy of Cache-aside Pattern
In the cache patterns post, I asked a question:
>Do you know why we don’t remove the cache key first and write to the database afterward?

Here is the reason why we don’t do this.

## ❌ Delete the cache before updating the database:

![](../assets/resources/cache-patterns/cache-delete-1.png)

According to the diagram above, it is obviously a dirty read that happened in steps 4 to 6. As you can see, we perform step 3 to delete the cache and now a Read request comes and found that the cache is missing. So, it performs an action to read the data from the database and set the data back to the cache.

Since the Write request is not finished yet and the Read request runs faster than the Write request so a data inconsistency problem happens in the cache. The subsequent requests will be reading the staled data from the cache since there is no action to remove the cache until the next Write.

To mitigate the data inconsistency problem, we can update the workflow to the following sequence.

## ✅ Delete the cache after updating the database:

![](../assets/resources/cache-patterns/cache-delete-2.png)

Now, the workflow is updated. As you can see in the diagram above, we perform a database update first and clear the cache afterward. 

Under this flow, the Write request can delete the cache even if the Read request set the stale data into the cache. The subsequent requests will be reading the correct data from the cache. But, there is still a problem in steps 2 to 5 which is related to the execution sequence. 

If step 5 runs faster than step 4 (set cache), it will cause the data inconsistency problem again. But, it is less chance to have this problem in most of the use cases.

Also, when adopting a cache strategy, we always need to have a reasonable expiry time to deal with the data inconsistency problem. We are not designing a strongly consistent system, so a little bit of data inconsistency is acceptable in most of the use cases.

<br>
<center>
<style>.bmc-button img{width: 27px !important;margin-bottom: 1px !important;box-shadow: none !important;border: none !important;vertical-align: middle !important;}.bmc-button{line-height: 36px !important;height:37px !important;text-decoration: none !important;display:inline-flex !important;color:#ffffff !important;background-color:#262626 !important;border-radius: 3px !important;border: 1px solid transparent !important;padding: 1px 9px !important;font-size: 23px !important;letter-spacing: 0.6px !important;box-shadow: 0px 1px 2px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;margin: 0 auto !important;font-family:'Cookie', cursive !important;-webkit-box-sizing: border-box !important;box-sizing: border-box !important;-o-transition: 0.3s all linear !important;-webkit-transition: 0.3s all linear !important;-moz-transition: 0.3s all linear !important;-ms-transition: 0.3s all linear !important;transition: 0.3s all linear !important;}.bmc-button:hover, .bmc-button:active, .bmc-button:focus {-webkit-box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;text-decoration: none !important;box-shadow: 0px 1px 2px 2px rgba(190, 190, 190, 0.5) !important;opacity: 0.85 !important;color:#ffffff !important;}</style><link href="https://fonts.googleapis.com/css?family=Cookie" rel="stylesheet"><a class="bmc-button" target="_blank" href="https://www.buymeacoffee.com/raychongtk"><img src="https://www.buymeacoffee.com/assets/img/BMC-btn-logo.svg" alt="Buy me a coffee"><span style="margin-left:5px">Buy me a coffee</span></a>
</center>