
```
kubectl create namespace grafana-operator
helm upgrade -i grafana-operator oci://ghcr.io/grafana/helm-charts/grafana-operator --version v5.19.0 -n grafana-operator
kubectl create namespace grafana 
kubectl apply -f grafana.yaml -n grafana
kubectl apply -f grafana-datasource.yaml -n grafana
kubectl apply -f grafana-dashboard.yaml -n grafana
```