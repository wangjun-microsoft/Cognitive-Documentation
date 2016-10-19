##GetUserTranslationCounts Method##

This method gets the count of translations that are created by the user. It provides the list of translation counts grouped by the uriPrefix, from, to, user, minRating, and maxRating request parameters. 

**Syntax**

##C###

UserTranslationCount[]GetUserTranslationCounts(
            string appId,
            string uriPrefix,
            string from,
            string to,
            int? minRating,
            int? maxRating,
            string user, 
            string category
            DateTime? minDateUtc,
            DateTime? maxDateUtc,
            int? skip,
            int? take);
            
**Parameters**

| Parameter  | Description                                                                                                                                                                                                                                         |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| appld      | Required. If the Authorization header is used, leave the appid field empty,else specify a string containing "Bearer" + " " + access token.                                                                                                          |
| uriPrefix  | Optional. A string containing prefix of URI of the translation.                                                                                                                                                                                     |
| from       | Optional. A string representing the language code of the translation text.                                                                                                                                                                          |
| to         | Optional. A string representing the language code to translate the text into.                                                                                                                                                                       |
| minRating  | Optional. An integer value representing the minimum quality rating for the,translated text. The valid value is between -10 and 10. The default value is 1.                                                                                          |
| maxRating  | Optional. An integer value representing the maximum quality rating for the,translated text. The valid value is between -10 and 10. The default value is 1.                                                                                          |
| user       | Optional. A string that is used to filter the result based on the originator,of the submission.                                                                                                                                                     |
| category   | Optional. A string containing the category or domain of the translation.,This parameter supports only the default option general.                                                                                                                   |
| minDateUtc | Optional. The date from when you want to retrieve the translations. The date,must be in the UTC format.                                                                                                                                             |
| maxDateUtc | Optional. The date till when you want to retrieve the translations. The date,must be in the UTC format.                                                                                                                                             |
| skip       | Optional. The number of results that you want to skip on a page. For example,,if you want the skip the first 20 rows of the results and view from the 21st result,record, specify 20 for this parameter. The default value for this parameter is 0. |
| take       | Optional. The number of results that you want to retrieve. The maximum number of each request is 100. The default is 100.                                                                                                                           |
>Note: The skip and take request parameters enable pagination for a large number of result records. 

Return value

The result set contains array of the **UserTranslationCount**. Each UserTranslationCount has the following elements: 

| Field  | Description                                                                      |
|--------|----------------------------------------------------------------------------------|
| Count  | The number of results that is retrieved.                                         |
| From   | The source language                                                              |
| Rating | The rating that is applied by the submitter in the AddTranslation() method call. |
| To     | The target language.                                                             |
| Uri    | The URI applied in trhe AddTranslation() method call.                            |
| USer   | The user name                                                                    |

**Exceptions**

| Exception                                                                                                        | Message                                                                           | Conditions                                                                                                                                                                                                                     |
|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ArgumentsOutOfRangeException](https://msdn.microsoft.com/en-us/library/system.argumentoutofrangeexception.aspx) | The parameter **'maxDateUtc'** must be greater than or equal to **'minDateUtc'**. | The value of the parameter **maxDateUtc** is lesser than the value of the parameter **minDateUtc**.                                                                                                                            |
| TranslateApiException                                                                                            | IP is over the quota.                                                             |  The limit for the number of requests per minute is reached.   The request size remains limited at 10000 characters. An hourly and a daily quota limit the number of characters that the Microsoft Translator API will accept. |
|                                                                                                                  | AppId is over the quota.                                                          | The application ID exceeded the hourly or daily quota.                                                                                                                                                                         |

>**Note**: The quota will adjust to ensure fairness among all users of the service.

###**Example**###
**C#
PHP**

**C#**

using System;
using System.IO;
using System.Net;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Json;
using System.Text;
using System.Web;

namespace CtfReporting
{
    class Program
    {
        static void Main(string[] args)
        {
            AdmAccessToken admToken;
            string headerValue;
            //Get Client Id and Client Secret from https://datamarket.azure.com/developer/applications/
            //Refer obtaining AccessToken (http://msdn.microsoft.com/en-us/library/hh454950.aspx) 
            AdmAuthentication admAuth = new AdmAuthentication("clientId", "clientSecret");
            try
            {
                admToken = admAuth.GetAccessToken();
                // Create a header with the access_token property of the returned token
                headerValue = "Bearer " + admToken.access_token;
                Console.WriteLine("User translations count");
                ctfGetUserTranslationsCount(headerValue, 0, 5);
                Console.WriteLine("Press Enter for Next 5 Records");
                if (Console.ReadKey().Key == ConsoleKey.Enter)
                {
                    ctfGetUserTranslationsCount(headerValue, 5, 5);
                    Console.WriteLine("Press any key to exit...");
                    Console.ReadKey(true);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
                Console.WriteLine("Press any key to exit...");
                Console.ReadKey(true);
            }
        }
        private static void ctfGetUserTranslationsCount(string authToken, int skip, int take)
        {
            // Add CtfReportingService as a service reference, Address:http://api.microsofttranslator.com/v2/beta/ctfreporting.svc
            CtfReportingService.CtfReportingServiceClient reportingClient = new CtfReportingService.CtfReportingServiceClient();
            CtfReportingService.UserTranslationCount[] userTranslationsCount = reportingClient.GetUserTranslationCounts(authToken, "", "es", "en", null, null, "", "general", null, null, skip, take);
            foreach (CtfReportingService.UserTranslationCount item in userTranslationsCount)
            {
                Console.WriteLine(string.Format("Count={0},From={1},To={2},Rating={3},Uri={4},User={5}", item.Count, item.From, item.To, item.Rating, item.Uri, item.User));
            }
        }
    }
    [DataContract]
    public class AdmAccessToken
    {
        [DataMember]
        public string access_token { get; set; }
        [DataMember]
        public string token_type { get; set; }
        [DataMember]
        public string expires_in { get; set; }
        [DataMember]
        public string scope { get; set; }
    }

    public class AdmAuthentication
    {
        public static readonly string DatamarketAccessUri = "https://datamarket.accesscontrol.windows.net/v2/OAuth2-13";
        private string clientId;
        private string cientSecret;
        private string request;

        public AdmAuthentication(string clientId, string clientSecret)
        {
            this.clientId = clientId;
            this.cientSecret = clientSecret;
            //If clientid or client secret has special characters, encode before sending request
            this.request = string.Format("grant_type=client_credentials&client_id={0}&client_secret={1}&scope=http://api.microsofttranslator.com", HttpUtility.UrlEncode(clientId), HttpUtility.UrlEncode(clientSecret));
        }

        public AdmAccessToken GetAccessToken()
        {
            return HttpPost(DatamarketAccessUri, this.request);
        }

        private AdmAccessToken HttpPost(string DatamarketAccessUri, string requestDetails)
        {
            //Prepare OAuth request 
            WebRequest webRequest = WebRequest.Create(DatamarketAccessUri);
            webRequest.ContentType = "application/x-www-form-urlencoded";
            webRequest.Method = "POST";
            byte[] bytes = Encoding.ASCII.GetBytes(requestDetails);
            webRequest.ContentLength = bytes.Length;
            using (Stream outputStream = webRequest.GetRequestStream())
            {
                outputStream.Write(bytes, 0, bytes.Length);
            }
            using (WebResponse webResponse = webRequest.GetResponse())
            {
                DataContractJsonSerializer serializer = new DataContractJsonSerializer(typeof(AdmAccessToken));
                //Get deserialized object from JSON stream
                AdmAccessToken token = (AdmAccessToken)serializer.ReadObject(webResponse.GetResponseStream());
                return token;
            }
        }
    }
}
                                            
**PHP**

<?php

class AccessTokenAuthentication {
    /*
     * Get the access token.
     *
     * @param string $grantType    Grant type.
     * @param string $scopeUrl     Application Scope URL.
     * @param string $clientID     Application client ID.
     * @param string $clientSecret Application client ID.
     * @param string $authUrl      Oauth Url.
     *
     * @return string.
     */
    function getTokens($grantType, $scopeUrl, $clientID, $clientSecret, $authUrl){
        try {
            //Initialize the Curl Session.
            $ch = curl_init();
            //Create the request Array.
            $paramArr = array (
             'grant_type'    => $grantType,
             'scope'         => $scopeUrl,
             'client_id'     => $clientID,
             'client_secret' => $clientSecret
            );
            //Create an Http Query.//
            $paramArr = http_build_query($paramArr);
            //Set the Curl URL.
            curl_setopt($ch, CURLOPT_URL, $authUrl);
            //Set HTTP POST Request.
            curl_setopt($ch, CURLOPT_POST, TRUE);
            //Set data to POST in HTTP "POST" Operation.
            curl_setopt($ch, CURLOPT_POSTFIELDS, $paramArr);
            //CURLOPT_RETURNTRANSFER- TRUE to return the transfer as a string of the return value of curl_exec().
            curl_setopt ($ch, CURLOPT_RETURNTRANSFER, TRUE);
            //CURLOPT_SSL_VERIFYPEER- Set FALSE to stop cURL from verifying the peer's certificate.
            curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
            //Execute the  cURL session.
            $strResponse = curl_exec($ch);
            //Get the Error Code returned by Curl.
            $curlErrno = curl_errno($ch);
            if($curlErrno){
                $curlError = curl_error($ch);
                throw new Exception($curlError);
            }
            //Close the Curl Session.
            curl_close($ch);
            //Decode the returned JSON string.
            $objResponse = json_decode($strResponse);
                
            if ($objResponse->error){
                throw new Exception($objResponse->error_description);
            }
            return $objResponse->access_token;
        } catch (Exception $e) {
            echo "Exception-".$e->getMessage();
        }
    }
}

/*
 * Class:AccessTokenAuthentication
 *
 * Create SOAP Object.
 */
class SOAPMicrosoftTranslator {
    /*
     * Soap Object.
     *
     * @var ObjectArray.
     */
    public $objSoap;
    /*
     * Create the SAOP object.
     *
     * @param string $accessToken Access Token string.
     * @param string $wsdlUrl     WSDL string.
     *
     * @return string.
     */
    public function __construct($accessToken, $wsdlUrl){
        try {
            //Authorization header string.
            $authHeader = "Authorization: Bearer ". $accessToken;
            $contextArr = array(
                'http'   => array(
                    'header' => $authHeader
            )
            );
            //Create a streams context.
            $objContext = stream_context_create($contextArr);
            $optionsArr = array (
                'soap_version'   => 'SOAP_1_2',
                'encoding'          => 'UTF-8',
                'exceptions'      => true,
                'trace'          => true,
                'cache_wsdl'     => 'WSDL_CACHE_NONE',
                'stream_context' => $objContext,
                'user_agent'     => 'PHP-SOAP/'.PHP_VERSION."\r\n".$authHeader    
            );
            //Call Soap Client.
            $this->objSoap = new SoapClient($wsdlUrl, $optionsArr);
        } catch(Exception $e){
            echo "<h2>Exception Error!</h2>";
            echo $e->getMessage();
        }
    }
}

try {
    //Soap WSDL Url.
    $wsdlUrl       = "http://api.microsofttranslator.com/v2/beta/ctfreporting.svc";
    //Client ID of the application.
    $clientID       = "clientId";
    //Client Secret key of the application.
    $clientSecret = "clientSecret";
    //OAuth Url.
    $authUrl      = "https://datamarket.accesscontrol.windows.net/v2/OAuth2-13/";
    //Application Scope Url
    $scopeUrl     = "http://api.microsofttranslator.com";
    //Application grant type
    $grantType    = "client_credentials";

    //Create the Authentication object
    $authObj      = new AccessTokenAuthentication();
    //Get the Access token
    $accessToken  = $authObj->getTokens($grantType, $scopeUrl, $clientID, $clientSecret, $authUrl);
    //Create soap translator Object
    $soapTranslator = new SOAPMicrosoftTranslator($accessToken, $wsdlUrl);
    
    //Set the Params.
    $from         = 'en';
    $to         = 'de';
    $minRating  = 0;
    $maxRating  = 10;
    $takeResult = 100;
    $user         = 'guestUser';
    //Request argument list.
    $requestArg = array (
        'user'       => $user,
        'from'       => $from,
        'to'           => $to,
        'minRating'  => $minRating,
        'maxRating'  => $maxRating,
        'take'       => $takeResult
    );
    //Call GetUserTranslationCount Method.
    $responseObj = $soapTranslator->objSoap->GetUserTranslationCounts($requestArg);
    $translationCountArr = $responseObj->GetUserTranslationCountsResult->UserTranslationCount;
    echo "<table border=2px>";
    echo "<tr>";
    echo "<td><b>User</b></td><td><b>From</b></td><td><b>To</b></td><td><b>rating</b></td><td><b>Count</b></td>";
    echo "</tr>";
    if(sizeof($translationCountArr) > 0) {
        if(sizeof($translationCountArr) > 1) {
            foreach ($translationCountArr as $translationCount) {
                echo "<tr><td>$translationCount->User</td><td>$translationCount->From</td>
                    <td>$translationCount->To</td><td>$translationCount->Rating</td>
                    <td>$translationCount->Count</td></tr>";
            }
        } else {
            echo "<tr><td>$translationCountArr->User</td><td>$translationCountArr->From</td>
                    <td>$translationCountArr->To</td><td>$translationCountArr->Rating</td>
                    <td>$translationCountArr->Count</td></tr>";
        }
    } else {
        echo "<tr><td col='5'>No Record Found.</td></tr>";
    }
    echo "</table>";
    exit;
} catch (Exception $e) {
    echo "Exception: " . $e->getMessage() . PHP_EOL;
}
                                            
                                          


