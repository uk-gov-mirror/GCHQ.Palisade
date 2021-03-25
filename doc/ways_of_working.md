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

# Ways of Working

## Contents
1. [Git branching model](#git-branching-model)
1. [Issues](#issues)
1. [Pull requests](#pull-requests)
1. [Coding style](#coding-style)

## Git branching model
We have adopted the following branching strategy:  
[Git Branching Model](https://nvie.com/files/Git-branching-model.pdf)

## Issues 
A pull request should correlate to a single GitHub issue.  
An issue should relate to a single functional or non-functional change - changes to alter/improve other pieces of functionality should be addressed in a separate issue in order to keep reviews atomic.
The reasoning behind code changes should be documented in the GitHub issue. 
All resolved issues should be included in the next GitHub milestone, this enables releases to be linked to the included issues.
If a code change requires users to make changes in order for them to adopt it then the issue should be labelled 'migration-required', and a comment should be added similar to:

```
### Migration Steps

[Description of what needs to be done to adopt the code change with examples]
```

#### Workflow
* Assign yourself to the issue
* Create a new branch off develop using pattern: gh-[issue number]-[issue-title]
* Commit your changes prefixing your commit title with: gh-[issue-number] - [commit title]
* Check your changes
* Create a pull request to merge your branch into develop (and assign label in-review to your issue)
* The pull request will be reviewed and following any changes and approval your branch will be merged into develop, and the branch deleted
* Close the issue - add a comment saying it has been merged into develop

## Pull Requests
Pull requests will undergo an in depth review by a Palisade committer to check the code changes are compliant with our coding style. 
This is a community so please be respectful of other members - offer encouragement, support and suggestions. 

As described in our git branching model - please raise pull requests to merge you changes into our **develop** branch.

Please agree to the [GCHQ OSS Contributor License Agreement](https://github.com/GovernmentCommunicationsHeadquarters/Gaffer/wiki/GCHQ-OSS-Contributor-License-Agreement-V1.0) before submitting a pull request.

## Coding style
Please ensure your coding style is consistent with rest of the project and follow coding standards and best practices.

In particular please ensure you have adhered to the following:
* Strive for small easy to read and understand classes and methods.
* Separate out related classes into packages and avoid highly coupled classes and modules.
* Checkstyle is run as part of 'mvn package', so you should ensure your code is compliant with these. The project will not build if there are issues which cause these plugins to fail.
* Classes and methods should comply with the single responsibility principal.
* Avoid magic numbers and strings literals.
* Avoid coupling services, if necessary duplicate code so individual services can be updated without causing cascading issues.
* Look after your streams - if you open one make sure you close it too. This should apply to all volatile resource usage.
* Don't swallow exceptions - ensure they are logged or rethrown.
* Give credit for other peoples work.
* Update the NOTICES file for changes to the dependencies.
* Consider the scope of dependencies - restrict them when possible using the appropriate maven scope.
* Don't expose private logic in classes through public methods.
* Try to avoid static classes/methods.
* Field access should be controlled via getters and setters.
* Make use of the core Java API - don't reinvent the wheel.
* Make use of generic typing.
* Make use of appropriate object oriented design patterns.
* Use Loggers instead of System.out.print and Throwable.printStackTrace.
* Ensure that the toString(), equals() and hashCode() methods are implemented where appropriate.
* Files should have appropriate licences.

#### Javadoc
Ensure your java code has sufficient javadocs explaining what the section of code does, and the intended use of it. 
Javadocs should be used in addition to clean readable code, it is not an excuse to write lazy code.

In particular:
* All public classes (not required for test classes unless an explanation of the testing is required)
* public methods
* public constants

#### Tests
* All new code should be sufficiently covered by tests. 
  In the few cases where this will is not possible - steps to verify the code should be thoroughly documented.
* Tests should cover edge cases and exception cases as well as normal expected behavior.
* Keep each test decoupled and don't rely on tests running in a given order - don't save state between tests.
* Overall for a given code change aim to improve the code coverage.
* Unit test classes should test a single class and be named following JUnit5 naming standards, test[TestName]
* Tests should be readable and self documenting where possible. 
* Each test should focus on testing one small piece of functionality invoked from a single method call. 
* Unit tests should use [JUnit 5.x.](https://junit.org/junit5/) and assertions use the [AssertJ library](https://assertj.github.io/doc/)
* We suggest the following pattern:

  ```java
  @Test
  public void testShould[DoSomething|ReturnSomething] {
      // Given
      [Setup your test here]

      // When
      [Invoke the test method]

      // Then
      [assert the method did what was expected]
  }
  ```
* For the breakdown of the different test cases, consider the following:
  * Unit Tests evaluates the smallest piece of testable software in the application
  * Component Tests are intended to a test sub-section of a microservice
  * Contract Tests are intended to verify that the result produced by an outbound service is in keeping with the demands of a consuming service
  * End-to-End Tests are intended to ensure (by testing the system in its entirety) that the system is fully capable of serving its business purposes and is in keeping with any external requirements.
  * Exploratory Tests are manual but documented explorations of the system 