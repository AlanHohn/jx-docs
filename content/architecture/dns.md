---
title: DNS
linktitle: DNS
description: Configuring DNS for external access to cluster services
date: 2019-06-24
publishdate: 2019-06-24
lastmod: 2019-06-24
menu:
  docs:
    parent: "architecture"
    weight: 100
weight: 100
sections_weight: 100
draft: false
toc: true
---

To be able to access services hosted within your cluster we default to an [nip.io](https://nip.io/) domain. This makes it super easy to setup and manage DNS.

However, for users who want services in the cluster to be available on a personal domain, we use external-dns which is just as easy.

## external-dns
**NOTE**: *Currently only supported on GKE*

[ExternalDNS](https://github.com/kubernetes-incubator/external-dns) can be used to help expose Kubernetes Services and Ingresses by syncronising with DNS providers. To setup your cluster using ExternalDNS:

```
jx install --provider gke --tekton --external-dns
```

*This will then prompt you for your domain.*

```bash
🙅 developer ~/go-workspace/jx(master)$ jx install --provider gke --tekton --external-dns
WARNING: When using tekton, only kaniko is supported as a builder
Context "gke_<your-project-id>_europe-west1-b_<your-cluster-name>" modified.
set exposeController Config URLTemplate "{{.Service}}-{{.Namespace}}.{{.Domain}}"
Git configured for user: **********  and email *********@****.***
helm installed and configured
? Provide the domain Jenkins X should be available at: your-domain.com
```

A CloudDNS managed zone is then created within your clusters GCP Project, the record-sets which expose your services will be created by ExternalDNS within this managed zone.

```
🙅 developer ~/go-workspace()$ gcloud dns managed-zones list
NAME                           DNS_NAME                   DESCRIPTION                       VISIBILITY
your-domain-com-zone           your-domain.com.           managed-zone utilised by jx       public
```

### delegation

Once the installation is complete, a list of name servers will be outputted to the terminal, please update your registrar using these name servers in order to delegate your domain onto Google CloudDNS.

```
nameservers output
```

### url template

All services should be available on the same domain, of which is derived as follows:

```
<service>-<namespace>.<your-domain>
```
