# 5.0 Introduction to multi-cloud orchestration capabilities

In the past two years, with the maturity of public cloud services and the differentiation of cloud provider products, many enterprises have begun to adopt hybrid IT and multi-cloud solutions in order to improve efficiency and maintain competitive advantages in the digital transformation team, thus Accelerate the pace of your multicloud strategy.
Distributed applications and workloads that were previously centralized in on-premises data centers are redefining traditional data center boundaries and forcing application modernization and infrastructure expansion to accommodate increasingly distributed workloads.
Relying on a combination of private clouds, multiple public clouds, and traditional infrastructure platforms, businesses are free to choose a cloud based on their specific strengths, benefiting from the specific strengths of each cloud provider.
In this way, build the most suitable application architecture for the enterprise, so as to ensure high service availability, enhance application elasticity, and increase load capacity.
Of course, enterprises can also reduce the risk of downtime of a single cloud provider by building redundant deployments to achieve rapid failover.

![Multi-cloud capabilities](https://docs.daocloud.io/daocloud-docs-images/docs/blogs/images/kairship04.png)

In the face of complex multi-cloud environments, 5.0 multi-cloud orchestration will bring us consistent cluster operation and maintenance, reduce management burden; cross-cluster application distribution capabilities, break data islands, and realize application cross-cluster level disaster recovery deployment.

## Features

The main functions of multi-cloud orchestration are as follows:

**Multi-cloud cluster instance management**

- One-click deployment of multi-cloud cluster instances, quickly deploy enterprise-level Karmada clusters through the web interface, support the creation of multiple Karmada instances, and they work at the same time, and the instances are not aware of or affect each other.
- One-click import of working clusters, which supports one-click import of clusters from Kpanda's existing managed clusters to Karmada instances, and real-time synchronization of the latest information of Kpanda clusters.
- An overview of the instance information, which supports viewing the CPU and memory usage of the connected working clusters in the instance.
- Working cluster management, which supports dynamic addition of new clusters to Karmada instances; support for dynamic removal of specific clusters from Karmada.
- CloudShell, which supports obtaining KubeConfig link information, and users can manage Karmada instances on the local terminal.
- Karmada native API support, supports all Karmada native APIs.

**Multi-cloud workloads**

- Supports interface-based creation of stateless workloads, adding differentiated configurations and distribution strategies
- Support viewing the deployment details of stateless workloads, single Pod monitoring, and log information
- Application failover, built-in application multi-cloud failover capability
- Cross-cluster workload distribution, rich multi-cloud application distribution strategy and coverage strategy
- Observability, rich auditing, Metrics exposure

**Resource Management**

- Support multi-cloud namespace management
- Support multi-cloud storage statement management
- Support multi-cloud configuration, key management
- Support multi-cloud Service and Ingress resource management

**Strategy Center**

Support deployment policy and differentiated policy management, view the workload associated with the policy, and provide the function of deleting idle deployment policies and differentiated policies.

## Graphical user interaction

The multi-cloud orchestration module is an aggregation platform for multi-cluster management, which supports users to access clusters from different vendors and regions for unified management.
Help enterprises quickly deploy workloads across clusters, and meet user scenarios such as cross-cluster management and disaster recovery deployment.
In terms of hierarchical structure, a two-level architecture is adopted. The top layer extracts the list of multi-cloud clusters. Select to enter the multi-cloud cluster management center to view overview, work cluster management, multi-cloud workload, resource management, and policy center.

On the multi-cloud cluster instance list interface, users can clearly perceive real-time information such as the running status, resource usage, and number of clusters of each multi-cloud cluster instance.
And can enter details based on multi-cloud cluster instance name. At the same time, if users want to use kubectl to manage the cluster, they can also use the Cloudtty desktop console tool on the interface.

On the `Overview` interface, users can view detailed cluster overview information, health status of cross-cluster workloads, resource information, etc.

On the `work cluster management` interface, users can manage the access clusters of multi-cloud clusters, and can view information such as the status and release version of each cluster.

On the `Multi-Cloud Workload` interface, users can perceive information such as workload status and number of instances under the current multi-cloud cluster with permissions. And you can enter the workload details by name, view logs, monitor, etc.

In the `Resource Management` interface, users can manage services and routes, namespaces, storage declarations, configuration and key modules. These resources are created across clusters to satisfy the resources that the deployment of cross-cluster workloads depends on.

In `Policy Center`, users can view the deployment policies and differentiated policies associated with workloads, but they are not allowed to delete the policies in use.
In addition, users can also customize and create deployment strategies and differentiated strategies to unlock advanced usage modes.

## What can multi-cloud orchestration do

You can manage multi-cloud orchestration through the Web UI. You can use the multi-cloud orchestration module to implement functional operations such as creating multi-cloud cluster instances, accessing clusters, and deploying applications across clusters.
Among them, the capability of multi-cloud workloads is fully aligned with Kubernetes workloads.

**Create a multi-cloud cluster**

In the multi-cloud orchestration module, users can create a multi-cloud cluster instance with one click, and then access and remove the working cluster on the details page after the instance is successfully created. At the same time, the expulsion of workload can be achieved by marking the working cluster with stains.

**Access member cluster**

The multi-cloud orchestration will synchronize all the clusters that have been connected to the container management module. The user only needs to click the "Connect to Cluster" button at the working cluster of the multi-cloud cluster instance, select the cluster to be connected, and click "Confirm". access operation.

**Deploy multi-cloud workloads**

The multi-cloud orchestration module supports Kubernetes-native workload type deployment and management capabilities, including: creation, configuration, expansion, deletion, and other full lifecycle management. In addition, it supports differentiated configuration of clusters, allowing users to easily handle the configuration management of different clusters.

- **Instance Scheduling Policy**

     Currently, multi-cloud orchestration supports the deployment of instances to the cluster selected by the user in the form of replication, that is, the number of instances is configured as 2, and two working clusters, Cluster A and Cluster B, are selected. A workload with 2 instances is deployed on B at the same time. More instance scheduling strategies will be gradually supported in the future.

- **cluster affinity and anti-affinity**

     Users can select clusters by region and availability zone, or by configuring affinity and anti-affinity to achieve more refined cluster selection.

- **differentiated configuration**

     Users can select clusters that require differentiated configurations, and then see the general configurations that have been configured in the previous steps, and modify the configurations in the differential steps so that workloads on different clusters run with different configurations.

- **Resource Management**

     When creating cross-cluster workloads, configuration differences between clusters are inevitable. Therefore, we can create configurations, keys, and storage statements in the resource management module, so that when creating workloads, we can quickly read and perform differentiated configurations. The resource management module also manages namespaces, services and ingress, and these resources will be created across clusters.

- **Strategy Center**

     In the policy center, users can manage deployment policies and differentiated policies created through workload association, and provide the function of deleting idle policies. It also supports maintaining, creating and editing deployment strategies and differentiation strategies in YAML.

## Frequently Asked Questions

- **Q: Which vendors' clusters are compatible with multi-cloud orchestration? **

     A: The 5.0 multi-cloud orchestration is compatible with the vendor clusters supported by the 5.0 container management, including AWS, Google Cloud, Xinchuang architecture, edge-cloud integration, and any standard Kubeneters ApiServer-based distribution container cluster.

- **Q: How to realize the management of clusters of other manufacturers? **

     Answer: By obtaining the KubeConfig file of other vendors' clusters, performing the cluster access operation in the container management module, and filling in the KubeConfig file of the target cluster, the access management of a container cluster in Container Management is completed. Then, in the multi-cloud orchestration module, you can access the cluster newly added to the container management module in the working cluster list of the multi-cloud cluster instance.

     ![Manage KubeConfig](https://docs.daocloud.io/daocloud-docs-images/docs/blogs/images/kairship01.png)

- **Q: How does the application implement cross-cluster communication? **

     A: Currently, the multi-cloud orchestration module does not have a built-in implementation of cross-cluster communication between applications. We can integrate Submariner to flatten the network between connected clusters and achieve IP reachability of pods and services between clusters. Submariner also provides cross-cluster service discovery capabilities through Lighthouse.

- **Q: How to obtain the real-time status of multi-cluster resources? **

     Answer: With the help of the self-developed open source component ClusterPedia, by installing the Agent component on the target cluster, combined with the Watch mechanism, the resource change information of the target cluster can be synchronized to the ETCD of the container management cluster in real time. Multi-cloud orchestration directly queries container-managed ETCD to obtain real-time status of multi-cluster resources.

     ![Get cluster resource status](https://docs.daocloud.io/daocloud-docs-images/docs/blogs/images/kairship02.png)

- **Q: What is the positioning of 5.0 multi-cloud orchestration in the fifth generation of products? **

     Answer: In the fifth-generation product, the multi-cloud orchestration module is at the core of connecting the past and the future. Right: docking with the DCE 5.0 application workbench. For the upper-level scenario-based management module, the multi-cloud orchestration module can expose any standard Kubernetes API, and easily realize cross-cluster application distribution and disaster recovery deployment. For the next: docking container management platform Kpanda, and Kpanda docking Any Kubernetes, such as edge K3S, Xinchuang environment, DCE, DKG, DKE, and external Openshift, Tanzu, CCE, etc., multi-cloud orchestration based on container management module, quick implementation Multi-cluster management.

     ![Positioning](https://docs.daocloud.io/daocloud-docs-images/docs/blogs/images/kairship03.png)

- **Q: Who can create a multi-cloud cluster? **

     A: Users with Global Admin and Kairship Owner roles can create multi-cloud clusters.

[Learn about multi-cloud orchestration](../kairship/intro/what.md){ .md-button }

[Download DCE 5.0](../download/dce5.md){ .md-button .md-button--primary }
[Install DCE 5.0](../install/intro.md){ .md-button .md-button--primary }
[Free Trial](../dce/license0.md){ .md-button .md-button--primary }