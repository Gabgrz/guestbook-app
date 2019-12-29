A ready to run app locally on Google Cloud Shell.

Steps to run

1. Set project.
2. cd to guestbook-services
3. Run command:

mvn spring-boot:run

4. Open a new terminal window
5. Set project
6. cd to guestbook-frontend
7. In local API Vision version, run command:

mvn spring-boot:run -Dspring.cloud.gcp.credentials.location=file:///$HOME/service-account.json

Updates
-
Date: 10/06/2019
- Pub/Sub is not working

Resources
-
Repository:
https://source.cloud.google.com/microservices-spring-gcloud/guestbook-app?authuser=3

<br>

---
<b>Other documentation</b>

To run this application locally on gcloud, follow these steps:

- Clone from Cloud Source Repository or Bucket

Cloud Source Repository:
gcloud source repos clone guestbook-app-local --project=certain-sun-256723
gcloud source repos clone guestbook-app-local --microservices-spring-gcloud

Bucket:
gsutil -m cp -r gs://[BUCKET_ID]/* .




[OPTIONAL]
- Configure Runtime Configurations
gcloud services enable runtimeconfig.googleapis.com
gcloud beta runtime-config configs create frontend_cloud

gcloud beta runtime-config configs variables set greeting \
  "Hi from Runtime Config" \
  --config-name frontend_cloud
  
gcloud beta runtime-config configs variables list --config-name=frontend_cloud

gcloud beta runtime-config configs variables \
  get-value greeting --config-name=frontend_cloud
  
- Update bucket names in java Class "FrontendController.java"