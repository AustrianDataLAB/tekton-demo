# [helm-upgrade-from-repo](https://hub.tekton.dev/tekton/task/helm-upgrade-from-repo)
These tasks will install / upgrade a helm chart into your Kubernetes giving only a helm repo URL.

**NOTE:** `helm_repo` must be publicly accessable.

## Preq

### install task
```bash
kubectl apply -f https://api.hub.tekton.dev/v1/resource/tekton/task/helm-upgrade-from-repo/0.2/raw
```

### apply pipeline
```bash
kubectl apply -f helm-upgrade-from-repo/helm-upgrade-from-repo-pipeline.yaml -n NAMESPACE
```

### Create SA 
**Additionaly we could define a global SA and set this in  [config-defaults.yaml](../extra/config-defaults.yaml)**

```bash
# Add service account
kubectl -n tekton-demo create serviceaccount tekton-helm-pipeline-sa

# Add edit role to service account
kubectl -n tekton-demo create rolebinding tekton-helm-pipeline-sa-edit --clusterrole edit --serviceaccount tekton-demo:tekton-helm-pipeline-sa 
```

### pipeline params
Used in the [tekton-dashboard](http://tekton-dashboard:9097/) 

```yaml
helm_repo: https://harbor.caas-0001.dev.austrianopencloudcommunity.org/chartrepo/external
chart_name: pacman-rancher/pacman-rancher
release_version: 0.0.1
release_name: pacman-rancher
release_namespace: tekton-demo
```

![dashboard](./params.png)


# TODO
* see [yq](https://hub.tekton.dev/tekton/task/yq) task
