# tomcat-microservice-openshift

A sample app to be deployed on openshift environments

## Prequisites

- a working OpenShift Cluster, e.g. [MiniShift](https://github.com/minishift/minishift)
- OpenShift Client Tools installed

## Setup

### MiniShift

If you want to use MiniShift please use at least 12 GB of RAM:

        minishift start --vm-driver virtualbox --memory 12288MB

### Pipeline

First, login and create a project:

        oc login
        oc new-project tomcat-microservice-openshift --display-name="OpenShift - Tomcat Microservice Reference Implementation"

 To setup the pipeline, process the template into cluster. This will create a pipeline which will use the Jenkinsfile from the git repository for further processing:

        oc process -f src/main/openshift/pipeline.yaml | oc apply -f -

Afterwards, you can start the pipeline from the Web UI.

## Development

To make further developments in the build pipeline, you can create your own branch and build the project against it. To build a branch called `feature-1`, create a new build configuration like this.

        oc process -f src/main/openshift/pipeline.yaml -p NAME=devel -p BRANCH=feature-1oc | oc apply -f -
