# helm-upgrade-from-source

Clone, and deploy a helm chart from a public source files, to the ADLS cluster with the help of Tekton pipelines.

### required tekton tasks

* [git-clone](https://hub.tekton.dev/tekton/task/git-clone)
* [helm-upgrade-from-source](https://hub.tekton.dev/tekton/task/helm-upgrade-from-source)

### setup namespace

```bash
# create namespace
kubectl create ns tekton-demo

# install git-clone task
kubectl -n tekton-demo apply -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/git-clone/0.9/git-clone.yaml

# install helm-upgrade-from-source task
kubectl -n tekton-demo apply -f  https://raw.githubusercontent.com/tektoncd/catalog/main/task/helm-upgrade-from-source/0.3/helm-upgrade-from-source.yaml

# Add service account
kubectl -n tekton-demo create serviceaccount helm-pipeline-run-sa

# Add edit role to service account
kubectl -n tekton-demo create rolebinding helm-pipeline-run-sa-edit --clusterrole edit --serviceaccount tekton-demo:helm-pipeline-run-sa 
```

### Apply created pipeline

```bash
kubectl -n tekton-demo apply -f helm-upgrade-from-source/helm-upgrade-from-source-pipeline.yaml
```

### Run pipeline for pacman

```bash
kubectl -n tekton-demo create -f helm-upgrade-from-source/packman-helm-from-resource.yaml
```


## TODO

**Tekton ingress**

Create a new tekton task, which will create a ingress manifest file that would be deployed in the kubernetest cluster.

See also: https://hub.tekton.dev/tekton/task/kubernetes-actions

**Linter** 

add this task to our steps before deploying the helm - this will check if the files are valid.

see task: https://hub.tekton.dev/tekton/task/yaml-lint
