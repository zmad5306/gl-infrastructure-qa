# gl-infrastructure-qa
k8s manifests for qa env

## Create Cluster

`gcloud config set compute/zone us-central1-f`

`gcloud container clusters create qa --cluster-version=1.9.6-gke.1 --node-version=1.9.6-gke.1 --num-nodes=4`

## Create Static IP

`gcloud compute addresses create gl-qa-ip --global`

## Continious Delivery Builds

**Name:** QA CD Build

**Trigger type:** Branch

**Branch (regex):** ^master$

**Build configration:** cloudbuild.yaml

**cloudbuild.yaml location:** /cloudbuild.yaml

### Substitution variables

| Variable                    | Value               |
| --------------------------- | -----               |
| _CLOUDSDK_COMPUTE_ZONE      | us-central1-f       |
| _CLOUDSDK_CONTAINER_CLUSTER | qa                  |
