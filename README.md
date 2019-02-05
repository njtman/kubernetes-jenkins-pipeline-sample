# kubernetes-jenkins-pipeline-sample

## Purpose
The purpose of this repository is to demonstration how the a simple Jenkins build pipeline
can execute using the [Kubernetes Jenkins Plugin](https://github.com/jenkinsci/kubernetes-plugin).

## How it works

### KubernetesPod.yaml
The Kubernetes Jenkins plugin gives you the ability to define a build pod inside a KubernetesPod.yaml, which would be versioned inside the repository you'd like to build.
The KubernetesPod.yaml describes the pod and the containers running in the pod.  The pod is created on demand and will live for the duration of each build.
Refer to the [Kubernetes Jenkins Plugin](https://github.com/jenkinsci/kubernetes-plugin) README in the `Pipeline support` section for technical documentation.

### Jenkinsfile
Inside the Jenkinsfile, you must specify some metadata which instructs Jenkins to read the KubernetesPod.yaml file.

Jenkins will instruct Kubernetes to launch a pod based on the criteria specified in the KubernetesPod.yaml file.
To specific pipeline steps inside a specific container, wrap the step inside a `container` block, passing a string parameter which maps to the name of the container name specified in the KubernetesPod.yaml file.
