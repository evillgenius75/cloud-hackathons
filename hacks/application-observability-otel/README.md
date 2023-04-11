# Application Observability in GKE using OpenTelemetry

## Introduction

This hack will explore the options to add fine grained observability of your applications running in GKE using OpenTelemetry and Cloud Trace. The goal is to touch the least amount of code in the applications but still get rich application level telemetry to determine applications performance issues. You will use the OpenTelemetry Kubernetes Operator to auto-inject OpenTelemetry tracing into your already deployed applications.

## Learning Objectives

In this hack you will be diagnosing application performance issues getting detail application telemetry and tracing with no code changes to the application.

1. GKE Out of Box telemetry data
2. OpenTelemetry and Distributed Tracing fundamentals
3. Cloud Trace and Cloud Operations for Application Performance Management

## Challenges

- Setting Up the Environment
   - Before we can hack, you will need to set up a few things.
-  Challenge 1: Deploy a Microservice application
   - Deploy a client & server application and verify logging and metrics are being collected
- Challenge 2: Deploy the OpenTelemetry Operator
   - Configure CertManager and the OpenTelemetry Operator in the GKE Cluster
- Challenge 3: Auto-instrument the applications
   - modify the application deployments to auto-instrument the microservices based on their language/framework
- Challenge 4: Observe Tracing of application and identify root cause
   - Determine how to read Spans and understand how to track down performance issues with your applications

## Hackathon Prerequisites

- Your own GCP project with Owner IAM role.
- gCloud CLI
- kubectl and helm installed on local system
- Visual Studio Code or other editor
(optional)
- Some Golang and/or .Net/C# knowledge for advanced challenges

## Contributors

- Eddie Villalba


## Challenge 0: Setting up your Environment

### Challenge Pre-requisites

**- GCP Project with IAM Owner role**

**- latest gcloud CLI**

### Introduction

**In this challenge you will be setting up the required services to run containerized services in GKE and have cloud based observability services enabled. This challenge sets up the service scaffolding to complete the next challenges**


### Description

To have the correct services available to be successful in the upcoming challenges you will need to create a GKE cluster with workload identity and Cloud Operations Logging and Monitoring enabled. Cloud Tace will also need to be enabled for further visibility in to the application that will be deployed.


### Success Criteria

**- A zonal GKE standard cluster with 3 nodes is accessible via kubectl**

**- Cloud Logging and Monitoring are enabled and GKE dashboard is receiving information**

**- Cloud Trace Dashboard is accessible (*Note:* it will not have any traces as of yet)**


### Learning Resources

*List of relevant links and online articles that should give the attendees the knowledge needed to complete the challenge.*

**- [Creating a Zonal GKE Standard Cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/creating-a-zonal-cluster)**

**- [Cloud Trace Overview](https://cloud.google.com/trace/docs/overview)**

**- [Enable Cloud Monitoring API](https://cloud.google.com/monitoring/api/enable-api#gcloud-cli)**

**- [Enable Cloud Logging API](https://cloud.google.com/logging/docs/api/enable-api)**


### Tips

*Add tips and hints here to give students food for thought.*

**- gcloud cli is your friend for speed.**

**- Workload Monitoring in GKE has been deprecated as of 1.24 and is now part of Managed Prometheus. You can deploy a cluster with version 1.23 to enable the legacy Stackdriver workload Metrics**


### Advanced Challenges (Optional)

*Too comfortable?  Eager to do more?  Try these additional challenges!*

**- Instead of using the now deprecated Cloud Operations Workload Metrics use [Google Managed Prometheus](https://cloud.google.com/stackdriver/docs/solutions/gke/gmp-migration) in your GKE cluster**


## Challenge 1: Deploy a Microservices Application

### Challenge Pre-requisites

**- a GKE standard Cluster**

**- gcloud CLI authenticated to the correct project**

**- kubectl installed with context for the GKE cluster selected**

### Introduction

**In this challenge you will deploy a small sample multi-service application that has not been instrumented for OpenTelemetry**

### Description

**To have the correct services available to be successful in the upcoming challenges you will need to create a GKE cluster with workload identity and Cloud Operations Logging and Monitoring enabled. Cloud Tace will also need to be enabled for further visibility in to the application that will be deployed.**


### Success Criteria

**- A zonal GKE standard cluster with 3 nodes is accessible via kubectl**

**- Cloud Logging and Monitoring are enabled and GKE dashboard is receiving information**

**- Cloud Trace Dashboard is accessible (*Note:* it will not have any traces as of yet)**


### Learning Resources

*List of relevant links and online articles that should give the attendees the knowledge needed to complete the challenge.*

**- [Creating a Zonal GKE Standard Cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/creating-a-zonal-cluster)**

**- [Cloud Trace Overview](https://cloud.google.com/trace/docs/overview)**

**- [Enable Cloud Monitoring API](https://cloud.google.com/monitoring/api/enable-api#gcloud-cli)**

**- [Enable Cloud Logging API](https://cloud.google.com/logging/docs/api/enable-api)**


### Tips

*Add tips and hints here to give students food for thought.*

**- gcloud cli is your friend for speed.**

**- Workload Monitoring in GKE has been deprecated as of 1.24 and is now part of Managed Prometheus. You can deploy a cluster with version 1.23 to enable the legacy Stackdriver workload Metrics or use [Managed Prometheus](https://cloud.google.com/stackdriver/docs/solutions/gke/gmp-migration)**


### Advanced Challenges (Optional)

*Too comfortable?  Eager to do more?  Try these additional challenges!*

**- Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce commodo nulla elit, vitae scelerisque lorem maximus eu. Nulla vitae ante turpis. Etiam tincidunt venenatis mauris, ac volutpat augue rutrum sed. Vivamus dignissim est sed dolor luctus aliquet. Vestibulum cursus turpis nec finibus commodo. Vivamus venenatis accumsan neque non lacinia.**

**- Sed maximus sodales varius. Proin eu nulla nunc. Proin scelerisque ipsum in massa tincidunt venenatis. Nulla eget interdum nunc, in vehicula risus. Etiam rutrum purus non eleifend lacinia. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed quis vestibulum risus. Maecenas eu eros sit amet ligula consectetur pellentesque vel quis nisi.**
