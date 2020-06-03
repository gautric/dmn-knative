
# DMN KNative Project

## Introduction

This project is a set of DMN sample running with Kogito over Docker for local env or Knative for Cloud env

## Compilation

### Maven

>  mvn clean compile quarkus:dev

### Docker

> mvn clean package -Dquarkus.container-image.build=true

### Knative

You need K8S/OCP platform with KNative Operator installed

> oc apply -f knative.yaml

## Execution

export DMN=http://localhost:8080

> curl -d @data/calculmiles-CDG-KIX-gold.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/MilesCalculation   2> /dev/null | jq 

> curl -d @data/calculmiles-CDG-JFK-silver.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/MilesCalculation   2> /dev/null | jq 

> curl -d @data/kyc.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 

> curl -d @data/kyc-false-1M-JP.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 

> curl -d @data/kyc-true-150k-US.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 


### Credits 

@mouachan

