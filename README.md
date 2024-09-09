# Description

A Chart project for uniovi-avib-morphingprojections-portal-chart microservice

# Deploye steps

**STEP01**: compile image

```
$ docker build --build-arg ARG_ANGULAR_PROFILES_ACTIVE=build-avib -t uniovi-avib-morphingprojections-portal:1.0.0 .
$ docker tag uniovi-avib-morphingprojections-portal:1.0.0 avibdocker.azurecr.io/uniovi-avib-morphingprojections-portal:1.0.0
$ docker push avibdocker.azurecr.io/uniovi-avib-morphingprojections-portal:1.0.0
```

**STEP02**: create a helm chart projection

```
$ helm create uniovi-avib-morphingprojections-portal-chart
```

**STEP03**: build chart package

This command will generate zip file locally with our chart configuration. The name depends on the  chart name and version configured

```
$ helm package .
```

**STEP04**: publish chart package in Azure Container Registry

This command will publish our chart package inside our ACR repository

```
$ helm push uniovi-avib-morphingprojections-portal-chart-1.0.0.tgz oci://avibdocker.azurecr.io/helm
```
