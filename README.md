# concourse-demo-chart

Helm chart for simple web app.

## Image

In values.yaml image.repository set as docker.artifactory.test/demo-webapp

It means what you have local docker registry named docker.artifactory.test.

## Docker login

In values.yaml imagePullSecrets set to 'regcred'

You need create secret in k8s cluster like this

After login to the docker registry (docker login docker.artifactory.test)

kubectl create secret generic regcred \
    --from-file=.dockerconfigjson=/somepath/.docker/config.json \
    --type=kubernetes.io/dockerconfigjson

## Test app

When chart deployed to the cluster use NodePort http://worknode:32080/greeting to test application.
