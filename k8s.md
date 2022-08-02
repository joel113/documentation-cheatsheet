# Kubernetes Cheat Sheet

https://kubernetes.io/de/docs/reference/kubectl/cheatsheet/

## PODs

`kubectl run -i -tty busybox --image=busybox -n namespace -- sh`

`kubectl run -i -tty alpine --image=alpine -n namespace -- sh`

`apk --update add curl`

`kubectl cp alpine:message.avro ~/message.avro` - copies a file from a pod to the local directory

## Deployments

`kubectl get deployments`

`kubectl scale deployment <deploymentname> --replicas=1`

## Logs

`kubectl logs deployment/foobar -c app -n namespace --follow` - show logs of foobar deployment

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
