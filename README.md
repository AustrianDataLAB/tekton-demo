# Presequence
Assuming your cluster already have tekton installed.

**Run this config to override default configs for tekton pipelines.**
```bash
kubectl apply -f extra/config-defaults.yml
```

# Pipelines

## CPPC (Clone, Package & Push Helm charts)
[CPPC](cppc) Pipeline will **clone** a repository where a helm chart is located, **packages** the helm chart and **push** to the desired **registry**.

...

## Install Helm chart from URL
[helm-upgrade-from-repo](helm-upgrade-from-repo) Pipeline will **deploy your helm package from repo url**.

...

## Clone & install Helm chart
[helm-upgrade-from-source](helm-upgrade-from-source) Pipeline will clone a repository where a Helm chart source code is located, and install it to the cluster.

...

<del> 

## CBP (Clone, Build & Push docker images)
[CBP](cbp) pipeline will clone a repository to a workspace, builds the docker image and push 
this image to the desired registry.

**Apply the pipeline**

```bash
kubectl -n tekton-demo apply -f cbp/cbp-pipeline.yml
```

</del>

...

# TODO
[Install and set up Tekton Triggers](https://tekton.dev/docs/installation/triggers/),
