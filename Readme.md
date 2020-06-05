
# DMN Kogito Project

## Introduction

This project is a set of DMN sample running with Kogito.

## Compilation

### Maven

```
mvn clean compile quarkus:dev
```

## Execution

```
export DMN_URL=http://localhost:8080

curl -d @data/kyc-false-1M-JP.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 

curl -d @data/kyc-true-150k-KP.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 

curl -d @data/kyc-false-1k-CY.json -X POST -H "Content-Type: application/json"  ${DMN_URL}/KYC   2> /dev/null | jq 

```
