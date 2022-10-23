
kubectl create namespace envoy-ns

docker build -t localhost:34401/apigee-hybrid/single-instance/envoy-proxy:v1 .
docker push localhost:34401/apigee-hybrid/single-instance/envoy-proxy:v1

SERVICE_NAME=$(kubectl get svc -n ${APIGEE_NAMESPACE} -l env=eval,app=apigee-runtime --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')

envsubst < envoy-deployment.tmpl > envoy-deployment.yaml

kubectl delete -f envoy-deployment.yaml
kubectl apply -f envoy-deployment.yaml