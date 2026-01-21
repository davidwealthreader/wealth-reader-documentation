---
description: Actions to be taken by the backend team
---

# 👩‍💻 Widget integration: backend

This section should follow the frontend checklist. The steps are as follows

* [ ] Create the URL in your environment where you will receive the data retrieved by the widget.
* [ ] In the response body, to confirm that you have received the data correctly, include

```json
{
    "status": "ok"
}
```

*   [ ] Associate the domain where you load the widget with your callback URL and your api\_key:<br>

    ```json
    # Define variables
    API_KEY='12345678'
    DOMAIN='http://development.client.com'
    URL_CALLBACK='https://development.client.com/hooks/wealthreader'

    # Execute the curl command using the variables
    curl --location "https://api.wealthreader.com/domains/" \
    --header "Content-Type: application/x-www-form-urlencoded" \
    --data-urlencode "method=add" \
    --data-urlencode "tokenize=1" \
    --data-urlencode "api_key=${API_KEY}" \
    --data-urlencode "domain=${DOMAIN}" \
    --data-urlencode "url_callback=${URL_CALLBACK}"
    ```


* [ ] To test the full flow, open the page that loads the widget that your front-end partner has created and enter real data or use one of the mock users that we have provided in the welcome email. If you do not have this email, please request it from support@wealthreader.com.
* [ ] Up to this point, you have completed the integration in a "one shot" use case, where no data refreshes are needed. If your use case requires refreshing the information, either through a nightly batch process, or by offering a refresh button to the end user, you will need to call the Wealth Reader API again with the obtained data. To do this, use the following documentation, paying particular attention to error code handling:
  * [ ] API Specification [OpenAPI V3](https://www.wealthreader.com/api-reference/en/).

{% hint style="info" %}
If you have any difficulty programming the callback URL and want to locate the cause of the problem, you may want to create a callback URL in a service such as https://pipedream.com/.
{% endhint %}
