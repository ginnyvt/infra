# Runner

Self-hosted runner for GitHub actions.

## Create PAT sealded secret (with repo permissions)

```bash
export PAT=your_github_pat
kubectl create secret generic gh-token \
   --namespace=harrytang-staging \
   --from-literal=github_token=$PAT \
   --dry-run=client -o yaml | kubeseal --format=yaml > sealed-secret.yaml
```
