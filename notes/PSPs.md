# Pod Security Policy (PSP)

https://www.cncf.io/online-programs/understanding-and-deploying-kubernetes-pod-security-policies/

## ask
```bash
# can i delete node
kubectl auth can-i delete node

# can i create clusterRoleBinding
kubectl auth can-i create clusterRoleBinding

# can i create pod in the namespace discover
kubectl auth can-i create pod -n discover
```

## PSP
```bash
# get current psp
kubectl get psp
```

