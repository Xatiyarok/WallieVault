
student-03-45c6481fd90c@test-vm:~$ gcloud compute firewall-rules list
ERROR: (gcloud.compute.firewall-rules.list) Some requests did not succeed:
 - Request had insufficient authentication scopes.

student-03-45c6481fd90c@test-vm:~$ gcloud compute firewall-rules delete allow-http-web-server
The following firewalls will be deleted:
 - [allow-http-web-server]

Do you want to continue (Y/n)?  y

ERROR: (gcloud.compute.firewall-rules.delete) Could not fetch resource:
 - Request had insufficient authentication scopes.