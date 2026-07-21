## Initials settings
1. In Cloud Shell, run the following command to set the default region:
    
    gcloud config set run/region REGION
    
2. Create a directory for the function code:
    
    mkdir gcf_hello_world && cd $_
    
3. Create and open `index.js` to edit:
    
    nano index.js

## Deploy function

Cloud Run functions are event driven, meaning a trigger type must be specified. When deploying a new function, `--trigger-topic`, `--trigger-bucket`, or `--trigger-http` are common trigger events. When deploying an update to an existing function, the function keeps the existing trigger unless otherwise specified.

## Test function

## View logs

