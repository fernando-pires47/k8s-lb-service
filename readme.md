# Kubernetes simples LB example
Simple commands to apply k8s infrastructure using kind.

## Dependencies

* Docker
* Kind
* Kubectl

# Install resources

### Create cluster

```bash

# Create cluster
kind create cluster --name kind --config kind/cluster.yml

# Check clusters
kind get clusters

# Check cluster it's running
kubectl cluster-info --context kind-kind

```

### Install NGINX Ingress

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

### Apply resources via k8s files

```bash

# Pods and Services
kubectl apply -f k8s/pod-service.yml -n default

# Ingress
kubectl apply -f k8s/ingress-nginx.yaml -n default

```

### Check resources running

```bash

# Pods
kubectl get pod --namespace=default

# Services
kubectl get service --namespace=default

# Ingress
kubectl get ingress --namespace=default

```

### Access URL to check the functionallity

```bash

# Load Balancer
http://localhost/lb

# Foo Service
http://localhost/foo

# Bar Service
http://localhost/foo

```


# Uninstall

```bash

# Pods and Services
kubectl delete -f k8s/pod-service.yml -n default

# Ingress
kubectl delete -f k8s/ingress-nginx.yaml -n default

# Cluster
kind delete cluster --name kind

```

