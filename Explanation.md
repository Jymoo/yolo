## Ocherstration with Kubernetis and GCP

## from the docker file pushe the images to dockerhub
 docker buid -t dockerhubname/filename:version
 list docker images
 docker login
 docker push image-name/version


## creating namespace
kubectl create namespace devops-project
    namespace/devops-project created
set namespace for this project by switching to use devops-project

 ## Creat deployment files to minikube for local test
1. Add backend-deployment.yaml for backend application
2. Add frontend-deployment.yaml for frondent application
3. Add mongodb-deployment.yaml for the mongo database


## implement the backend-deployment.yaml, frontend-deployment.yaml, mongodb-deployment.yaml, network-policy.yaml in a manifest folder 

# apply backend changes 
kubectl apply -f backend-deployment.yaml
kubectl apply -f frontend-deployment.yaml
kubectl apply -f mongodb-deployment.yaml
kubectl apply -f network-policy.yaml

## test in minikube using minikube ip 
minikube ip: get the ip of the node
kubectl get svc: list the services with port running

## when sure that all is well 
Edit the manifest yamls to use service to communicate other than IPs

## Create GCR to push the images to gloud

build
 docker build -t gcr.io/<project-id>/<image-name>:<tag> .

tag
 docker tag gcr.io/<project-id>/<image-name>:<tag>

authenticate gcloud
 gcloud auth configure-docker

push to gcr
 docker push gcr.io/<project-id>/<image-name>:<tag>



## To deploy  to Google Kubernetes Engine (GKE) using the kubectl command line, follow these steps:

Authenticate with Google Cloud and Set Up Kubernetes Context:
First, make sure you are authenticated with your Google Cloud account and have the necessary permissions to manage GKE clusters.

gcloud auth login
gcloud config set project <your-project-id>
gcloud container clusters get-credentials <cluster-name> --zone <cluster-zone>
Replace <your-project-id>, <cluster-name>, and <cluster-zone> with  actual project ID, GKE cluster name, and the corresponding zone.

## Apply Kubernetes Manifests:

kubectl apply -f path/to/your/manifest.yaml
Apply each of your manifest files

kubectl apply -f manifest/backend-deployment.yaml
kubectl apply -f manifest/frontend-deployment.yaml
kubectl apply -f manifest/mongodb-deployment.yaml
kubectl apply -f manifest/network-policy.yaml

Monitor Deployment:

kubectl get pods
kubectl get deployments
kubectl get services

Access Application:

Once  deployments are up and running, access application using the external IP or domain name associated with your GKE LoadBalancer or Ingress.

### ''' 
use link below to access frondend
http://35.225.47.7/

'''

## [optional] add skaffold to compine all the manifest files, run and deploy to GCK
run the skafffold using 
skaffold run
