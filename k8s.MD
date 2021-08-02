# Kubernetes Cheat Sheet

https://kubernetes.io/de/docs/reference/kubectl/cheatsheet/

## PODs

`kubectl run -i -tty busybox --image=busybox -n namespace -- sh`

`kubectl run -i -tty alpine --image=alpine -n namespace -- sh`

`apk --update add curl`

## Logs

`kubectl logs deployment/foobar -c app -n namespace --follow` - show logs of foobar deployment

## Secrets

`kubectl get secret/keystore -o jsonpath='{.data}' -n tsmb | jq '."keystore.p12"' | tr -d \" | base64 -decode > keystore.p12`
