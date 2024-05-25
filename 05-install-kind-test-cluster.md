# install test k8s cluster with tool like kind
1. install kind tool 
   kubernetes.io  > search for kind
   kind official page https://kind.sigs.k8s.io/
   kind github page https://github.com/kubernetes-sigs https://github.com/kubernetes-sigs/kind

   https://kind.sigs.k8s.io/docs/user/quick-start/#installation

   pre-reqs
     - docker
     - if you have golang 
        go install sigs.k8s.io/kind@v0.23.0 && kind create cluster
        This will put kind in $(go env GOPATH)/bin

     - Installing From Release Binaries

```bash
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.23.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.23.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

2. create cluster
   kind create cluster --name kind-2
   kind get clusters
   kubectl cluster-info --context kind-kind-2
   kind delete cluster

   ```yaml
   # a cluster with 3 control-plane nodes and 3 workers
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: control-plane
- role: control-plane
- role: worker
- role: worker
- role: worker
   ```

   kind create cluster --config kind-example-config.yaml

3. create a k8s cluster with specific version
  https://kind.sigs.k8s.io/docs/user/quick-start/#setting-kubernetes-version
  https://github.com/kubernetes-sigs/kind/releases
  ```yaml
  kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  image: kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55
- role: worker
  image: kindest/node:v1.16.4@sha256:b91a2c2317a000f3a783489dfb755064177dbc3a0b2f4147d50f04825d016f55
  ```
