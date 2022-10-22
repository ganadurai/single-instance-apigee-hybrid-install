
kubectl create namespace envoy-ns

docker build -t localhost:34401/apigee-hybrid/single-instance/envoy-proxy:latest .
docker push localhost:34401/apigee-hybrid/single-instance/envoy-proxy:latest

kubectl apply -f envoy-deployment.yaml