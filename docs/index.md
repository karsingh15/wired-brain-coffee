<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-e2e-ms-package">About E2E MS Package</a>
      <ul>
        <li><a href="#end-to-end-flow-that-package-provides">End to End flow that package provides</a></li>
        <li><a href="#services-in-the-package">Services in the package</a></li>
        <li><a href="#libraries-in-the-package">Libraries in the package</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Usage</a>
      <ul>
       <li><a href="#when-to-use">When to use this package</a></li>
       <li><a href="#how-to-use">How to use this package</a></li>
      </ul>
    </li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## About E2E MS Package
Within an event-driven architecture, before the team starts implementing the loosely coupled microservices, they often need to agree on the best practices and the standards they are going to follow for each microservice. Also, they often have to build a lot of foundational elements.

This package provides such foundational elements to the developers so that developers can start writing the domain logic from day 1 instead of worrying about the cross-cutting concerns such as logging, application configuration, project structure, project dependencies, gradle configuration, database integration, Kafka integration, PACT integration etc.
With the help of this package, the team can get a microservice up and running within a few seconds.

This package provides implementation of the architecture defined [here](https://tools.publicis.sapient.com/confluence/display/DIAT/Backend+Design).
As part of this package, comes a Spring boot-based system API and GraphQL-based experience API implementations comprising all the best practices mentioned at the aforesaid link. Along with the APIs, this package comes bundled with a few custom libraries that provide sample integrations with various technologies such as

### End to End flow that package provides
![End to End flow](src/main/resources/images/endtoendflow.png)
### Services in the package

Service Name  | Features                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Roadmap
------------- |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------
**System API**    | This is a Spring Boot based service that provides implementations for: <ul><li>Integration with the messaging frameworks (Spring Kafka, OCI Streaming)</li><li>Integration with Resilience Library for Ciruit Breaking</li><li>Ciruit Breaking at Kafka Consumer Level</li><li>Integration with Vaults (OCI, Azure)</li><li>Integration with Azure Blob Store</li><li>Integration with MySQL and Spring Data</li><li>Idempotency handling for POST requests</li><li>Headers propagation to support distributed tracing</li><li>Gradle configuration for separate functional and unit test coverage</li><li>Reference implementation of tests with embedded Kafka and Redis</li><li>Reference implementation of PACT based contract tests</li></ul> |<ul><li>Integration with more databases (Postgres)</li><li>Integration with GCP and AWS services</li><li>Integration with Azure App Insights for custon metrics</li><li>Pipeline to deploy on the Kubernetes Cluster</li></ul>
**Experience API** | This is a Spring Boot based GraphQL service that provides implementations for: <ul><li>Integration with Netflix DGS</li><li>Consistent BFF exception handling</li><li>Reference implementation of PACT based contract tests</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | <ul><li>Pipeline to integrate with the Apollo Studio</li><li>Pipeline to deploy on the Kubernetes Cluster</li></ul>
**Process API** | This is a Spring Boot based service that provides implementation for a configuration driven orchestration workflow                                                                                                                                                                                                                                                                                                          | <ul><li>Pipeline to deploy on the Kubernetes Cluster</li></ul>
**Fintech Event Handler** | This is a Spring Boot based service that converts a REST call into a Kafka event. It is generally used to receive webhook events from the Fintechs. All validations before rasing an event are configuratiuon based. To receive a new type of event (as a REST call), one just need to add the configuration without changing even a single line of code                                                                                                                                                                                                                                                                                                                                                                                                                                                         | <ul><li>Pipeline to deploy on the Kubernetes Cluster</li></ul>

### Libraries in the package

Library Name  | Features | Roadmap
------------- |---------------|---------------
**Events Library**    | This library provides the following functionalities: <ul><li>Provides an abstraction over Spring Kafka by exposing easy-to-use functions for publishing and consuming the messages</li><li>Extends the resilience4j library to support circuit breaking at the Kafka consumer level instead of just at the HTTP layer</li><li>Provides integration with OCI streaming</ul> |  <ul><li>Integration with schema registry</li></ul>
**Bff Library**    | This library provides the following functionalities: <ul><li>Capability to add GraphQL query in the ditributed trace</li><li>Consistent exception handling for GraphQL services</li></ul> |
**Webclient Library**    | This library provides an encapsulation on Spring WebClient and adds project-specific exception handling and logging capabilities to it |  <ul><li>Abstraction on top of other HTTP clients like OKHttp/Retrofit</li></ul>
**Azure Blob Store Library** | This library provides the following functionalities: <ul><li>A way to connect with the multiple Azure Blob Stores. Multiple Blob Stores can be configured and the relevant configuration is picked based on the URL used to read the file</li><li>Standardizes the way to conenct with the Azure Blob Store instead of each team writing their own implementation</li></ul> |
**OCI Vault Library** | This library provides integration with OCI Vault and auto refresh the bean config if the values change in the vault</li></ul> |
**Idempotency Library** | This library leverages AspectJ and provides annotations to make any method Idempotent. Internally it expects Redis configuration in the service to support idempotency</li></ul> |

<!-- Usage -->
## Usage

### How to use
To help with the usage of the package, it comes bundled with a JavaFX-based service generation functionality. Using this generator, any of the above services or libraries can be cloned to be used in the project.
To start the generator, clone the package and run the MyLauncher.java class
To build any library or system api, please add following as environment properties:
- MinimumUnitTestsInstructionCoverage=0.50
- MinimumComponentTestsInstructionCoverage=0.50
- PactBrokerUrl=https://<PACT-FLOW-URL>
- PactAuthenticationToken=<PACT AUTH TOKEN>
- SONAR_TOKEN=<SONAR TOKEN>


## Contact
- Sahil Goel - sahil.goel11@publicissapient.com
- Suresh Poonia - suresh.poonia@publicissapient.com
- Saida Reddy Mutana - saidareddy.muttana@publicissapient.com 
- Elankeeran Vaitiyanathan - elankeeran.vaithiyanathan@publicissapient.com
- Hitesh Mohan Nagrani - hitesh.nagrani@publicissapient.com
