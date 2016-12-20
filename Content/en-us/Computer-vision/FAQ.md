<!-- 
NavPath: Computer Vision API
LinkLabel: Frequently Asked Questions
Url: Computer-Vision-API/FAQ
Weight: 50
-->

# Computer Vision API Frequently Asked Questions

### Question: 
The Computer Vision API offers at least two ways of obtaining tags for an image. According to the documentation there's a list of tags for "description", as well as a top level "tags" list. The "tags" list additionally contains confidence-levels, the "description tags" list does not. However, the description tag list seems to be much more exhaustive than the top level tags list, usually showing 5 to 10 times as many tags. Why are there two different lists of tags and what's the use case for each list? Also, is there a reason why the description-tags list shows way more tags than the top-level tags list? 
### Answer:
Although the list is similar today, there is no guarantee for now or for the future that these lists remain this way. The idea for the tags inside the description was to give API users an option to construct a sentence of their liking using these tags if the confidence for the natural-language sentence was low.

**Note:** In both the tags and description.tags cases, the terms are in descending confidence order.

---

### Question:
When calling postAsync with particular image url, I get the below error in json response.
"Invalid image URL or error downloading from target server. Remote server error returned: "An error occurred while sending the request.""
The image URL is http://localhost:3942/WebImages/test1.jpg
### Answer:
When you make a request to the Cognitive Service API with an image URL as you've specified, you're instructing the service running in the cloud to load the image from that location. The service cannot locate your localhost, hence the error.

You have two options: (a) if your image is already available at a public-reachable URL, use the URL instead. If you're unsure whether the URL is publicly reachable, try entering it in a browser on your phone, for example. Alternatively, (b) Upload the image in the HTTP request body. You'll need to also set the MediaTypeHeaderValue to application/octet-stream.

If you're using a managed language (like C#) with Visual Studio, consider using the [NuGet](https://www.nuget.org/packages/Microsoft.ProjectOxford.Face) package. This will take care of the details for you. The source for that NuGet package is on [GitHub](https://github.com/Microsoft/Cognitive-Face-Windows/tree/master/ClientLibrary)

---

