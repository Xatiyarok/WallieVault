### Creating a GKE cluster
A [cluster](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture) consists of at least one **cluster master** machine and multiple worker machines called **nodes**. Nodes are [Compute Engine virtual machine (VM) instances](https://cloud.google.com/compute/docs/instances/) that run the Kubernetes processes necessary to make them part of the cluster.

To create a cluster:
gcloud container clusters create --machine-type=e2-medium --zone=us-east4-c lab-cluster

### Get authentication credentials for the cluster
Authenticate with the cluster:
gcloud container clusters get-credentials lab-cluster

### Deploy an application to the cluster
GKE uses Kubernetes objects to create and manage your cluster's resources. Kubernetes provides the [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) object for deploying stateless applications like web servers. [Service](https://kubernetes.io/docs/concepts/services-networking/service/) objects define rules and load balancing for accessing your application from the internet.

To **create a new Deployment** `hello-server` from the `hello-app` container image, run the following `kubectl create` command:

kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0

To create a Kubernetes Service, which is a Kubernetes resource that lets you expose your application to external traffic, run the following `kubectl expose` command: