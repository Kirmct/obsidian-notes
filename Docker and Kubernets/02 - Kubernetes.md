When we are running up a lot of containers, kubernetes will help us to orchestrate those containeters in a more simple way.
Container Orchestrater. Making sure that all is running anda scaling correctly.

## History
- Built by Google now maintained by the Cloud Native Foundation
- Often referred to as K8S
- Container Orchestrator
- Huge subject area!
- 2 broad user profiles
	- Developer
	- Administrator

## Architecture
![[Pasted image 20250131153121.png]]


![[Pasted image 20250131153702.png]]


## Comands

### Deploy a service
To be possible to deploy a service we need to have a folder K8S and a yml file to this.
We need to be inside the folder K8S
```C#
kubectl apply -f <file name>
kubectl apply -f platforms-dep.yml
```

```C#
kubectl get deployments //we can see the deploys
kubectl get pods
```

Deleting a deployment, container image and pod image
```C#
kubectl delete deployment <deployment name>
kubectl delete deployment platforms-dep
```


Getting the service port and running on Postman or others
```C#
kubectl apply -f <file name>
kubectl apply -f platforms-np-srv.yml
```

To get the port we need to run the command to see the open services.
When we get the port is possible to use inside Postman if the service is running
```C#
kubectl get services
```

```C#
kubectl delete service <service name>
```