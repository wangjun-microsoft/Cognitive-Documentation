<!--
NavPath: Bing Speech API/Speech Recognition/Client Library
LinkLabel: Get started in C#
Url: Speech-api/documentation/GetStarted/GetStartedCSharpDesktop
Weight: 6
-->

# Get started with Bing Speech Recognition and/or intent in C&#35; for .Net Windows
With Microsoft Speech Recognition Service Library, your service can utilize the power of Microsoft Speech transcription cloud to convert spoken language to text. This service-to-service library works in real-time so your client app can send audio to servers in the cloud and start receiving partial recognition results back simultaneously and asynchronously. For client library API reference, see the [Microsoft Bing Speech SDK](https://cdn.rawgit.com/Microsoft/Cognitive-Speech-STT-Windows/master/docs/SpeechSDK/index.html).

This article describes how to install, build, and run a C# example app. It also describes the basic concepts used to develop speech recognition services and advanced topics on buffering and connection management. 

### Table of Contents
*	[Install, Build, and Run the Example App](#Example)
*	[Speech Recognition Service Concepts](#Concepts)
 * [Preferences](#Preferences)
 * [Recognition Modes](#RecognitionModes)
 *	[Supported Audio Formats](#RecognitionModes)
 *	[Events](#Events)
 *	[Related Topics](#RelatedTopics)

<a name="Example">
## Install, Build, and Run the Example App
### Prerequisites
* #### Platform requirements
The below example has been developed for the .NET Framework using [Visual Studio 2015, Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs).
* #### Get the client library and example
You may download the Speech API client library and example through  [SDK](https://github.com/microsoft/cognitive-speech-stt-windows). The downloaded zip file needs to be extracted to a folder of your choice, many users choose the Visual Studio 2015 folder.
* #### Subscribe to Speech API and get a free trial subscription key
Before creating the example, you must subscribe to Speech API which is part of Microsoft Cognitive Services (previously Project Oxford). For subscription and key management details, see [Subscriptions](https://www.microsoft.com/cognitive-services/en-us/sign-up). Both the primary and secondary key can be used in this tutorial.

### Step 1: Install the example application
1.	Start Microsoft Visual Studio 2015 and click **File**, select **Open**, then **Project/Solution**.
2.	Browse to the folder where you saved the downloaded Speech API files. Click on **Speech**, then **Windows**, and then the **Sample-WPF** folder.
3.	Double-click to open the Visual Studio 2015 Solution (.sln) file named **SpeechToText-WPF-Samples.sln**. This will open the solution in Visual Studio.

### Step 2: Build the example application
1.	Press Ctrl+Shift+B, or click **Build** on the ribbon menu, then select **Build Solution**.

### Step 3: Run the example application
1.	After the build is complete, press **F5** or click **Start** on the ribbon menu to run the example.
2.	Locate the **Project Oxford Speech to Text** window with the **text edit box** reading **"Paste your subscription key here to start"**. Paste your subscription key into the text box as shown in below screenshot. You may choose to persist your subscription key on your PC or laptop by clicking the **Save Key** button. When you want to delete the subscription key from the system, click **Delete Key** to remove it from your PC or laptop.

![Speech Recognition paste in key](../Images/SpeechRecog_paste_key.PNG)
3.	Under **Speech Recognition Source** choose one of the six speech sources, which fall into two main input categories.
*  Using your computer’s microphone, or an attached microphone, to capture speech.
*  Playing an audio file.

There are example audio files to be used with this example application. You find the files in the repository you downloaded with this example under **SpeechToText**, in the **Windows** folder, under **samples**, in the **SpeechRecognitionServiceExample** folder. These example audio files will run automatically if no other files are chosen when selecting the **Use wav file for Shortphrase mode** or **Use wav file for Longdictation mode** as your speech input. Currently only wav and MP4 audio formats are supported.

![Speech to Text Interface](../Images/HelloJones.PNG)

<a name="Concepts"></a>
## Concepts

<a name="Preferences"></a>
###Preferences 
To create a SpeechClient, you need to first create a Preferences object. The Preferences object is a set of parameters that configures the behavior of the speech service. It consists of the following fields:
* SpeechLanguage: The locale of the audio being sent to the speech service.
* ServiceUri: The endpoint use to call the speech service.
* AuthorizationProvider: An IAuthorizationProvider implemetation used to fetch tokens in order to access the speech service. Although the sample provides a Cognitive Services authorization provider, it is highly recommended to create your own implementation to handle token caching.
* EnableAudioBuffering: An advanced option, please see Connection Management

<a name="RecognitionModes"></a>
### Recognition Modes
Each category has three recognition modes.
*  **ShortPhrase mode:** an utterance up to 15 seconds long. As data is sent to the server, the client will receive multiple partial results and one final multiple N-best choice result.
*  **LongDictation mode:** an utterance up to 2 minutes long. As data is sent to the server, the client will receive multiple partial results and multiple final results, based on where the server indicates sentence pauses.
*  **Intent detection:** The server returns additional structured information about the speech input. To use Intent you will need to first train a model. See details [here](https://www.luis.ai/).

<a name="SupportedFormats"></a>
### Supported Audio Formats
Supported Audio formats
The Voice API supports audio/wav using the following codecs: 
* PCM single channel
* Siren 
* SirenSR

<a name="Events"></a>
### Events
* #### Partial Results Event:
This event gets called every time the Speech Recognition Server has an idea of what the speaker might be saying – even before he or she has finished speaking (if you are using the Microphone Client) or have finished transferring data (if you are using the Data Client).
* #### Intent Event:
Called on WithIntent clients (only in ShortPhrase mode) after the final reco result has been parsed into structured JSON intent.
* #### Result Event:
When you have finished speaking (in ShortPhrase mode), this event is called. You will be provided with n-best choices for the result. In LongDictation mode, the handler associated with this event will be called multiple times, based on where the server thinks sentence pauses are.

Eventhandlers are already pointed out in the code in form of code comments.

 **Return format** |  Description |
 ------|------
 **LexicalForm** |  This form is optimal for use by applications that need raw, unprocessed speech recognition results.
 **DisplayText**  |  The recognized phrase with inverse text normalization, capitalization, punctuation and profanity masking applied. Profanity is masked with asterisks after the initial character, e.g. "d***". This form is optimal for use by applications that display the speech recognition results to a user.
**Inverse Text Normalization (ITN) has been applied**  |  An example of ITN is converting result text from "go to fourth street" to "go to 4th st". This form is optimal for use by applications that display the speech recognition results to a user.
**InverseTextNormalizationResult**  | Inverse text normalization (ITN) converts phrases like "one two three four" to a normalized form such as "1234". Another example is converting result text from "go to fourth street" to "go to 4th st". This form is optimal for use by applications that interpret the speech recognition results as commands or perform queries based on the recognized text.
**MaskedInverseTextNormalizationResult**  |  The recognized phrase with inverse text normalization and profanity masking applied, but no capitalization or punctuation. Profanity is masked with asterisks after the initial character, e.g. "d***". This form is optimal for use by applications that display the speech recognition results to a user. Inverse Text Normalization (ITN) has also been applied. An example of ITN is converting result text from "go to fourth street" to "go to 4th st". This form is optimal for use by applications that use the unmasked ITN results but also need to display the command or query to the user.

<a name="RelatedTopics"></a>
Related Topics
* [Get Started with Bing Speech Recognition in C Sharp for .Net on Windows Phone 8.1](GetStartedCSharpWinPhone.md)
* [Get started with Bing Speech Recognition and/or intent in Java on Android](GetStartedJavaAndroid.md)
* [Get started with Bing Speech Recognition and/or intent in Objective C on iOS](Get-Started-ObjectiveC-iOS.md)
* [Get started with Bing Speech API in JavaScript](GetStartedJS.md)
* [Get started with Bing Speech API in cURL](GetStarted-cURL.md)
