# Presequence

**Configuring Your registry Secret**

```bash
kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=DOCKER_USERNAME --docker-password=DOCKER_PASSWORD --docker-email DOCKER_EMAIL
```

# CBP Clone, Build & Push pipeline

## Tasks

### [git-clone](https://github.com/tektoncd/catalog/tree/v1beta1/git#git-clone/)

```bash
kubectl apply -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/git-clone/0.9/git-clone.yaml
```


### [kaniko](https://github.com/tektoncd/catalog/tree/main/task/kaniko)
build an image and push it to a container registry

```bash
kubectl apply -f https://raw.githubusercontent.com/tektoncd/catalog/main/task/kaniko/0.6/kaniko.yaml

```

#### error:

* https://github.com/GoogleContainerTools/kaniko/issues/2146
```shell
# step-build-and-push	
container has runAsNonRoot and image will run as root
gcr.io/kaniko-project/executor@sha256:c6166717f7fe0b7da44908c986137ecfeab21f31ec3992f6e128fff8a94be8a5

# https://github.com/GoogleContainerTools/kaniko/blob/main/deploy/Dockerfile

```

#### [DOCKER_CONFIG](https://github.com/tektoncd/pipeline/pull/706)



# TODO
Add some extra tasks:
* [Scan an image for vulnerabilities with Red Hat Advanced Cluster Security](https://hub.tekton.dev/tekton/task/rhacs-image-scan)
