# Clone, Package & push Helm chart

## Apply task

```bash
kubectl apply task/helm-package-from-repo.yaml -n $NAMESPACE
```

## Apply Pipeline

```bash
kubectl apply pipeline/pipeline-clone-package-push.yaml -n $NAMESPACE
```
