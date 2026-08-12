gcloud compute networks create managementnet --project=qwiklabs-gcp-01-5e1d954f1258 --subnet-mode=custom --bgp-routing-mode=regional --bgp-best-path-selection-mode=legacy 

gcloud compute networks subnets create managementsubnet-1 --project=qwiklabs-gcp-01-5e1d954f1258 --range=10.130.0.0/20 --stack-type=IPV4_ONLY --network=managementnet --region=us-east1


gcloud compute --project=qwiklabs-gcp-01-5e1d954f1258 firewall-rules create managementnet-allow-icmp-ssh-rdp --direction=INGRESS --priority=1000 --network=managementnet --action=ALLOW --rules=tcp:22,tcp:3389,icmp --source-ranges=0.0.0.0/0

Creating a VM:

gcloud compute instances create managementnet-vm-1 \
    --project=qwiklabs-gcp-01-5e1d954f1258 \
    --zone=us-east1-c \
    --machine-type=e2-micro \
    --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=managementsubnet-1 \
    --metadata=enable-osconfig=TRUE,enable-oslogin=true \
    --maintenance-policy=MIGRATE \
    --provisioning-model=STANDARD \
    --service-account=499351412110-compute@developer.gserviceaccount.com \
    --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/trace.append \
    --create-disk=auto-delete=yes,boot=yes,device-name=managementnet-vm-1,image=projects/debian-cloud/global/images/debian-13-trixie-v20260811,mode=rw,size=10,type=pd-balanced \
    --no-shielded-secure-boot \
    --shielded-vtpm \
    --shielded-integrity-monitoring \
    --labels=goog-ops-agent-policy=v2-template-1-7-0,goog-ec-src=vm_add-gcloud \
    --reservation-affinity=any \
&& \
printf 'agentsRule:\n  packageState: installed\n  version: latest\ninstanceFilter:\n  inclusionLabels:\n  - labels:\n      goog-ops-agent-policy: v2-template-1-7-0\n' > config.yaml \
&& \
gcloud compute instances ops-agents policies create goog-ops-agent-v2-template-1-7-0-us-east1-c \
    --project=qwiklabs-gcp-01-5e1d954f1258 \
    --zone=us-east1-c \
    --file=config.yaml \
&& \
gcloud compute resource-policies create snapshot-schedule default-schedule-1 \
    --project=qwiklabs-gcp-01-5e1d954f1258 \
    --region=us-east1 \
    --max-retention-days=14 \
    --on-source-disk-delete=keep-auto-snapshots \
    --daily-schedule \
    --start-time=00:00 \
&& \
gcloud compute disks add-resource-policies managementnet-vm-1 \
    --project=qwiklabs-gcp-01-5e1d954f1258 \
    --zone=us-east1-c \
    --resource-policies=projects/qwiklabs-gcp-01-5e1d954f1258/regions/us-east1/resourcePolicies/default-schedule-1

Shorter version:

gcloud compute instances create \ privatenet-vm-1 \ --zone=us-east1-c \ --machine-type=e2-micro \ --subnet=privatesubnet-1

