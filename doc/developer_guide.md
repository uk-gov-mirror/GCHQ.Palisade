<!---
Copyright 2018-2021 Crown Copyright

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
--->

# Developer Guide

### Getting Started
#### Build prerequisites:
* [Java 11](https://openjdk.java.net/projects/jdk/11/) (OpenJDK 11) has been used for the development of Palisade
* [Git](https://git-scm.com/) access to repositories listed below
* [Maven](https://maven.apache.org/) for the Java compile/test build process

#### Deploy prerequisites:
* [Docker](https://www.docker.com/) for building containers
* [Kubernetes](https://kubernetes.io/) for cluster orchestration and container management
* [Helm 3](https://helm.sh/) for deploying to Kubernetes and managing deployments
 

### GitHub Repositories
The Palisade project has been divided into a set of separate GitHub repositories for simplification of development and maintenance.
They consist of the following:

[Palisade](https://gchq.github.io/Palisade)  
Documentation for how Palisade works at a high level, considered the landing spot for new members coming to the Palisade Project

[Palisade Services](https://github.com/gchq/Palisade-services)  
Contains the various different Micro Services required to run Palisade, apply rules and policies, verify users and retrieve resources 

[Palisade Clients](https://github.com/gchq/Palisade-clients)  
Client code for using Palisade from different data processing technologies, different language libraries, or slightly different implementations each with pros and cons.

[Palisade Examples](https://github.com/gchq/Palisade-examples)  
Code examples showing an examples of how Palisade can be used in different deployments

[Palisade Readers](https://github.com/gchq/Palisade-readers)  
Library of code for connecting Palisade into different data storage technologies

[Palisade Integration Tests](https://github.com/gchq/Palisade-integration-tests)  
Contains larger, external tests that are run as part of our CI/CD pipeline.
//TODO link high level test strategy


Palisade Readers, Clients, and Services are all required to run the existing solution.
The examples provide a demonstration of how the automated policy rule enforcement is applied to data being read by a user.
The examples will provide a good start to understanding how Palisade works.

For an overview of the examples code see [here](https://github.com/gchq/Palisade-examples).  
For a quickstart guide to running the examples, see [here](../QUICKSTART.md).


## Contributing
We welcome contributions to the project.
Detailed information on our ways of working can be found [here](ways_of_working.md).

The following gives some useful documentation intended to help with the developer or contributor on-boarding experience.

* [Initial Requirements](initial_requirements.md) - The initial design requirements for Palisade
* [High level architectural diagram](component_descriptions.md) - Shows a high level overview of how the services link together
* [Standard flow for a read request through the Palisade system](read_process.md) - Message Sequence Chart (MSC) covering this flow
* [How might the system be deployed?](deployments.md) - The different ways to deploy Palisade
* [Security considerations](security_considerations.md) - Security considerations to be taken whilst working on Palisade
* [Roadmap for Palisade](roadmap.md) - Where Palisade is heading
* [Ways of Working](ways_of_working.md) - Developer guide to branching strategy and code standards


## License
Palisade is licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0) and is covered by [Crown Copyright](https://www.nationalarchives.gov.uk/information-management/re-using-public-sector-information/copyright-and-re-use/crown-copyright/).


## FAQ
1. What is the version of Java is supported?
   The existing version of the application is built with Java 11.
   It should work with later versions of Java, but this has not been tested and cannot be verified

1. What build environments are supported?
   We do not currently support Windows as a build environment, If you are running on Windows then you will need this: Microsoft Visual C++ 2010 SP1 Redistributable Package
   To support hadoop environments, see the hadoop guide in Palisade-Services/resource-service/[README.md](https://github.com/gchq/Palisade-services/tree/develop/resource-service#hadoop-and-windows)
