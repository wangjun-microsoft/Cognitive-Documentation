<!-- 
NavPath: Content Moderator
LinkLabel: Get Started
Url: content-moderator/documentation/quickstart
Weight: 190
-->

# Get Started #
Start by signing up for the [review tool](http://contentmoderator.cognitive.microsoft.com/ "Content Moderator Review Tool") and uploading images to explore the automated moderation and review the  results right within your web browser. 

Also read: [Review Tool User Guide](review-tool-user-guide/why.md)

You can take actions such as changing the highlighted tags and submitting your decisions to the default workflow. You can then move on to using the review API to integrate your content (images) with the tool, and finally, use the underlying moderation APIs directly for automated moderation and custom list management.

## 1. Sign up for the review tool ##
Sign up to try the [review tool](http://contentmoderator.cognitive.microsoft.com/ "Content Moderator Review Tool") by either using your existing Microsoft account or create a new account within the review tool.

## 2. Invite team members ##
On the opening screen after signup, name your team, and optionally, invite your colleagues by entering their email addresses. You can see the status of existing invites, cancel pending invites, and after confirmation by the invited users, you can assign them the role of an administrator (like yourself) or of a reviewer.

![Invite team member](images/QuickStart-2-small.png)

## 3. Upload images ##
Use the File Upload feature to upload a set of sample images for moderation. These can be your images, subject to size and count restrictions. You will find a link to download the sample images on the File Upload screen.

![Upload files](images/QuickStart-3.PNG)

## 4. Submit for automated moderation ##
Submit your uploaded content to start the auto-moderation step. Internally, the review tool will call the moderation APIs to scan your content for built-in tags. Once the scanning is complete, you will see a message informing you about the results waiting for your review.

![Moderate files](images/QuickStart-4.PNG)

## 5. Review and confirm results ##
As your business application calls the Moderator [image API](image-moderation-api.md "Image Moderation API"), the tagged content will start queuing up, ready to be reviewed by the human review teams. You can quickly review large volumes of content using this approach. You will be doing a few different things as part of your moderation workflow such as:

- Adjusting the zoom level
- Browsing the reviews on-screen
- Reviewing moderation scores and results
- Confirming or modifying the tags returned by the API

![Review results](images/QuickStart-5.PNG)
