Cloud developer project 3 - John Ngo


eksctl create cluster --name my-cluster --region us-east-1 --fargate

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

eksctl delete cluster --name my-cluster --region us-east-1


docker build . -t [Dockerhub-username]/udagram-frontend:v6
docker push [Dockerhub-username]/udagram-frontend:v6

