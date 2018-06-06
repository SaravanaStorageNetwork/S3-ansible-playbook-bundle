Deploys a APB which provide S3 service using GlusterFS backend volume.

## What it does
* Deploys a web app that provide S3 service.

## Parameters
* NAMESPACE: Optional, default 'glusterfs', Namespace to deploy the cluster in.

It expects CNS cluster is setup and running.

## Running the application
```
docker run --rm --net=host \
-v $HOME/.kube:/opt/apb/.kube:z \
-u $UID \
docker.io/ansibleplaybookbundle/gluster-s3-apb \
provision --extra-vars 'namespace=glusterfs'
```

## Tearing down the application
```
docker run --rm --net=host \
-v $HOME/.kube:/opt/apb/.kube:z \
-u $UID \
docker.io/ansibleplaybookbundle/gluster-s3-apb \
deprovision --extra-vars 'namespace=glusterfs'
```
