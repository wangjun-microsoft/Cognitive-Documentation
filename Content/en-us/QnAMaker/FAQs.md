<!-- 
NavPath: QnA Maker
LinkLabel: FAQs
Url: QnAMaker/documentation/faqs
Weight: 86 
-->

# FAQs #
### Who are the target audience for the QnA Maker tool?
QnA Maker is primarily meant to provide a FAQ data source which you can query from your Bot/Application. Although developers will find this useful, content owners will especially benefit from this tool. QnA Maker is a completely no-code way of managing the content that powers your Bot/Application.

### How do I login to the QnA Maker Portal?
You can login with your [Microsoft account](https://www.microsoft.com/en-us/account/)..

### Is the QnA Maker Service free?
Yes, currently the QnA Maker tool is free to use. However, we do meter the usage per account. See the Subscription Keys section of the documentation for details.

### My URLs have valid FAQ content, but the tool cannot extract them. Why not?
It’s possible that the tool is not able to auto-extract QnA from valid FAQ URLs. In such cases, you have an option to copy-paste the QnA content in a txt and try ingesting it. Alternately, you can always editorially add content to your knowledge base.

### What format does the tool expect the file content to be?
We support two formats of files for ingestion.

	1.	Tsv: QnA contained in the format Question<Tab>Answer
	2.	Txt, Docx, Pdf: QnA contained as regular FAQ content, i.e. sequence of questions and answers.
	
### How large a knowledge base can I create?
Currently we have a limit of a 20MB knowledge base.

### The updates I made to my knowledge base are not reflected on publish. Why not?
Every edit operation, whether in Table update, Test or Settings needs to be saved before it can be published. Make sure you press the Save and retrain button after every edit operation.

### What is the roadmap of the QnA Maker?
Currently the QnA Maker tool handles semi-structured FAQ content. Eventually the vision is to be able to answer questions from un-structured content as well.

### Do I need to use BotFramework to use the QnA Maker tool?
Not necessarily, however the QnAMaker is integrated seamlessly into Botframework as a QnA Bot Template. This makes is almost no effort to create an FAQ bot with Botframework.

### Why can’t I replace my Knowledge Base by the upload feature?
The format in which upload expect the file is Question<Tab>Answer<Tab>Source.

### When should I refresh my subscription keys?
You should refresh your subscription keys I you suspect that they have been compromised. Any requests with your subscription key will count towards your quota.