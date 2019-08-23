
# Make voice call from audio file

This api initiate a call, after the answer it will play an audio file and Dillo will automatically hang up after the file is played.

### Prerequisites 

1. Have an CustomerCode, ApiKey and Sender defined 
2. Have an url with  audio file in wav format

### Implementation

In order to make a call you have to set value to the required parameters.

The apikey and CustomerCode is displayed on Console menu on your account. Also, from your account you can get the sender from  Dashboard->Sender menu.

The httpUrl is the url to which you have to make the POST call. 

The receivers are set in the phoneNumbers variable. This a list of string. The phone number must be with prefix and it can begin either with + or with '00'.

```
string httpUrl = "http://italiacall.sendservice.eu/ndoctwebapi/api/sendaction";

string customerCode = "John";
string apiKey = "0A0BXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX";
string sender = "9876";
string fileUrl = "https://s3.eu-central-1.amazonaws.com/dev-amazon-polly/105d3d94-297f-4b53-a7f9-ceb31dd2b1ae.wav";     

 List<string> phoneNumbers = new List<string>();
 //duplicate this row to add more phone numbers
 //NOTE: phone number  with prefix
  phoneNumbers.Add("0040752674265");

  var responseCall= dillo.MakeVoiceCall(customerCode, apiKey, sender, fileUrl, phoneNumbers, httpUrl)

  Console.WriteLine(responseCall);
```

### Response

If the the customer code or the apiKey is incorrect the response status  will be 404 Not Found, else the response status it will be 201 Created and in the body you will receive an unique identifier code that allows you to check the request status.
Ex:

```
{
"guid": "3abf0de6-5c51-4a74-90c8-d3f95d844969"
}
```
