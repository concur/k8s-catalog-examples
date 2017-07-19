# k8s-catalog-examples
Examples of how the 
[Kubernetes Service Catalog](https://github.com/kubernetes-incubator/service-catalog)
can be used with existing
[cloud foundry service brokers](https://docs.cloudfoundry.org/services/examples.html). 

### Why use Service Catalog?
This pattern works incredibly well for providing access to external resources
from any services running on your various Kubernetes clusters and even resources
running on any other system in your environment that supports the
[Open Service Broker API](https://github.com/openservicebrokerapi/servicebroker)
from Cloud Foundry.

Developers can indicate that they need access to a service in the catalog and
at runtime are provided with the correct details to connect to the external resource.
Service brokers create the external resource when it doesn't yet exist, provide the
details of how to connect to it (via a Kubernetes secret currently) and handle
removing it when it's no longer needed (where it makes sense). This enables
[12-factor apps](https://12factor.net/) to consume external services in a declarative
way just like they can with services running natively on Kubernetes.

### [Vault](vault)
[Hashicorp](https://www.hashicorp.com/) developed a service broker for
[Vault](https://www.vaultproject.io/) on Cloud Foundry. It provides connectivity
information, credentials for accessing Vault with various scoped locations (full private,
shared read/write for org, global read only) and access to a
[cryptography as a service](https://www.vaultproject.io/docs/secrets/transit/) backend.