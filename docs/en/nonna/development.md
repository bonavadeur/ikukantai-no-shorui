# Development

First, apply a demo application for `nonna` development:

```bash
$ kubectl apply -f config/hello.yaml
```

Make sure `nonna` is injected into the Pod:

```bash
$ kubectl get pod | grep hello
hello-00001-deployment-598589db69-bhwhv                  2/2     Running   0              26m

$ kubectl get pod hello-00001-deployment-598589db69-bhwhv -o yaml | grep image:
    image: index.docker.io/bonavadeur/shuka@sha256:92b17a46559202b3584a3e9e1373914ed0e66bc55ba6d3a1353312dae25de79b
    image: docker.io/bonavadeur/nonna:dev
    image: docker.io/bonavadeur/nonna:dev
    image: sha256:79054189220aa9f84fac527b4069f4ed17b6de4e6713d5d58ccfe06a17ea0dd6
```

Take a look in [build.sh](./build.sh). There are two options for building `nonna` image:
+ **ful**: build `nonna` image from source, fastly but large size of image
+ **push**: like **ful** options, but slower and smaller size of image because the compression level is increased and then image will be pushed to the registry

```bash
$ ./build.sh ful # faster but larger image size
$ ./build.sh push # slower but smaller image size
```
