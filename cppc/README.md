# Clone, Package & push Helm chart

## Preq

### Authentication to a Container Registry

This Task & Pipeline requires a registry secret, in order to push charts.

**Create basicAuth secret**

```bash
kubectl -n $NAMESPACE create secret generic <NAME_OF_SECRET> \
    --from-literal=username=USERNAME \
    --from-literal=password=<AUTH>
```

## Parameters

* **HELM_IMAGE**: Helm image that has cm-push plugin (_default:_ `mbwali/helm-rootless`)
* **REPO_URL**: Repository URL to clone from. (_required_)
* **CHART_NAME**: Name of the Chart (_required_)
* **CHART_DESTINATION**: Destination URL for chart, (_default:_ `https://harbor.caas-0001.dev.austrianopencloudcommunity.org`)
* **CHART_DIR**: The directory in the source repository where the installable chart should be found. (_default:_ `""`)
* **HELM_SECRET_NAME**: The name of secret which contains basic auth keys for the registry - (_required_)

## Apply task

```bash
kubectl apply task/helm-package-from-repo.yaml -n $NAMESPACE
```

## Apply Pipeline

```bash
kubectl apply pipeline/pipeline-clone-package-push.yaml -n $NAMESPACE
```
