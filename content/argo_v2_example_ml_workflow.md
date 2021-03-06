# Machine Learning Workflow on Kubernetes

This example **Deepdream demo**  shows you how to run a container-native, ML pipeline on Kubernetes using the Argo workflow engine. An Argo Workflow is a Kubernetes custom resource that consists of steps and every step runs as a container within a Kubernetes pod. Following are the steps you'll run in the **Deepdream demo** which uses [Google's Deepdream](https://hub.docker.com/r/herval/deepdream/):


* Download an image 
* Split the image
* Run multiple iterations of deep dream algorithm on different parts of the split image in parallel
* Create and store a video as artifact showing how the algorithm processed the image in every iteration 

<!-- <<Add the video>> -->

## Prerequisites
This tutorial assumes the following:

* You have set your Kubernetes context to the correct cluster
* You have successfully [installed Argo on Kubernetes](https://applatix.com/open-source/argo/get-started/installation)
* You have configured Argo ConfigMap to use Google Storage/AWS S3/Minio as Artifact Repository
* You have installed Argo CLI



## About the YAML Files

The ML workflow uses [dream.yaml](https://github.com/argoproj/image-processing-demo/blob/master/.argo-v2/dream.yaml).


## Run Deep Dream Workflow

### From Argo CLI:

```
$ argo submit ./dream.yaml

```
Get the status of the running job:


```
$ argo get <job_name>

```

Get the logs of any step in the workflow

```
$ argo logs <step_name/podname>

```


### From Browser
You can see the workflow status in the Argo Web UI. You can also check the logs and artifacts generated by each step.

![CI-workflow](../images/ciworkflow.png)
 
## Output artifact
Go to your **storage endpoint** and download your final video and intermediate images after every iteration

