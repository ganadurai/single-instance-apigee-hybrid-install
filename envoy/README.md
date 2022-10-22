docker build -f "$ENVOY_HOME/Dockerfile-aekitctl" \
  -t apigee/devrel-envoyproxy:latest "$ENVOY_HOME"

kubectl create namespace envoy-ns

docker build -t apigee-hybrid/single-instance/envoy-proxy:latest .
docker push localhost:34401/apigee-hybrid/single-instance/envoy-proxy:latest

kubectl apply -f envoy-deployment.yaml