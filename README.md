# Presequence
Assuming your cluster already have tekton installed.

**Run this config to override default configs for tekton pipelines.**
```bash
kubectl apply -f extra/config-defaults.yml
```

# Pipelines

## CPPC (Clone, Package & Push Helm charts)
[CPPC](cppc/README.md) Pipeline will **clone** a repository where a helm chart is located, **packages** the helm chart and **push** to the desired **registry**.

...

## Install Helm chart from URL
[helm-upgrade-from-repo](helm-upgrade-from-repo/README.md) Pipeline will **deploy your helm package from repo url**.

...

## Clone & install Helm chart
[helm-upgrade-from-source](helm-upgrade-from-source/README.md) Pipeline will clone a repository where a Helm chart source code is located, and install it to the cluster.

...
