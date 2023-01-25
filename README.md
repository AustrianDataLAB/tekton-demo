# Presequence
Assuming your cluster already have tekton installed.

**Run this config to override default configs for tekton pipelines.**
```bash
kubectl apply -f extra/config-defaults.yml
```

# Pipelines

## CPP (Clone, Package & Push)
[CPP](cpp) Pipeline will **clone** a repository where a helm chart is located, **packages** the helm chart and **push** this package to the desired **registry**.

...

## Deploy helm package
[helm-upgrade-from-repo](helm-upgrade-from-repo) Pipeline will **deploy your helm package from repo url**.

...

## Clone & deploy helm chart
[helm-upgrade-from-source](helm-upgrade-from-source) This Pipline will clone a repository where a helm chart source code is located, and deploy it to the cluster.

...

<del> 

## CBP (Clone, Build & Push)
[CBP](cpp) pipeline will clone a repository to a workspace, builds the docker image and push 
this image to the desired registry.

**Apply the pipeline**

```bash
kubectl -n tekton-demo apply -f cbp/cbp-pipeline.yml
```

</del>

...

# TODO
[Install and set up Tekton Triggers](https://tekton.dev/docs/installation/triggers/),
