# Web

Go to the `web` directory and run the following command to create the sealed secret:

```bash
export CF_API_TOKEN="toBeReplaced"
export REVALIDATE_TOKEN="toBeReplaced"
export NAMESPACE="toBeReplaced"
kubectl create secret generic --dry-run=client \
    web-env \
    --namespace=$NAMESPACE \
    --from-literal=CF_API_TOKEN=$CF_API_TOKEN \
    --from-literal=REVALIDATE_TOKEN=$REVALIDATE_TOKEN \
    -o yaml \
    | kubeseal --format=yaml > sealed-secret.yaml
```
