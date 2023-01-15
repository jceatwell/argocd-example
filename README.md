#### Commands

```bash
# install ArgoCD in k8s
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# access ArgoCD UI
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8080:443 -n argocd

# login with admin user and below token (as in documentation):
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

# you can change and delete init password

```

## Create Projects

Using CLI Tool:

```
argocd proj create myproject -d https://kubernetes.default.svc,mynamespace -s https://github.com/argoproj/argocd-example-apps.git
```

## Create application

```
kubectl create -f application.yaml
kubectl -n argocd get applications
```

#### Links

* Example Based repo: [https://gitlab.com/nanuchi/argocd-app-config](https://gitlab.com/nanuchi/argocd-app-config)

* Install ArgoCD: [https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd](https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd)

* Login to ArgoCD: [https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli](https://argo-cd.readthedocs.io/en/stable/getting_started/#4-login-using-the-cli)

* ArgoCD Configuration: [https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/)

* ArgoCD Github Repo [https://github.com/argoproj/argo-cd](https://github.com/argoproj/argo-cd)

* ArgoCD Custom Resource Definitions [https://github.com/argoproj/argo-cd/tree/master/manifests/crds](https://github.com/argoproj/argo-cd/tree/master/manifests/crds)

* Information on HorizontalPodAutoscaler [https://www.densify.com/kubernetes-tools/kustomize](https://www.densify.com/kubernetes-tools/kustomize)
