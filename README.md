# Dialogflow in App Engine

[![Build
Status](https://travis-ci.org/GoogleCloudPlatform/appengine-try-java.svg?branch=master)](https://travis-ci.org/GoogleCloudPlatform/appengine-try-java)

This project demostrates that how to use Dialogflow in a java project in 
[GCP App Engine](https://cloud.google.com/appengine/docs/java/).

## Before you begin

1.  Download and install the [Google Cloud
    SDK](https://cloud.google.com/sdk/docs/).
1.  [Install and configure Apache Maven](http://maven.apache.org/index.html).
1.  [Create a new Google Cloud Platform project, or use an existing
		one](https://console.cloud.google.com/project).
1.  Initialize the Cloud SDK.

        gcloud init

1.  Install the Cloud SDK `app-engine-java` component.

        gcloud components install app-engine-java

## Deploying to App Engine

To run the application locally, use the [Maven App Engine
plugin](https://cloud.google.com/appengine/docs/java/tools/using-maven).

    mvn clean appengine:run

View the app at [localhost:8080](http://localhost:8080).

To deploy the app to App Engine, run

    mvn clean appengine:deploy

After the deploy finishes, you can view your application at
`https://YOUR_PROJECT.appspot.com`, where `YOUR_PROJECT` is your Google Cloud
project ID. You can see the new version deployed on the [App Engine section of
the Google Cloud Console](https://console.cloud.google.com/appengine/versions).

## Dialogflow with Kommunicate 

Dialogflow is an API that can used in many applications, Kommunicate is one of the interface the can integrate Dialogflow as its banckend bot to interact with users.

To integrate Dialogflow with Kommunicate, please follow [Integrate Dialogflow Bot into Website](https://www.kommunicate.io/blog/how-to-integrate-bot-using-dialogflow-in-kommunicate-1ac32911a7d0/)


## Code Explanation

The Javescript code of Kommunicate
```
<script type="text/javascript">
    /* NOTE : Use web server to view HTML files as real-time update will not work if you directly open the HTML file in the browser. */
    (function(d, m){
      var kommunicateSettings = {"appId":"26fee6508198ba626bcfd9e393d0ab19d","conversationTitle":"OretaBot", 
   "message":"Do you want more updates?",
   "ignoreTextResponse": false, // pass true if you want to hide the text response which you're passing along with custom payload in intent. 
   "platform":"kommunicate",
   "metadata": {
       "contentType": "300",
       "templateId": "6",
       "payload": [{
           "title": "Yes",
           "message": "Cool! send me more."
       }, {
           "title": "No ",
           "message": "Don't send it to me again"
       }]
   },
    "preLeadCollection": [{
    "field": "name",                          // Whatever column you want to add
    "required": true,                         //make it true if you want to make it mandatory
    "placeholder": "enter your name"          // add whatever text you want to show in placeholder
},
{
    "field": "email",
    "type": "email",
    "required": true,
    "placeholder": "enter your email"
}, 
{
    "field": "phone",
    "type": "phone",
    "required": true,
    "placeholder": "enter your phone"
},
{
    "field": "address",
    "type": "address",
    "required": true,
    "placeholder": "enter your address"
}]};
      var s = document.createElement("script"); s.type = "text/javascript"; s.async = true;
      s.src = "https://api.kommunicate.io/v2/kommunicate.app";
      var h = document.getElementsByTagName("head")[0]; h.appendChild(s);
      window.kommunicate = m; m._globals = kommunicateSettings;
    })(document, window.kommunicate || {});
</script>
```




