# ControlPlane Training / Demo Tekton Pipeline

This repository contains a sample Tekton Pipeline specification that builds and pushes a container image to an OCI registry. The container image is based on a NodeJS "Hello World" application for demonstration purposes.

Two sets of manifests are included:

- `app-spec`: the NodeJS application specification, including sample JavaScript code and Dockerfile examples on how to build a container image for the app.
- `pipeline-spec`: the Tekton Pipeline specification, including supporting Kubernetes resources (e.g. OCI registry Secret object, PersistentVolume and PersistentVolumeClaim objects)

:warning: This is a reusable collateral for ControlPlane training courses. You are free to use this code as a starting point but don't run it in a production environment.

## Sample Application

The sample application runs a NodeJS Express web server on port `3000`.

Two Dockerfiles are provides:

- `app-spec/Dockerfile`: basic setup of NodeJS application as Docker container
- `app-spec/Dockerfile.distroless`: minimal setup of NodeJS application based on multi-stage build with a distroless image

## Sample Pipeline

Two different examples of sample Tekton pipelines are provided:

- `pipeline-spec/simple-pipeline`: sample build & push pipeline that uses Kaniko.
- `pipeline-spec/scan-pipeline`: sample pipeline that scans the container image with Aquasec Trivy before pushing it to the OCI registry.

Additional Kubernetes manifests are included in the repo, to be used alongside either Tekton Pipeline specification:

- `oci-registry/oci-registry-creds.yaml`: a Secret object with credentials for the OCI registry (e.g. Docker Hub)
- `volumes/pv.yaml`: a PersistentVolume object where the Tekton Pipeline workspace is persisted in the target Kubernetes cluster
- `volumes/pvc.yaml`: a PersistentVolumeClaim object that maps the PV.
