## gitops-cluster-bootstrap

<img src="images/1.png" width="450px;">
This is an app-of-apps style start up repository for ArgoCD.

The goal is to setup a production like set of workloads ( observability, security and example applications ).

To get going with a Kubernetes cluster running ArgoCD, run the following:

`kubectl apply -f bootstrap.yaml`

## Prerequisites

- MicroK8s as either stand alone or cluster
- Distributed storage on MicroK8s `microk8s enable mayastor`
## Hacks

Prometheus CRD's when used with ArgoCD apply can get big, so here is a hack to get arond the sync errors
Thanks to [this](https://blog.ediri.io/kube-prometheus-stack-and-argocd-how-workarounds-are-born) guide.

kubectl replace -k  hacks/ -n observability
