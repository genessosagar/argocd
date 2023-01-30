Notes: Installation options
You need to create a namespace for argocd.

kubectl create ns argocd

and then choose one of the below options :

1. Non-HA :

a. cluster-admin privileges: https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

b. namespace level privileges: https://github.com/argoproj/argo-cd/raw/stable/manifests/namespace-install.yaml

kubectl create ns argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get all -n argocd
kubectl get pods -n argocd

- Get Initial admin password
kubectl get secret -n argocd
kubectl get secret -n argocd argocd-initial-admin-secret -o yaml
We will be able to see the password, we need to convert it from base64
https://base64.guru/converter

kubectl get svc -n argocd


* Port Forwarding
Notes: Port Forward
Use this command in order to access Argo CD on your local machine on port 8080
kubectl port-forward svc/argocd-server -n argocd 8080:443
open browser https://localhost:8080/




2. HA:

a. cluster-admin privileges: https://github.com/argoproj/argo-cd/raw/stable/manifests/ha/install.yaml

b. namespace level privileges: https://github.com/argoproj/argo-cd/raw/stable/manifests/ha/namespace-install.yaml

3. Light installation "Core"

https://github.com/argoproj/argo-cd/raw/stable/manifests/core-install.yaml

4. Helm chart: https://github.com/argoproj/argo-helm/tree/main/charts/argo-cd
