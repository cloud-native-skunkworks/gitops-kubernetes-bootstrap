## gitops-cluster-bootstrap

<img src="images/1.png" width="450px;">

This is an app-of-apps style start up repository for ArgoCD.

The goal is to setup a production like set of workloads ( observability, security and example applications ).

## Workloads

<img src="images/4.png" width="450px;">

Workloads deployed through ArgoCD.
Configuration of the application is done via the `bootstrap` root app that has it's own configuration within `values.yaml`. This is propagated into the child apps.

When looking at the wider business context, we see how the applications in this repository can feed more broadly back into the business.

<img src="images/6.png" width="1000px;">

### GitOps

As mentioned this repository focuses on gitOps with Argocd.
Below is an example of the applications deployed in various waves.

<img src="images/5.png" width="650px;">


## Prerequisites

- Join the Komodor community slack [here](https://join.slack.com/share/enQtMzkxODc1NTc0OTgzMS1lN2RkNmVlZjJiYmU5NGE0NDVhOTEzMzFjOGVlMzk3NzY0NzU4ZGU2YjBhYzZhNGIyZTUyNjZiYmM2NDFkZjY0)
- Spin up a Kubernetes cluster on your favourite cloud provider or hardware

- Setup argocd

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
- Add this repository as a bootstrap cluster
```
kubectl apply -f bootstrap.yaml
```


### Custom values

Check `values.yaml` and adjust as required

## Credits

Prometheus CRD's when used with ArgoCD apply can get big, so here is a hack to get arond the sync errors
Thanks to [this](https://blog.ediri.io/kube-prometheus-stack-and-argocd-23-how-to-remove-a-workaround) guide.

### Software tooling BOM

- kubectl
- kubectx
- k9s
- jq
- kustomize
- helm
- sshuttle