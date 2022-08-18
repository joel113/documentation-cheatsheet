# Kubernetes Cheat Sheet

https://kubernetes.io/de/docs/reference/kubectl/cheatsheet/

## PODs

`kubectl run -i -tty busybox --image=busybox -n namespace -- sh`

`kubectl run -i -tty alpine --image=alpine -n namespace -- sh`

`kubectl get pod -o="custom-columns=NAME:.metadata.name,INIT-CONTAINERS:.spec.initContainers[*].name,CONTAINERS:.spec.containers[*].name" -n namespace` - Shows a list of pods in the namespace including the containers

`kubectl cp alpine:message.avro ~/message.avro` - copies a file from a pod to the local directory

`kubectl get pods -n namespace -o=custom-columns=NAME:.metadata.name | grep "flink" | xargs -I POD kubectl delete pod POD -n namespace` - Deletes a range of pods depending on the name`

## Deployments

`kubectl get deployments`

`kubectl scale deployment <deploymentname> --replicas=1`

## Config Maps

`kubectl describe configmap/configmapname -n namespace` - Shows the config map configmapname

## Logs

`kubectl logs pod/foobar container-name -n namespace --follow` - Show logs of foobar pod and container-name container

`kubectl logs deployment/foobar -c app -n namespace --follow` - Show logs of foobar deployment

## Secrets

`kubectl get secret/keystore -o jsonpath='{.data}' -n tsmb | jq '."keystore.p12"' | tr -d \" | base64 -decode > keystore.p12`

## Custom Resource Defintions

`kubectl apply -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/master/bundle.yaml' - Applies the custom resource definition at the given url

`kubectl get crds` - Gets the state of the crd requests

`kubectl get api-resources` - List the api resources managed by the cluster

## Cluster Access

`kubectl port-forward svc/alertmanager-operated 9093:9093` - Forwards the given service port to localhost 9093

## Cert Manager

`kubectl get issuer` - Gets the issuer of the cert manager

`kubectl get clusterissuer` - Gets the cluster issuer of the cert manager

`kubectl describe certificaterequest example-com-2745722290` - Returns more information about a specific certificate request

`kubectl describe order example-com-2745722290-439160286` - Returns more information about a specific order

`kubectl describe challenge example-com-2745722290-4391602865-0` - Returns more information about a specific challenge

## Context

`kubectl config view` - Shows kubectl config configuration

`kubectl config view -o jsonpath='{.users[].name}'` - Shows user names in kubectl config configuration

`kubectl config use-context my-cluster-name` - Sets the current context to my-cluster-name

`kubectl config unset current-context` - Resets the current context

## Kustomize

`kustomize build .` - Performs a kustomize build

`kustomize build . | kubectl apply -f -` - Performs a kustomize build and passes the result to kubectl apply
