<img src="./img/cleanup-docker.png" width="400">

### Table of Contents

- [What Problem to solve](#what-problems-to-solve)
- [Useful command lines](#useful-command-lines)
- [Sources](#sources)

### What Problems to solve 

- This tool help you to clean-up your private docker-registry by selecting unused images in kubernetes.

### Useful command lines  

```
kubectl get pods --all-namespaces -o jsonpath="{..image}" |\
                                                     tr -s '[[:space:]]' '\n' |\
                                                     cut -d "/" -f2,3 | sort -u >> /tmp/k8s/k8s.images
```

```
your_docker_registry_client list tags $your_repo --registry=your_registry_url | sort -u >> /tmp/your_docker_registry_name/dr.images

```

```
your_docker_registry_client delete $your_repo $your_reference --registry=your_registry_url | sort -u >> /tmp/your_docker_registry_name/dr.images

```


### Sources 

- https://github.com/sky-uk/cleanup-docker-registry
- https://hub.docker.com/r/unbrokendome/docker-registry-cleanup/~/dockerfile/
- https://github.com/yodle/Docker-Registry-Cleaner
- https://github.com/cloudwatt/docker-registry-client
