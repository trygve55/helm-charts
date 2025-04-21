# helm-charts
Helm charts for:
* Sonarr
* Radarr
* Prowlarr
* Bazarr
* Jellyfin
* Jellyseer
* arch-qbittorrentvpn

All of these Helm charts support using `baseUrl: /` to enable hosting each service in a specific subfolder. This is useful if you want to host all services under the same domain.

All of these Helm charts support using `clusterIssuer: letsencrypt` to enable HTTPS when using `ingress-ngnix` and `cert-manager`. Setting this value will enable HTTPS for all hosts defined for this helm release.

Sonarr, Radarr and Prowlarr support `authenticationMethod: External` to disable the application's built in authentication, this is useful when you want to use Ingress based authentication.

## Adding Helm chart repository
```shell
helm repo add trygve55 https://trygve55.github.io/helm-charts --force-update
```

## Example usage
You can find examples on how to use these helm charts in [k8s-servarr-setup](https://github.com/trygve55/k8s-servarr-setup).
