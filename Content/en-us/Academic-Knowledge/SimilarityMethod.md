<!-- 
NavPath: Academic Knowledge API
LinkLabel: Similarity Method
Url:Academic-Knowledge-API/documentation/SimilarityMethod
Weight: 75
-->

# Similarity Method

The **similarity** REST API is used to calculate the academic similarity between two texts. 
<br>

**REST endpoint:**
```
https://api.projectoxford.ai/academic/v1.0/similarity?
```

## Request Parameters
Parameter        |Data Type      |Required | Description
----------|----------|----------|------------
**s1**        |String   |Yes  |String to be compared
**s2**        |String   |Yes  |String to be compared
<sub>
GET requests' input length is bounded by URL length limitation.
<br>
POST requests have a input string length limitation of 1MB.
</sub>
<br>
## Response
Name | Description
--------|---------
**SimilarityScore**        |A floating point value between -1.0 to 1.0 representing the cosine similarity of between text input s1 and s2 with 1.0 being the most similar and -1.0 being the least similar
<br>

## Success/Error Conditions
HTTP Status | Reason | Response
-----------|----------|--------
**200**         |Success | Floating point number
**400**         | Bad request or request invalid | Error message      
**500**         |Internal server error | Error message
**Timed out**     | Request timed out.  | Error state
<br>

**Example:**
```
https://api.projectoxford.ai/academic/v1.0/similarity?s1=Using complementary priors, we derive a fast greedy algorithm that can learn deep directed belief networks one layer at a time, provided the top two layers form an undirected associative memory&s2=Deepneural nets with a large number of parameters are very powerful machine learning systems. However, overfitting is a serious problem in such networks
```
In this example, we generate the similarity score between two partial abstracts using the **similarity** API.
```
0.520
```
The score is deteremined by assessing the academic concepts through word embedding and vectors. In this example, 0.52 represents that the two partial abstracts are somewhat relevant. 
<br>
