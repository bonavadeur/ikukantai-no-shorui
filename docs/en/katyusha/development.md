# Development

First, apply a demo application for `nonna` development:

```bash
$ kubectl apply -f config/hello.yaml
```

Take a look in [build.sh](./build.sh). There are two options for building `katyusha` image:
+ **ful**: build `katyusha` image from source, fastly but large size of image
+ **push**: like **ful** options, but slower and smaller size of image because the compression level is increased and then image will be pushed to the registry

```bash
$ ./build.sh ful # faster but larger image size
$ ./build.sh push # slower but smaller image size
```