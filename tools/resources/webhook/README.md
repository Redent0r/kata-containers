# Kata Admission controller webhook

Implement a simple admission controller webhook to annotate pods with resources requests and limits. Based on
https://github.com/kata-containers/tests/tree/main/kata-webhook

## How to build the admission controller

> **Note:**
> Only run this step if you are modifying the current webhook or don't
> want to use the webhook available in docker hub.

First build the admission controller image and the associated
Kubernetes YAML files required to instantiate the admission
controller.

```bash
$ docker build -t quay.io/kata-containers/kata-webhook-example:latest -f Dockerfile .
```

> **Note:**
> Image needs to be published for the webhook needs to work. Alternately
> on a single machine cluster change the `imagePullPolicy` to use the locally
> built image.

## Setting resources requests and limits using an admission controller

Use the [admission webhook](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/#admission-webhooks)
and sample admission controller we created by running the commands below:


```bash
$ ./create-certs.sh
$ kubectl apply -f deploy/
```
