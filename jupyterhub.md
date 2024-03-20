# JupyterHub

JupyterHub is a multi-user server-hosted Jupyter notebook environment. The OBIS JupyterHub is hosted at <https://jupyter.obis.org>. After registration and approval by the administrators, you will be able to access the hub and create R and Python notebooks. Users also have access to example notebooks and datasets in a shared folder.

```mermaid
flowchart LR
    Dockerfile.hub
    Dockerfile.obis-notebook
    shared_folder
    data_folder
    scratch_folder
    subgraph hub
    hub_container
    end
    subgraph notebook_user1
    container_user1
    end
    subgraph notebook_user2
    container_user2
    end
    Dockerfile.hub-..->hub_container
    Dockerfile.obis-notebook-..->container_user1
    Dockerfile.obis-notebook-..->container_user2
    hub_container-->container_user1
    hub_container-->container_user2
    data_folder-->container_user1
    data_folder-->container_user2
    scratch_folder-->container_user1
    scratch_folder-->container_user2
    shared_folder-->container_user1
    shared_folder-->container_user2
    style Dockerfile.hub fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style Dockerfile.obis-notebook fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style shared_folder fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
    style data_folder fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
    style scratch_folder fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
```

## Creating and running a notebook

[to be added]