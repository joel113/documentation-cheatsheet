# AWS Cheatsheet

## Shell Functions

```
# AWS Profiles
function aws-profiles {
        grep '\[profile .*\]' ~/.aws/config | cut -c10- | tr -d [ | tr -d ]
}

function set-aws-profile {
        readonly profile=${1:?"The aws profile must be specified."}
        export AWS_PROFILE="$profile"
}
```

`aws-profiles` - Returns the available aws profiles

`set-aws-profile profile` - Sets the profile aws profile

```
# AWS Regions
function aws-regions {
        aws get regions
}

function set-aws-region {
        readonly region=${1:?"The region must be specified."}
        export AWS_REGION="$region"
}
```

`aws-regions` - Returns the available aws regions

`set-aws-region region` - Sets the region aws region

```
# K8s Clusters
function aws-k8s-clusters {
        aws eks list-clusters
}

function set-aws-k8s-cluster {
        readonly profile=${AWS_PROFILE:?"The profile must be specified."}
        readonly cluster=${1:?"The cluster must be specified."}
        aws eks update-kubeconfig --profile "$profile" --name "$cluster"
}
```

`aws-k8s-clusters` - Returns the available aws k8s clusters

`set-aws-k8s-cluster cluster` - Sets the cluster aws k8s cluster

```
# K8s Namespaces
function aws-k8s-namespaces {
        kubectl get namespace
}

function set-aws-k8s-namespace {
        readonly namespace=${1:?"The  context mus be specified."}
        kubectl config set-context --current --namespace=$namespace
}
````

`aws-k8s-namespace` - Returns the available aws k8s namespaces

`set-aws-k8s-namespace namespace` - Sets the namespace aws k8s namespace 
