<!-- 
NavPath: Custom Speech Service
LinkLabel: Frequently Asked Questions
Url: Custom-Speech-Service/documentation/GetStarted
Weight: 10
-->
# Custom Speech Service Frequently Asked Questions
##### If you can't find answers to your questions in this FAQ, try asking the Custom Speech Service community on [StackOverflow](https://stackoverflow.com/questions/tagged/project-oxford+or+microsoft-cognitive) and [UserVoice](https://cognitive.uservoice.com/) 

-----

**Question**: Can I update my existing model (model stacking)

**Answer**: We do not offer the ability to update an existing model with new data. 
* If you have a new data set and you want to customize an existing model you must re-adapt it with the new data and the old data set that you used.
* The old and new data sets must be combined in a single .zip (if it is acoustic data) or a .txt file if it is language data
* Once adaptation is done the new updated model needs to be de-deployed to obtian a new endpoint

**Question**: What if I need higher concurrency than what either Tier1 or Tier 2 offer

**Answer**: Tier1 offers up to 4 concurrent requests and Tier2 up to 12. 
* Please contact us if you require higher than that.

**Question**: Can I download my model and run it locally

**Answer**: We do not enable models to be downloaded and executed locally.

**Question**: Are my requests logged?
**Answer**: Requests are typically logged in Azure in secure storage. 
* If you have privacy concerns that prohibit you from using the Custom Speech Service please contact us and we can discuss logging/tracing alternatives.

-----
