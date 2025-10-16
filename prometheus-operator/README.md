```
kubectl create namespace tanzu-system-monitoring 
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

# Optionally run this to generate a new values file.
# helm show values prometheus-community/kube-prometheus-stack > prom-helm-values.yaml

kubectl create secret tls prometheus-tls-secret --cert=./fullchain.pem --key=./priv.pem -n tanzu-system-monitoring
helm upgrade -i kps prometheus-community/kube-prometheus-stack -n tanzu-system-monitoring -f prom-helm-values.yaml
```