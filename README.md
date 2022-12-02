# tekton-demo


## DEMO

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

#### forward the pacman port

```bash
sudo kubefwd svc -n tekton-demo
```

**VISIT**
[http://pacman-rancher](http://pacman-rancher/)


# Errors
```bash
pacman-rancher	adlsregistrysbx.azurecr.io/tutorials/pacman:latest		0	-	
CreateContainerConfigError (container has runAsNonRoot and image will run as root (pod: "pacman-rancher-75d5cbc87f-rw2hn_tekton-demo(6fac4b02-9217-4c5c-b68e-22db305db726)", container: pacman-rancher))


mongo	bitnami/mongodb:4.4.14
0/1	0	0	0	7 mins	
Pods "mongo-858c84d959-" is forbidden: PodSecurityPolicy: unable to admit pod: [spec.initContainers[0].securityContext.runAsUser: Invalid value: 0: running with the root UID is forbidden]:Deployment does not have minimum availability.

```