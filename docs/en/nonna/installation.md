# Installation

## 1. Requirement

+ [ikukantai](https://github.com/bonavadeur/ikukantai?tab=readme-ov-file#3-installation) Fleet is deployed, version >= 2.1
+ [Go](https://go.dev/doc/install) is installed, version >= 1.22.4
+ [Docker]() is installed. `docker` command can be invoked without sudo
+ [upx](https://upx.github.io/) is installed, version >= 4.2.4

## 2. Config `nonna` as image of queue-proxy

Edit Custom Resource **Image**.**caching.internal.knative.dev/v1alpha1** and Configmap **config-deployment** in namespace **knative-serving** to change image for queue-proxy to `nonna`, see [replace-image.sh](hack/replace-image.sh)

```bash
$ chmod +x hack/replace-image.sh
$ ./hack/replace-image.sh
```

## 3. Add configs to Configmap for Nonna

`nonna` uses these configs in ConfigMap **config-ikukantai** in namespace **knative-serving**:

| Config | Description | Value | Example |
|-|-|-|-|
| **ikukantai-enable-nonna** | enable/disable `nonna` | bool | "true", "false" |
| **nonna-threads** | number of processing threads in `nonna` | integer | "10" |

Example:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: config-ikukantai
  namespace: knative-serving
...
data:
  ...
  ikukantai-enable-nonna: 'true'
  nonna-threads: '10'
  ...
```
