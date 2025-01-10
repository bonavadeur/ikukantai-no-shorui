# Installation

## 1. Requirement

+ [ikukantai](https://github.com/bonavadeur/ikukantai?tab=readme-ov-file#3-installation) Fleet is deployed, version >= 2.0
+ [ko build](https://ko.build/install/) is installed, version 0.16.0
+ [Go](https://go.dev/doc/install) is installed, version >= 1.22.4
+ [Docker]() is installed. `docker` command can be invoked without sudo

## 2. Installation

`miporin` is deployed in namespace **knative-serving**

```bash
kubectl apply -f config/miporin.yaml
```

