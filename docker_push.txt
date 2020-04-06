#!/bin/bash

sed -i "s|SED_REPLACE|$AWS_BUCKET_CREDENTIALS|g" udacity-c3-deployment/k8s/aws-secret.yaml
kubectl create secret generic env-secret --from-literal=POSTGRESS_USERNAME=${POSTGRESS_USERNAME} --from-literal=POSTGRESS_PASSWORD=${POSTGRESS_PASSWORD} --dry-run -o yaml | kubectl apply -f -

kubectl apply -f udacity-c3-deployment/k8s

kubectl set image deployments/backend-feed backend-feed=scheele/udacity-restapi-feed:$SHA
kubectl set image deployments/backend-user backend-user=scheele/udacity-restapi-user:$SHA
kubectl set image deployments/frontend frontend=scheele/udacity-frontend:$SHA
kubectl set image deployments/reverseproxy reverseproxy=scheele/udacity-reverseproxy:$SHA