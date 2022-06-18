# How this repo works
The main idea of this repository is use the Openshift Pipelines(Tekton) for CI and Openshift GitOps(Argo) for CD.

There are   projects that we need to this sample:
- hello-spring-dev
- hello-spring-prod
- spring-pipeline
- nexus
- sonarqube

### Deploy and create a Nexus instance
[NEXUS](https://github.com/rafamqrs/demo-pipeline-tkn/nexus/README.md)


### Deploy SonarQube
[SONARQUBE](https://github.com/rafamqrs/demo-pipeline-tkn/sonarqube/sonarqube.adoc)


### Create the springs projects.
- hello-spring-dev
- hello-spring-prod
- spring-pipeline

We're gonna use the *spring-pipeline* project to build and run the openshift pipeline, so for that we have to give the right permission for the service account *pipeline* then it will be able to execute the necessaries tasks on the other two springs projects.

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

Ok, without futher ado, we can finally start the Continuous Integration, so we're gonna create the pipeline as img below:

![Pipeline](https://github.com/rafamqrs/demo-pipeline-tkn/imgs/pipeline.png)

### Triggers - TKN
https://dzone.com/articles/building-a-multi-feature-pipeline-with-openshift-p