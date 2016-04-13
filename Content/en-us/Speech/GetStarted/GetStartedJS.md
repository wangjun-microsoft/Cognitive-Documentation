<!-- 
NavPath: Bing Speech API/Get Started with Speech API
LinkLabel: Get started with Speech Recognition and/or intent in JavaScript
Url: Speech-api/documentation/GetStarted/GetStartedJS
Weight: 100
-->

#Get Started with Bing Speech API in JavaScript

Develop a basic JavaScript application that uses Bing Speech Recognition API to convert spoken audio to text by sending audio to Microsoft’s servers in the cloud. The example below is a web application created in Visual Studio 2015 that demonstrates the use of Microsoft Cognitive Services (formerly Project Oxford) Speech To Text API using Javascript.  

The Speech Recognition web example demonstrates the following features using a wav file or external microphone input:
 * Short-form recognition
 * Long-form dictation
 * Recognition with intent
To use Speech.JS, simply host Speech.1.0.0.js on your website. A 'minified' version of Speech.JS is also available Speech.1.0.0.min.js.

### Table of Contents
*	[Prerequisites](#Prerequisites)
*	[Step 1: Install the example application](#Step1)
*	[Step 2: Build the example application](#Step2)
*	[Step 3: Run the example application](#Step3)
*	[Review and Learn](#Review)   
*	[Related Topics](#Related)

### <a name="Prerequisites">Prerequisites</a>
* #### Platform requirements
The below example has been developed for the .NET Framework using [Visual Studio 2015, Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs). 

* #### Get the client library and example
You may download the Speech API client library and example through  [GitHub](https://github.com/Microsoft/ProjectOxford-ClientSDK/tree/master/Speech/Speech.JS). The downloaded folder needs to be hosted locally on your machine to follow the below scenario.

* #### Subscribe to Speech API and get a free trial subscription key 
Before creating the example, you must subscribe to Speech API which is part of Microsoft Cognitive Services (previously Project Oxford). For subscription and key management details, see [Subscriptions](https://www.microsoft.com/cognitive-services/en-us/sign-up). Both the primary and secondary key can be used in this tutorial. 

### <a name="Step1">Step 1: Install the example application</a>
1.	Start Microsoft Visual Studio 2015 and click **File**, select **Open**, then **Project/Solution**.
2.	Browse to the folder where you saved the downloaded Speech.JS files. Click on **Speech** and then the **Speech.JS**folder.
3.	Double-click to open the Visual Studio 2015 Solution (.sln) file named **Oxford.Speech.JS.sln**. This will open the solution in Visual Studio.

### <a name="Step2">Step 2: Build the example application</a>
1.	Press Ctrl+Shift+B, or click **Build** on the ribbon menu, then select **Build Solution**.

### <a name="Step3">Step 3: Run the example application</a>
1.	After the build is complete, choose the target browser you would like to use for running your Speech-to-Text web app. 
2.	Press **F5** or click **Start** on the ribbon menu to run the example.  
3.	Locate the **Cognitive Services Speech to Text** window with the **text edit box** reading **"Subscription Key"**. Paste your subscription key into the text box as shown in below screenshot. You may choose to persist your subscription key on your PC or laptop by clicking the **Save Key** button. When you want to delete the subscription key from the system, click **Delete Key** to remove it from your PC or laptop.





4.Choose the target browser you would like to use.



1."Debug" to launch the sample app.

Running the sample

1.In the web application, enter your Microsoft Cognitive Services (formerly Project Oxford) Speech subscription key under "Oxford Key".


2.Select whether you would like to use the Microphone and what speech mode you would like to use by select "Use Microphone" and the "Mode" drop down box.


3.For modes where you would like both Speech recognition and Intent to work, you need to sign up Language Understanding Intelligent Service (LUIS) and set the key values in the fields "Luis AppID" and "LUIS SubscriptionId".


4.To Start recognition, press the Start button.




Contributing

We welcome contributions and are always looking for new SDKs, input, and suggestions. Feel free to file issues on the repo and we'll address them as we can. You can also learn more about how you can help on the Contribution Rules & Guidelines.

For questions, feedback, or suggestions about Microsoft Cognitive Services, feel free to reach out to us directly.
• Cognitive Services UserVoice Forum

License

All Microsoft Cognitive Services SDKs and samples are licensed with the MIT License. For more details, see LICENSE.

Sample images are licensed separately, please refer to LICENSE-IMAGE.


Status
 API
 Training
 Shop
 Blog
 About
   © 2016 GitHub, Inc.
 Terms
 Privacy
 Security
 Contact
 Help
 
