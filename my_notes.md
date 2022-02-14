# Introduction
## What is ArgoCD?

* Argo is a GitOps CD tool for Kubernetes specifically.

## Getting Started

* Review this video: https://www.youtube.com/watch?v=MeU5_k9ssrs
* Install Argo CD using this resource: https://argo-cd.readthedocs.io/en/stable/getting_started/
    ```
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```
* Forward port to ArgoCD server
    ```
    kubectl port-forward -n argocd svc/argocd-server 8080:443
    ```
* Navigate to https://localhost:8080 using your browser
* Get the initial password for the `admin` account
    ```
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
    ```
* Login to the ArgoCD dashboard
* Clone this repo to your own copy in Github or BitBucket: https://gitlab.com/nanuchi/argocd-app-config
* Edit `application.yaml` to point to your new repo and push it to your repo.
* Apply the `application.yaml` using `kubectl`.
    ```
    kubectl apply -f application.yaml
    ```
* Go back to the ArgoCD dashboard in your browser. You should see the application was created.

## What are Argo Rollouts?

* Argo Rollouts is a progressove delivery controller for Kubernetes
* Provides blue-green and canary update strategies
* Integrates with service meshes and ingress controllers to shape traffic.
* Automates promotion and rollback based on analysis
* See https://www.youtube.com/watch?v=hIL0E2gLkf8 for demo and overview.
