# How this repo works
The main idea of this repository is use the Openshift Pipelines(Tekton) for CI and Openshift GitOps(Argo) for CD.

There are some projects that we need to this sample 
    - hello-spring-dev
    - hello-spring-prod
    - spring-pipeline
    - nexus
    - sonarqube

### Deploy and create a Nexus instance
[Nexus](https://github.com/rafamqrs/demo-pipeline-tkn/nexus/README.md)


### Deploy SonarQube
[Sonar](https://github.com/rafamqrs/demo-pipeline-tkn/sonarqube/sonarqube.adoc)


### Create the projects springs projects.
- hello-spring-dev
- hello-spring-prod
- spring-pipeline

We're gonna use the *spring-pipeline* project to build and run the openshift pipeline, so for that we have to give the permission for the service account *pipeline* to the other two projects.

```shell
    oc policy add-role-to-user \
    edit \
    system:serviceaccount:spring-pipeline:pipeline \
    --rolebinding-name=pipeline-edit \
    -n hello-spring-dev
```
```shell
    oc policy add-role-to-user \
    edit \
    system:serviceaccount:spring-pipeline:pipeline \
    --rolebinding-name=pipeline-edit \
    -n hello-spring-dev
```

### Triggers - TKN
https://dzone.com/articles/building-a-multi-feature-pipeline-with-openshift-p