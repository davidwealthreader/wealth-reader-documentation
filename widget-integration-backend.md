---
description: Actions to be taken by the backend team
---

# 👩‍💻 Widget integration: backend

This section should follow the frontend checklist. The steps are as follows

* [ ] **Create the callback URL**\
  Create a callback URL in your environment where Wealth Reader will send the data obtained through the widget.\
  This URL must be able to receive POST requests with a JSON body.\
  To confirm that the data has been received correctly, your endpoint must respond with HTTP 200 and the following body:

```json
{
    "status": "ok"
}
```

*   [ ] **Associate the domain, the callback URL and the API key**\
    From the Wealth Reader clients area, associate:

    * the domain from which the widget will be loaded;
    * the callback URL where you will receive the data;
    * your `api_key`.\
      \
      You can do this at: [https://www.wealthreader.com/clients/](https://www.wealthreader.com/clients/)


* [ ] To test the full flow, open the page that loads the widget that your front-end partner has created and enter real data or use one of the mock users that we have provided in the welcome email. If you do not have this email, please request it from support@wealthreader.com.
* [ ] Up to this point, you have completed the integration in a "one shot" use case, where no data refreshes are needed. If your use case requires refreshing the information, either through a nightly batch process, or by offering a refresh button to the end user, you will need to call the Wealth Reader API again with the obtained data. To do this, use the following documentation, paying particular attention to error code handling:
  * [ ] API Specification [OpenAPI V3](https://www.wealthreader.com/api-reference/en/).

{% hint style="info" %}
If you have any difficulty programming the callback URL and want to locate the cause of the problem, you may want to create a callback URL in a service such as https://pipedream.com/.
{% endhint %}
