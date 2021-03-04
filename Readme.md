
# DMN KNative Project

## Introduction

This project is a set of DMN sample running with Kogito over Docker for local env or Knative for Cloud env

## Install KNative Operator

### Install KNative Operator

> oc project openshift-operators

> oc apply -f knative-operator.yaml

### Install KNative Serving

> oc create namespace knative-serving

> oc apply -f knative-serving.yaml

> oc get knativeserving.operator.knative.dev/knative-serving -n knative-serving --template='{{range .status.conditions}}{{printf "%s=%s\n" .type .status}}{{end}}'

....
DependenciesInstalled=True
DeploymentsAvailable=True
InstallSucceeded=True
Ready=True
VersionMigrationEligible=True
....

## Compilation

### Maven

>  mvn clean compile quarkus:dev

### Docker

> mvn clean package -Dquarkus.container-image.build=true

### Knative

You need K8S/OCP platform with KNative Operator installed

> oc apply -f knative.yaml

## Execution

> export DMN_URL=http://localhost:8080

> curl -d @data/calculmiles-CDG-KIX-gold.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/MilesCalculation   2> /dev/null | jq 

> curl -d @data/calculmiles-CDG-JFK-silver.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/MilesCalculation   2> /dev/null | jq 

> curl -d @data/kyc.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 

> curl -d @data/kyc-false-1M-JP.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 

> curl -d @data/kyc-true-150k-US.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 


### Credits 

@mouachan

### Links


* https://docs.openshift.com/container-platform/4.6/serverless/installing_serverless/installing-openshift-serverless.html[Operator installation]
* https://docs.openshift.com/container-platform/4.6/serverless/installing_serverless/installing-knative-serving.html#serverless-install-serving-yaml_installing-knative-serving[]
* <https://knative.dev/docs/serving/>
