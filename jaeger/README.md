```
kubectl create namespace jaeger
helm repo add jaegertracing https://jaegertracing.github.io/helm-charts
helm repo update
# Optionally run this to generate a new values file.
# helm show values jaegertracing/jaeger > jaeger-helm-values.yaml

kubectl create secret tls jaeger-tls-secret --cert=./fullchain.pem --key=./priv.pem -n jaeger
helm install jaeger jaegertracing/jaeger -n jaeger -f jaeger-helm-values.yaml
```