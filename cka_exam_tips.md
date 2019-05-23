Kubernetes io docs available
Especially know tasks and concepts

Time is of the essence
Grab yaml files from the docs 

Use dry run for generating manifest,
i.e.
kubectl run --image=nginx -o yaml --dry-run

alias k=kubectl
alias kgp=kubectl get pods
alias kgd=kubectl get deployments

kubectl run help docs are great, even better just grep for existing
kubectl run --help | grep kubectl
# you're often asked to create resource of a certain type with a name, can all be done with different restart policies on RUN
kubectl run --help | grep restart


