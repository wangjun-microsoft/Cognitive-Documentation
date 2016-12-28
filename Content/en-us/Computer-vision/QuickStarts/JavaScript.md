<!-- 
NavPath: Computer Vision API/Quick Starts
LinkLabel: Overview
Url: Computer-Vision-API/documentation
Weight: 1000
-->

# Computer Vision JavaScript Quick Starts
This article describes ... for quickly gettting started using JavaScript and the Vision API:
* [Generating a thumbnail](#GetAThumbnail)
* [Generating a description for an Image](#GenerateADescription)
* [Determining if an image contains adult content](#AdultContent) 

## Get a Thumbnail Using JavaScript <a name="GetAThumbnail"> </a>
Intelligently generate a thumbnail based on an image's region of interest (ROI). 

#### Get a Thumbnail JavaScript Example

* Enter the Height and Width desired for the cropped image.
* Enter the [Subscription Key](https://www.microsoft.com/cognitive-services/en-us/Computer-Vision-API/documentation/vision-api-how-to-topics/HowToSubscribe)
* Enter the image URL; for example: {"url":"http://example.com/images/test.jpg"}

```
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


## Generate a Description Using JavaScript <a name="GenerateADescription"> </a>
Generate a description of an image in human readable language with complete sentences.
#### JavaScript Example 
```
<!DOCTYPE html>
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

## Determine whether an Image Contains Adult Content Using JavaScript <a name="AdultContent"> </a>
Determine whether or not an image contains mature content.
  
