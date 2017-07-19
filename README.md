# k8s-catalog-examples
Examples of how to the Kubernetes Service Catalog can be used with existing cloud foundry service brokers. 

### Why should I use this?
This pattern works incredibly well for providing access to external resources from any services running on your various kubernetes clusters and even resources running on any other IaaS layer in your environment that supports the Open Service Broker API from Cloud Foundry.

Developers can indicate that they need access to a service in the catalog and at runtime are provided with the correct details to connect to the external resource. Service brokers create the external resource when it doesn't yet exist, provide the details of how to connect to it (via a Kubernetes secret currently) and handle removing it when it's no longer needed (where it makes sense). This enables 12-factor apps to consume external services in a declarative way just like they can with services running on Kubernetes.

### [Vault](vault)
Hashicorp developed a service broker for Vault for Cloud Foundry. It provides connectivity information, credentials for accessing Vault with various scoped locations (full private, shared read/write for org, global read only) and access to an encryption as a service backend.