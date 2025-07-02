# turingpi-homelab
Repo for turingpi homelab using argocd's app-of-apps pattern

## Install

```
git clone https://github.com/kenadaddy/turingpi-homelab
cd turingpi-homelab/
helm repo add argocd https://argoproj.github.io/argo-helm
helm dependency build charts/argo-cd
helm install argo-cd charts/argo-cd \
    --namespace argocd \
    --create-namespace
helm template apps/ | kubectl apply -f -
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```

## Update charts

```bash
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update charts/argo-cd
```
