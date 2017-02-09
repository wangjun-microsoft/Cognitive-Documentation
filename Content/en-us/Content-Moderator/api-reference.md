<!-- 
NavPath: Content Moderator
LinkLabel: API Reference
Url: content-moderator/documentation/api-reference
Weight: 130
-->

# API Reference #

## Review API ##
When you sign up for the [human review tool](http://contentmoderator.cognitive.microsoft.com/ "Content Moderator Review Tool"), you can use the review API key available within the review tool, to integrate your content in bulk. The review API will internally use the image and text moderation APIs to scan your images or text, and create reviews in the review tool to be available for human oversight.

[**Review API**](https://westus.dev.cognitive.microsoft.com/docs/services/580519463f9b070e5c591178/operations/580519483f9b0709fc47f9c5 "Content Moderator Review API")

## Image and Text Moderation APIs ##
The imagea and text moderation APIs scan your content and send the results with relevant information either back to your systems or to the built-in review tool (for images), depending on who is calling the API. You can use this information to implement your own post-moderation workflow such as publish, reject, or review.

You can sign up to try the image and text moderation APIs for free (5K transactions per month) in two ways. Either [subscribe to the Content Moderator API](https://portal.azure.com/#create/Microsoft.CognitiveServices/apitype/ContentModerator) on the Azure portal or sign up for the online [review tool](http://contentmoderator.cognitive.microsoft.com/). In the latter case, you will find your content moderator API credentials listed on the Settings screen in the review tool.

[**Image and Text Moderation APIs**](https://westus.dev.cognitive.microsoft.com/docs/services/57cf753a3f9b070c105bd2c1/operations/57cf753a3f9b070868a1f66c "Image and Text Moderation APIs")

## List Management API ##
Use this API to create and manage your custom lists of Images and Text. The lists that you create can be used in the **Image/Match** and **Text/Screen** operations. You can use your Moderate API credentials for the list management API as well.

[**List Management API**](https://westus.dev.cognitive.microsoft.com/docs/services/57cf755e3f9b070c105bd2c2/operations/57cf755e3f9b070868a1f675 "Content Moderator List Management API")
