Using [kind](https://kind.sigs.k8s.io/) to create k8s cluster.

Create cluster, install and test traefik.
```
kind create cluster --config kind-config.yaml
kubectl ctx kind-kind
helm install traefik traefik/traefik --values=traefik-chart-values.yaml
kubectl apply -k deployment/
```

Expose the dashboard:
```
kubectl port-forward (kubectl get pods --selector "app.kubernetes.io/name=traefik" --output=name) 9001:9000
```