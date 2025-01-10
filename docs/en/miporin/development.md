# Development

Firstly, modify image used by **deployment/miporin** in namespace **knative-serving** by image named `docker.io/bonavadeur/miporin:dev`. A new Pod miporin will be raised up due to the previous changes, and this Pod will be failed. Next, build your own image for development environment:

```bash
$ kubectl -n knative-serving patch deploy miporin --patch '{"spec":{"template":{"spec":{"containers":[{"name":"miporin","image":"docker.io/bonavadeur/miporin:dev"}]}}}}'
$ chmod +x ./build.sh
$ ./build.sh ful
```

Change Endpoint IP address to IP of your machine for running `miporin` by binary:

```yaml
# file ./config/localdev.yaml
apiVersion: discovery.k8s.io/v1
kind: EndpointSlice
metadata:
  name: miporin-localdev
  namespace: knative-serving
...
endpoints:
  - addresses:
    - "192.168.122.100" # change this to be your IP, example: 192.168.189.22
```

Some util commands

```bash
# grant execute permission to build.sh file
chmod +x ./build.sh
# run code directly by binary
./build.sh local
# run miporin as a container
./build.sh ful
# push miporin image to docker registry
./build.sh push <tag>
```

