# Installation

## 1. Requirement

+ [ikukantai](https://github.com/bonavadeur/ikukantai?tab=readme-ov-file#3-installation) Fleet is deployed, version >= 2.2
+ [Go](https://go.dev/doc/install) is installed, version >= 1.22.4
+ [Docker]() is installed. `docker` command can be invoked without sudo
+ [upx](https://upx.github.io/) is installed, version >= 4.2.4

## 2. Config `katyusha` as image of Activator

Let's assume that the nodes in your cluster are named **node1**, **node2**, **node3**. See `spec.template.spec.affinity` to fill this information into the [activator-deployment.yaml](config/activator-deployment.yaml) file correctly.

Change Activator from deployed as DaemonSet to Deployment

```bash
$ kubectl -n knative-serving delete daemonset activator
$ kubectl apply -f config/activator-deployment.yaml
```

New raising Activator will deployed with image `katyusha:dev`

```bash
$ kubectl -n knative-serving get deploy activator -o yaml | grep image:
        image: docker.io/bonavadeur/katyusha:dev
```

## 3. Add configs to Configmap for Katyusha

`katyusha` uses these configs in ConfigMap **config-ikukantai** in namespace **knative-serving**:

| Config | Description | Value | Example |
|-|-|-|-|
| **ikukantai-enable-katyusha** | enable/disable `katyusha` | bool | "true", "false" |
| **katyusha-threads** | number of processing threads in `katyusha` | integer | "10" |
| **katyusha-enable-junbanmachi** | enable/disable Layer-1 Queuing feature | bool | "true", "false" |
| **katyusha-enable-fukabunsan** | enable/disable Load Balancing feature | bool | "true", "false" |
| **katyusha-enable-outoushuugou** | enable/disable Response Pool feature | bool | "true", "false" |
| **katyusha-junbanmachi-concurrent-request** | number of concurrent request in Layer-1 Queue | integer | "10" |

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
  ikukantai-enable-katyusha: 'true'
  katyusha-enable-fukabunsan: 'true'
  katyusha-enable-junbanmachi: 'true'
  katyusha-enable-outoushuugou: 'true'
  katyusha-junbanmachi-concurrent-request: '10'
  katyusha-threads: '10'
  ...
```
