# Building Docker images on Mac for the Cloud 

## Problem

Nowadays, many developers work on Mac M1/M2 machines with `arm64` CPUs. 

The Docker images that are built locally for `arm64` may not run in your Cloud provider where nodes are running `amd64` CPUs.  

You may see the error like this:

```
The requested image's platform (linux/amd64) does not match the detected host
platform (linux/arm64/v8) and no specific platform was requested
```


## Solution

By default, your Docker engine (e.g. Docker Desktop) builds images for your local CPU platform, but you may override this behavior.

There is `DOCKER_DEFAULT_PLATFORM` env variable that you can set to `linux/amd64` before building the image.

```
export DOCKER_DEFAULT_PLATFORM=linux/amd64
```
