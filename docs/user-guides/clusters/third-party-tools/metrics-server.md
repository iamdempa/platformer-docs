---
title: Setting up Metrics Server
---

Platformer Console support Kubernetes native metrics to display current Pod Utilization metrics. It also supports [Horizontal Pod AutoScaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)

## Before you begin

- Ensure that you have a cluster connected at Platformer Console. [Read more on Cluster Connection here](/user-guides/clusters/03-connecting-clusters/)

## Installing using Platformer Shell

1. [Access Kubectl Shell from the Console](/user-guides/clusters/04-kubectl-shell/)

4. Run the following commands to install the metrics server.

    ```
    helm repo add stable https://kubernetes-charts.storage.googleapis.com
    ```

    ```

    helm install --namespace kube-system  metrics-server stable/metrics-server \
    --set "args[0]=--logtostderr,args[1]=--kubelet-preferred-address-types=InternalIP,args[2]=--kubelet-insecure-tls"  
    ```

    !!! hint
        You can change the passed in variables any way you want. Please refer [NGINX Ingress Helm Repository](https://github.com/helm/charts/tree/master/stable/nginx-ingress)

## Manual Installation

Please follow the steps for your specific Kubernetes infrastructure provider: [Metrics Server Installation Guide](https://github.com/kubernetes-sigs/metrics-server)
