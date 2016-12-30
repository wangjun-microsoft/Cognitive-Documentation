<!-- 
NavPath: Computer Vision API/Quick Starts
LinkLabel: Overview
Url: Computer-Vision-API/documentation
Weight: 1000
-->

# Computer Vision JavaScript Quick Starts
This article provides information and code samples to help you quickly get started using JavaScript and the Vision API. With the Vision API you can:
* [Analyze an image](#AnalyzeImage) 
* [Intelligently generate a thumbnail](#GetThumbnail)
* [Get a description of an image](#GenerateDescription)
* [Detect and extract text from an Image](#OCR)

## Analyze an Image With Computer Vision API Using JavaScript <a name="AnalyzeImage"> </a>
Analyze images to obtain:
* The category defined in this [taxonomy](https://www.microsoft.com/cognitive-services/en-us/Computer-Vision-API/documentation/Category-Taxonomy). 
* A detailed list of tags related to the image content. 
* A description of image content in a complete sentence. 
* The coordinates, gender and age of any faces contained in the image.
* The ImageType (clipart or a line drawing)
* The dominant color, the accent color, or whether an image is black & white.
* Whether the image contains pornographic or sexually suggestive content. 

#### Analyze an Image JavaScript Example
```javascript
<html>
<head>
    <title>JSSample</title>
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
</head>
<body>

<script type="text/javascript">
    $(function() {
        var params = {
            // Request parameters
            "visualFeatures": "Categories",
            "details": "{string}",
            "language": "en",
        };
      
        $.ajax({
            url: "https://api.projectoxford.ai/vision/v1.0/analyze?" + $.param(params),
            beforeSend: function(xhrObj){
                // Request headers
                xhrObj.setRequestHeader("Content-Type","application/json");
                xhrObj.setRequestHeader("Ocp-Apim-Subscription-Key","{subscription key}");
            },
            type: "POST",
            // Request body
            data: "{body}",
        })
        .done(function(data) {
            alert("success");
        })
        .fail(function() {
            alert("error");
        });
    });
</script>
</body>
</html>
```

## Get a Thumbnail with Computer Vision API Using JavaScript <a name="GetThumbnail"> </a>
Intelligently generate a thumbnail based on an image's region of interest (ROI). 

#### Get a Thumbnail JavaScript Example

* Enter the Height and Width desired for the cropped image.
* Enter the [Subscription Key](https://www.microsoft.com/cognitive-services/en-us/Computer-Vision-API/documentation/vision-api-how-to-topics/HowToSubscribe)
* Enter the image URL; for example: {"url":"http://example.com/images/test.jpg"}

```javascript
<html>
<head>
    <title>JSSample</title>
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
</head>
<body>

<script type="text/javascript">
    $(function() {
        var params = {
            // Request parameters
            "width": "{number}",
            "height": "{number}",
            "smartCropping": "true",
        };
      
        $.ajax({
            url: "https://api.projectoxford.ai/vision/v1.0/generateThumbnail?" + $.param(params),
            beforeSend: function(xhrObj){
                // Request headers
                xhrObj.setRequestHeader("Content-Type","application/json");
                xhrObj.setRequestHeader("Ocp-Apim-Subscription-Key","{subscription key}");
            },
            type: "POST",
            // Request body
            data: "{body}",
        })
        .done(function(data) {
            alert("success");
        })
        .fail(function() {
            alert("error");
        });
    });
</script>
</body>
</html>
```
#### Get a Thumbnail Response
* A successful response contains the thumbnail image binary. 
* If the request fails the response contains an error code and a message to help determine what went wrong.


## Generate a Description Using JavaScript <a name="GenerateDescription"> </a>
Generate a description of an image in human readable language with complete sentences.

#### Generate a Description JavaScript Example 
```javascript
<html>
<head>
    <title>JSSample</title>
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
</head>
<body>

<script type="text/javascript">
    $(function() {
        var params = {
            // Request parameters
            "maxCandidates": "1",
        };
      
        $.ajax({
            url: "https://api.projectoxford.ai/vision/v1.0/describe?" + $.param(params),
            beforeSend: function(xhrObj){
                // Request headers
                xhrObj.setRequestHeader("Content-Type","application/json");
                xhrObj.setRequestHeader("Ocp-Apim-Subscription-Key","{subscription key}");
            },
            type: "POST",
            // Request body
            data: "{body}",
        })
        .done(function(data) {
            alert("success");
        })
        .fail(function() {
            alert("error");
        });
    });
</script>
</body>
</html>
```
#### Generate a Thumbnail Response
* Successful response
* Error response

## Optical Character Recognition (OCR) <a name="OCR"> </a>
Optical Character Recognition (OCR) detects text in an image and extracts the recognized characters into a machine-usable character stream


