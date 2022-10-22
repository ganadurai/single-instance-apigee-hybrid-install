
kubectl create namespace envoy-ns

docker build -t localhost:34401/apigee-hybrid/single-instance/envoy-proxy:v1 .
docker push localhost:34401/apigee-hybrid/single-instance/envoy-proxy:v1

kubectl delete -f envoy-deployment.yaml
kubectl apply -f envoy-deployment.yaml