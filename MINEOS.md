# Mineos-node

```shell
mkdir -p /home/trygve/k8s-data/config/mineos
kubectl create secret generic mineos -n minecraft \
  --from-literal=username=admin \
  --from-literal=password=changeme
helm install prowlarr trygve55/mineos \
  --namespace minecraft \
  --set clusterIssuer="letsencrypt-prod" \
  --set ingress.enabled=true \
  --set ingress.adminPage.host="mineos.local" \
  --set httpServices[0].port=8123 \
  --set httpServices[0].name="dynmap" \
  --set httpServices[0].host="minecraft.local" \
  --set httpServices[0].path="/"
```