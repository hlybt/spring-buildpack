# Spring Boot Containerization w Buildpacks

A demo of creating a docker image from application source code. 

There are ways for developers to package an application into a container image. 

Creating a dockerfile seems like a very straightforward solution at first blush. However, writing a dockerfile manually adds extra workload such as image configuration, dependency management, etc. It becomes increasingly complex and error-prone.

Docker images can be built directly from your Maven or Gradle plugin using Cloud Native Buildpacks. 

To achieve this: 

- have Docker installed and running 

- install [Pack](https://buildpacks.io/docs/for-platform-operators/how-to/integrate-ci/pack/) - a CLI tool maintained by the CNB project to support the use of buildpacks

- configure the default builder:

    `pack config default-builder paketobuildpacks/builder-jammy-base`

- build the image from the source code: 

    `pack build spring-buildpack --env BP_JVM_VERSION=21`

- create and run the container: 

    `docker run -p 8080:8080 spring-buildpack`

- see "Hello docker!" message at: 

    `http://localhost:8080/hello` 

<br /><br />

Resources: 

https://docs.spring.io/spring-boot/reference/packaging/container-images/cloud-native-buildpacks.html#packaging.container-images.buildpacks
 
https://spring.io/blog/2023/09/22/paketo-buildpacks-bionic-end-of-support

https://paketo.io/docs/howto/java/

https://bell-sw.com/blog/how-to-use-buildpacks-to-build-java-containers/


