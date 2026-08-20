
# Configurar región
gcloud config set compute/region europe-west1

# Configurar zona
gcloud config set compute/zone europe-west1-b

# Crear bucket de Cloud Storage
gcloud storage buckets create \
  gs://qwiklabs-gcp-04-3a5b7764cf07-bucket

# Crear tópico de Pub/Sub
gcloud pubsub topics create topic-memories-965

# Desplegar Cloud Function de segunda generación
gcloud functions deploy memories-thumbnail-maker \
  --gen2 \
  --runtime=nodejs22 \
  --region=europe-west1 \
  --source=. \
  --entry-point=memories-thumbnail-maker \
  --trigger-bucket=gs://qwiklabs-gcp-04-3a5b7764cf07-bucket