GCP Regions and Zones: GCP offers products and services in multiple distinct geographic locations, called regions. Each region has multiple distinct zones. Each zone is isolated from other zones in terms of power and internet connectivity.(160Km apart?)

GCP gives you three basic ways to interact with the services and resources.

Google Cloud Platform Console: a web-based, graphical user interface that you can use to manage your GCP projects and resources.

Command-line interface

Google Cloud SDK: provides the gcloud command-line tool, which gives you access to the commands you need.

Cloud Shell: a browser-based, interactive shell environment for GCP. You can access Cloud Shell from the GCP console. If you prefer to work in a terminal window, the Google Cloud SDK provides the gcloud command-line tool, which gives you access to the commands you need. The gcloud tool can be used to manage both your development workflow and your GCP resources. See the gcloud reference for the complete list of available commands.

[Client libraries](https://cloud.google.com/compute/docs/api/libraries): The Cloud SDK includes client libraries that enable you to easily create and manage resources. GCP client libraries expose APIs to provide access to services and resource management functions. You also can use the Google API client libraries to access APIs for products such as Google Maps, Google Drive, and YouTube.

## Check Out resources for Data Analyst
https://github.com/GoogleCloudPlatform/training-data-analyst

## Cloudshell

GCP Project ID in Cloud Shell. While working in Cloud Shell, you will have access to the Project ID in the $DEVSHELL_PROJECT_ID environment variable.
~~~
export GCLOUD_PROJECT=$DEVSHELL_PROJECT_ID
~~~
## Datastore

`Google Cloud Datastore` is a NoSQL document database built for automatic scaling, high performance, and ease of application development. Cloud Datastore offers SQL-like queries being called GQL. 

In this lab, you use Datastore to store application data for an online Quiz application. You also configure the application to retrieve from Datastore and display the data in the quiz.

The Quiz application skeleton has already been written. You clone the repository that contains the skeleton using Google Cloud Shell, review the code using the Cloud Shell editor, and view it using the Cloud Shell web preview feature. You then modify the code that stores data to use Cloud Datastore

[IF your database is empty, you can still upgrade to Cloud Firestore, the next generation of Cloud Datastore, to get more features](https://cloud.google.com/firestore/docs/firestore-or-datastore?_ga=2.14672767.-936674689.1554190521) 