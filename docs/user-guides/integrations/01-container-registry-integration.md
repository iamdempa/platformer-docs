---
id: 01-container-registry-integration
title: Container Registry Integration
sidebar_label: Container Registries
slug: container-registry-integration
---

## Introduction

Once a Container Registry is connected to your Platformer Project, you can use it across any of your Environments and Clusters under the same Project, even if they are hosted with different infrastructure providers.

### Supported Container Registry Providers

-   Docker
-   Google Container Registry (GCR)
-   AWS Elastic Container Registry (ECR)
-   Azure Container Registry (ACR)
-   Github
-   Harbour
-   Custom registries (any JSON-based configs)

![](/assets/images//docs/supported-registries.png)


## Integrating a Container Registry to your Project

To integrate a new container registry to the Platformer Console, navigate to **Credentails** > **Container Registries** and click **+ CREDENTIAL** (or **Get started** if you haven't added one before)

!!! important
    The required credentials or service account permissions will vary from provider to provider. Please refer to your registry providers documentation for the required permissions.

![](/assets/images//docs/integrations-1.png)
