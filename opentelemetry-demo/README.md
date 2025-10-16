```
kubectl create namespace opentel
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
helm repo update 

# Optionally run this to generate a new values file.
# helm show values open-telemetry/opentelemetry-demo > ./otel-demo-helm-values.yaml

kubectl create secret tls opentel-tls-secret --cert=./fullchain.pem --key=./priv.pem -n opentel
helm install my-otel-demo open-telemetry/opentelemetry-demo -f otel-demo-helm-values.yaml -n opentel

# To update
# helm upgrade my-otel-demo open-telemetry/opentelemetry-demo -f otel-demo-helm-values.yaml -n opentel
```