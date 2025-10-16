```
kubectl create namespace jaeger
helm repo add jaegertracing https://jaegertracing.github.io/helm-charts
helm repo update
# Optionally run this to generate a new values file.
# helm show values jaegertracing/jaeger > jaeger-helm-values.yaml
helm install jaeger jaegertracing/jaeger -n jaeger -f jaeger-helm-values.yaml
```