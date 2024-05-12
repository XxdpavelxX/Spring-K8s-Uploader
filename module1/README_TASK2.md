## K8s Deployment

Stored in k8s-manifests folder.

### Requirements
- Zero-downtime deployments should be possible
- Data is persisted across application restarts
- The application should be exposed via Ingress

### Explanation:
To fulfill these requirements, we create several Kubernetes manifests:

Deployment: To ensure zero-downtime deployments, we use a Deployment, which allows for rolling updates. Uses image from local machine so remember to follow docker steps in README_TASK1.md

PersistentVolume and PersistentVolumeClaim: To persist data across restarts, we use a PersistentVolume and PersistentVolumeClaim.

Service: To expose the application within our K8s cluster, we use a Service.

Ingress: To expose the application outside of our k8s cluster, we an Ingress.

### Running the application in K8s:
kubectl apply -f k8s-manifests

### For local testing of application w/ k8s:
If you want to access your application via localhost:8080, you can use kubectl port-forward to forward traffic from your local machine to the Kubernetes service. 

kubectl port-forward service/celonis-app-service 8080:80

#### Cleainng up k8s resources
To delete the resoucess in k8s
kubectl delete -f k8s-manifests
