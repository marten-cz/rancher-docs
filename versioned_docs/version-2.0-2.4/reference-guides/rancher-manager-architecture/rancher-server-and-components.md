---
title: Rancher Server and Components
---

<head>
  <link rel="canonical" href="https://ranchermanager.docs.rancher.com/reference-guides/rancher-manager-architecture/rancher-server-and-components"/>
</head>

The majority of Rancher 2.x software runs on the Rancher Server. Rancher Server includes all the software components used to manage the entire Rancher deployment.

The figure below illustrates the high-level architecture of Rancher 2.x. The figure depicts a Rancher Server installation that manages two downstream Kubernetes clusters: one created by RKE and another created by Amazon EKS (Elastic Kubernetes Service).

For the best performance and security, we recommend a dedicated Kubernetes cluster for the Rancher management server. Running user workloads on this cluster is not advised. After deploying Rancher, you can [create or import clusters](../../pages-for-subheaders/kubernetes-clusters-in-rancher-setup.md) for running your workloads.

The diagram below shows how users can manipulate both [Rancher-launched Kubernetes](../../pages-for-subheaders/launch-kubernetes-with-rancher.md) clusters and [hosted Kubernetes](../../pages-for-subheaders/set-up-clusters-from-hosted-kubernetes-providers.md) clusters through Rancher's authentication proxy:

<figcaption>Managing Kubernetes Clusters through Rancher's Authentication Proxy</figcaption>

![Architecture](/img/rancher-architecture-rancher-api-server.svg)

You can install Rancher on a single node, or on a high-availability Kubernetes cluster.

A high-availability Kubernetes installation is recommended for production.

A Docker installation of Rancher is recommended only for development and testing purposes. The ability to migrate Rancher to a high-availability cluster depends on the Rancher version:

For Rancher v2.0-v2.4, there was no migration path from a Docker installation to a high-availability installation. Therefore, you may want to use a Kubernetes installation from the start.

The Rancher server, regardless of the installation method, should always run on nodes that are separate from the downstream user clusters that it manages. If Rancher is installed on a high-availability Kubernetes cluster, it should run on a separate cluster from the cluster(s) it manages.