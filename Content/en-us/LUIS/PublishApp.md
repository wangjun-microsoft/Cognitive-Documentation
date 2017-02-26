<!-- 
NavPath: LUIS API
LinkLabel: PublishApp
Url: LUIS-api/documentation/home
Weight: 81
-->

#Publish your app
When you finish building and testing your app, you can publish it as a web service. Also, if you make significant changes to your app make sure to re-publish.

**Before you publish, make sure to:**

* Assign a subscription key to your app, otherwise you’ll not be able to publish. For information on how to set up and manage Azure subscription keys, see [Manage your keys](Manage-Keys.md).

* (Optional) It would be better to test your app before publishing it. For instructions, see [Train and test your app](Train-Test.md).

* Train your app by clicking the **Train** button on the **Publish App** page. 


##Publish your app as a web service
You can publish your app to an HTTP endpoint to make it available as a web service that interprets the sentences sent to it. 

**To publish your app as a web service:**

1. Open your app (e.g. TravelAgent) by clicking its name on **My Apps** page, and then click **Publish App** in your app's left panel.
![Train before publishing](/Content/en-us/LUIS/Images/PublishApp-TrainFirst.JPG)
2. In the **Publish App** page, click **Train** (if the app wasn't trained already).
![Publish your app](/Content/en-us/LUIS/Images/PublishApp-enabled.JPG)
3. Click **Publish**. After few moments, the endpoint URL of your published app will be displayed.  
![Application Published to HTTP endpoint](/Content/en-us/LUIS/Images/PublishApp-URL.JPG)

 > **Note:**
> If the **Publish** button is disabled, then either your app does not have an assigned subscription key, or you have not trained your app yet.

To test how your published app works, you can access the test console by clicking **Train & Test** in the left panel. For instructions on how to test your app using the test console, see [Train and test your app](Train-Test.md).

If you want to test your published endpoint in a browser using the generated URL, you can click the URL to open it in your browser, then set the URL parameter "&q" to your test query (for example: "&q=Book me a flight to Boston on May 4"), and then press Enter. You will get the JSON response of your HTTP endpoint. 
![JSON response of published HTTP endpoint](/Content/en-us/LUIS/Images/PublishApp-JSONresponse.JPG)
