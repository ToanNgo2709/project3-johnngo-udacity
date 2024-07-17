Cloud developer project 3 - John Ngo


eksctl create cluster --name my-cluster --region us-east-1 --fargate


eksctl create cluster \
  --name project3-john-cluster \
  --region us-east-1 \
  --nodegroup-name my-m5-large-nodes \
  --node-type m5.large \
  --nodes 2 \
  --nodes-min 2 \
  --nodes-max 3 \
  --managed


kubectl apply -f aws-secret.yaml
kubectl apply -f env-secret.yaml
kubectl apply -f env-configmap.yaml
kubectl apply -f udagram-api-feed-deployment.yaml
kubectl apply -f udagram-api-feed-service.yaml
kubectl apply -f udagram-api-user-deployment.yaml
kubectl apply -f udagram-api-user-service.yaml
kubectl apply -f udagram-frontend-deployment.yaml
kubectl apply -f udagram-frontend-service.yaml
kubectl apply -f udagram-reverseproxy-deployment.yaml 
kubectl apply -f udagram-reverseproxy-service.yaml
kubectl apply -f hpa.yaml


kubectl get nodes -o wide
kubectl get pods -A -o wide

kubectl get deployments
kubectl expose deployment frontend --type=LoadBalancer --name=publicfrontend
kubectl expose deployment reverseproxy --type=LoadBalancer --name=publicreverseproxy

kubectl get services 
kubectl get pods

eksctl delete cluster --name project3-johnngo-cluster --region us-east-1


docker build . -t toan158n/udagram-frontend:v8
docker push toan158n/udagram-frontend:v8


kubectl set image deployment frontend frontend=toan158n/udagram-frontend:v8

