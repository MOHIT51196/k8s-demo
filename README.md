# K8S USEFULL COMMANDS

## Create namespace
kubectl create namespace <namespace>

## Expose a pod via service
kubectl expose deployment <deployment name> --type=LoadBalancer --namespace=<namepsace>

## Generate user certificates
openssl genrsa -out <user key name> 2048
openssl req -new -key <user key name> -out <csr name> -subj "/CN=<common name>/O=<organisation>..."
openssl x509 -req -in <csr name> -out <user cert name> -CA <ca cert> -CAkey <ca key> -CAcreateserial -days <days to expire>

## Create a user
kubectl config set-credentials <user name> --client-certificate=<user cert name> --client-key=<user key name>

## Create a user context
kubectl config set-context <context name> --cluster=<cluster name> --user=<user name> --namespace=<namespace>

## Use context
kubectl config use-context <context name>

## Show/add label on node
kubectl get nodes --show-labels
kubectl label nodes <node name> <key>=<value>
