---
title: Hello Minikube
content_type: tutorial
weight: 5
card:
  name: tutorials
  weight: 10
---

<!-- overview -->

This tutorial shows you how to run a sample app
on Kubernetes using minikube and Katacoda.
Katacoda provides a free, in-browser Kubernetes environment.

{{< alert title="Note" >}}
You can also follow this tutorial if you've installed minikube locally.
See [minikube start](https://minikube.sigs.k8s.io/docs/start/) for installation instructions.
{{< /alert >}}

<!-- {{< note >}}this is a test {{< /note>}} -->

teste

## Objectives

* Deploy a sample application to minikube.
* Run the app.
* View application logs.


This tutorial provides a container image that uses NGINX to echo back all the requests.

<!-- lessoncontent -->

## Create a minikube cluster

1. Click **Launch Terminal**


!!! Success "Expected output"
    ```{ .bash .no-copy }
    Hello World!
    ```

??? question "Are you seeing `curl: (6) Could not resolve host: hello.default.${LOADBALANCER_IP}.sslip.io`?"
