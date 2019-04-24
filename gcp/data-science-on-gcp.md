## Ingesting Data Into The Cloud Using Google App Engine

Create environment variables that will be used later in the lab for your project ID and the storage bucket that will contain your data:

~~~
export PROJECT_ID=$(gcloud info --format='value(config.project)')
export BUCKET=${PROJECT_ID}-ml
~~~

## Ingest data files to the storage bucket

The repository contains a Python application called `ingest_flights.py` in the `02_ingest/monthlyupdate/` folder which contains the following functions:

Change to `monthly update` directory
~~~
cd ~/data-science-on-gcp/02_ingest/monthlyupdate
~~~
download data for a month
~~~
./ingest_flights.py  --bucket $BUCKET --year 2015 --month 01
~~~

## Create a Flask web app to ingest data

Flask is a framework for creating lightweight web applications with Python. Our final objective is to create a web application, written in Python, that can be invoked using Cron so Flask is ideal.

The Python file ingestapp.py uses Flask to host a simple welcome page for the root of the web app that just points to a second URL, /ingest , that calls the ingest_next_month function defined in the ingest_flights.py application you tested in the last task.

To load and run an application on Google App Engine you need to create a yaml file that contains the details that specify the type of application, the application itself, and its parameters.

The repository contains a pre-prepared sample yaml file called app.yaml.
~~~
runtime: python
env: flex
entrypoint: gunicorn -b :$PORT ingestapp:app
service: flights

#[START env]
env_variables:
    CLOUD_STORAGE_BUCKET: cloud-training-demos-ml
#[END env]

handlers:
- url: /ingest
  script: ingestapp.app

- url: /.*
  script: ingestapp.app
 ~~~ 

Google App Engine needs to be initialized. The simplest way to do this is to create a new application and then deploy an application to it. Do that by running the following:
~~~
gcloud app create --region us-central

git clone https://github.com/GoogleCloudPlatform/python-docs-samples
cd python-docs-samples/appengine/standard/hello_world
~~~

Now that App Engine has been initialized, stop the sample demo application:
~~~
gcloud app deploy --quiet --stop-previous-version
~~~

Change back to the monthly update directory:
~~~
cd ~/data-science-on-gcp/02_ingest/monthlyupdate
~~~

The sample app.yaml configuration file in the 02_ingest/monthlyupdate directory in the repository needs to be modified to point to the correct cloud storage bucket for this lab:
~~~
sed -i -e 's/cloud-training-demos-ml/'"$BUCKET"'/g' app.yaml
~~~

Now deploy the app using Google App Engine:
~~~
gcloud app deploy
~~~


