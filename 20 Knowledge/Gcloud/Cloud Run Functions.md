
## Initials settings
1. In Cloud Shell, run the following command to set the default region:
    
    gcloud config set run/region REGION
    
2. Create a directory for the function code:
    
    mkdir gcf_hello_world && cd $_
    
3. Create and open `index.js` to edit:
    
    nano index.js

## Deploy function

Cloud Run functions are event driven, meaning a trigger type must be specified. When deploying a new function, `--trigger-topic`, `--trigger-bucket`, or `--trigger-http` are common trigger events. When deploying an update to an existing function, the function keeps the existing trigger unless otherwise specified.

Deploy the **nodejs-pubsub-function** function to a pub/sub topic named **cf-demo**

gcloud functions deploy nodejs-pubsub-function \
  --gen2 \
  --runtime=nodejs_version \
  --region=REGION \
  --source=. \
  --entry-point=helloPubSub \
  --trigger-topic cf-demo \
  --stage-bucket PROJECT_ID-bucket \
  --service-account cloudfunctionsa@PROJECT_ID.iam.gserviceaccount.com \
  --allow-unauthenticated

Verify the status of the function:

gcloud functions describe nodejs-pubsub-function \
  --region=REGION
## Test function

After you deploy the function and know that it's active, test that the function writes a message to the cloud log after detecting an event.

- Invoke the PubSub with some data.
    
    gcloud pubsub topics publish cf-demo --message="Cloud Function Gen2"
## View logs

Check the logs to see your messages in the log history:

gcloud functions logs read nodejs-pubsub-function \
  --region=REGION