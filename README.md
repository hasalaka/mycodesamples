# mycodesamples

alias k=kubectl
k exec -it nginx-pod -- /bin/sh #direct access to pod

k expose pod nginx-pod --type=NodePort --port=80 #Expose pod directly 

#Build and push to reg #

1) docker build -t gcr.io/gcp-wow-rwds-hwaravita-poc-dev/nodesample:v3 .

2) docker push gcr.io/gcp-wow-rwds-hwaravita-poc-dev/nodesample:v3

Verify
gcloud container images list
gcloud container images list-tags gcr.io/gcp-wow-rwds-hwaravita-poc-dev/nodesample

#Update deployment manaully
kubectl set image deployment/samplenodeproxy-deployment nodeapp=gcr.io/gcp-wow-rwds-hwaravita-poc-dev/nodesample:v4 --record