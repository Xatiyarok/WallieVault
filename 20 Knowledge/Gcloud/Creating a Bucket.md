
When you create a bucket you must follow the universal bucket naming rules, below.

**Bucket naming rules** 

- Do not include sensitive information in the bucket name, because the bucket namespace is global and publicly visible.
- Bucket names must contain only lowercase letters, numbers, dashes (-), underscores (_), and dots (.). Names containing dots require [verification](https://cloud.google.com/storage/docs/domain-name-verification).
- Bucket names must start and end with a number or letter.
- Bucket names must contain 3 to 63 characters. Names containing dots can contain up to 222 characters, but each dot-separated component can be no longer than 63 characters.
- Bucket names cannot be represented as an IP address in dotted-decimal notation (for example, 192.168.5.4).
- Bucket names cannot begin with the "goog" prefix.
- Bucket names cannot contain "google" or close misspellings of "google".
- Also, for DNS compliance and future compatibility, you should not use underscores (_) or have a period adjacent to another period or dash. For example, ".." or "-." or ".-" are not valid in DNS names.
## Creating
Use the make bucket (`buckets create`) command to make a bucket, replacing `<YOUR_BUCKET_NAME>` with a unique name that follows the bucket naming rules:

gcloud storage buckets create gs://<YOUR-BUCKET-NAME>

This command is creating a bucket with default settings. To see what those default settings are, use the Cloud console **Navigation menu** > **Cloud Storage**, then click on your bucket name, and click on the **Configuration** tab.

## Upload an object into your bucket

Use Cloud Shell to upload an object into a bucket.

1. To download this image (ada.jpg) into your bucket, enter this command into Cloud Shell:

curl https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg --output ada.jpg


2. Use the `gcloud storage cp` command to upload the image from the location where you saved it to the bucket you created:

gcloud storage cp ada.jpg gs://YOUR-BUCKET-NAME

**Note:** When typing your bucket name, you can use the tab key to autocomplete it.

You can see the image load into your bucket from the command line.

You've just stored an object in your bucket!

3. Now remove the downloaded image:

rm ada.jpg

## Download an object from your bucket

- Use the `gcloud storage cp` command to download the image you stored in your bucket to Cloud Shell:

gcloud storage cp -r gs://YOUR-BUCKET-NAME/ada.jpg .

If successful, the command returns:

Copying gs://YOUR-BUCKET-NAME/ada.jpg...
/ [1 files][360.1 KiB/2360.1 KiB]
Operation completed over 1 objects/360.1 KiB.

You've just downloaded the image from your bucket.

## Copy an object to a folder in the bucket

- Use the `gcloud storage cp` command to create a folder called `image-folder` and copy the image (ada.jpg) into it:

gcloud storage cp gs://YOUR-BUCKET-NAME/ada.jpg gs://YOUR-BUCKET-NAME/image-folder/

**Note:** Compared to local file systems, [folders in Cloud Storage](https://cloud.google.com/sdk/gcloud/reference/storage/folders) have limitations, but many of the same operations are supported.

## List contents of a bucket or folder

- Use the `gcloud storage ls` command to list the contents of the bucket:

gcloud storage ls gs://YOUR-BUCKET-NAME

## ist details for an object

- Use the `gcloud storage ls` command, with the `-l` flag to get some details about the image file you uploaded to your bucket:

gcloud storage ls -l gs://YOUR-BUCKET-NAME/ada.jpg

## Make your object publicly accessible

- Use the `gcloud storage objects update` command to grant all users read permission for the object stored in your bucket:

gcloud storage objects update gs://YOUR-BUCKET-NAME/ada.jpg --add-acl-grant=entity=allUsers,role=READER

## Remove public access

1. To remove this permission, use the command:

gcloud storage objects update gs://YOUR-BUCKET-NAME/ada.jpg --remove-acl-grant=allUsers