# Red Hat - Authorino

Install Red Hat - Authorino.

Do not use the `base` directory directly, as you will need to patch the `channel` based on the version of OpenShift you are using, or the version of the operator you want to use.

The current *overlays* available are for the following channels:

* [managed-services](operator/overlays/alpha)
* [stable](operator/overlays/stable)

## Usage

If you have cloned the `gitops-catalog` repository, you can install Red Hat - Authorino based on the overlay of your choice by running from the root (`gitops-catalog`) directory.

```
oc apply -k authorino-operator/operator/overlays/<channel>
```

Or, without cloning:

```
oc apply -k https://github.com/redhat-cop/gitops-catalog/authorino-operator/operator/overlays/<channel>
```

As part of a different overlay in your own GitOps repo:

```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
  - https://github.com/redhat-cop/gitops-catalog/authorino-operator/operator/overlays/<channel>?ref=main
```