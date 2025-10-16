```
kubectl create namespace tanzu-system-monitoring 
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm upgrade -i kps prometheus-community/kube-prometheus-stack -n tanzu-system-monitoring -f prom-helm-values.yaml
```