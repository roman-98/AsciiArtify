### Демо ArgoCD

Демо-інструкція на отримання доступу до інтерфейсу ArgoCD:

![Image](../.data/argo-setup.gif)

```sh
k3d cluster create argo
k create namespace argocd
k apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
k get all -n argocd
k get pod -n argocd -w
k get all -A
k port-forward svc/argocd-server -n argocd 8080:443&
k -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
k -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo
```