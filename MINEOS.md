# Mineos-node

```shell
mkdir -p /home/trygve/k8s-data/config/mineos
kubectl create namespace minecraft
kubectl create secret generic mineos -n minecraft \
  --from-literal=username=admin \
  --from-literal=password=changeme
helm install mineos trygve55/mineos \
  --namespace minecraft \
  --set clusterIssuer="letsencrypt-prod" \
  --set ingress.enabled=true \
  --set ingress.adminPage.host="mineos.local" \
  --set httpServices[0].port=8123 \
  --set httpServices[0].name="dynmap" \
  --set httpServices[0].host="minecraft.local" \
  --set httpServices[0].path="/"
```

Example of Dynmap being added:
```shell
  --set httpServices[0].port=8123 \
  --set httpServices[0].name="dynmap" \
  --set httpServices[0].host="minecraft.local" \
  --set httpServices[0].path="/"
```

Example of another TCP port being added:
```shell
  --set services[0].port=25565 \
  --set services[1].port=25566 \
  --set services[2].port=25567 \
  --set services[3].port=25568 \
  --set services[4].port=25569 \
  --set services[5].port=25570 \
  --set services[6].port=24454 \
  --set services[6].name="simple-voice-chat" \
  --set services[6].protocol="UDP"
```