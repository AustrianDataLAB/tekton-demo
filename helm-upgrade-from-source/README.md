## TODO

**Tekton ingress**

Create a new tekton task, which will create a ingress manifest file that would be deployed in the kubernetest cluster.

See also: https://hub.tekton.dev/tekton/task/kubernetes-actions

**Linter** 

add this task to our steps before deploying the helm - this will check if the files are valid.

see task: https://hub.tekton.dev/tekton/task/yaml-lint
