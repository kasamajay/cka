# how to create kind cluster on EC2 and kubectl/k9s on workstation/local-desktop

1. create kind cluster with below 

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
networking:
  apiServerAddress: "0.0.0.0"
  apiServerPort: 7443
```

```bash
kind create cluster --config kind.yaml
```

2. check the ports listening on ec2
```bash
netstat -tuplen
```

3. make sure the security groups on ec2 (k8s api-server port)

4. copy the contents from file .kube/config

5. export KUBECONFIG=/users/kasamajay/kubeconfigs/test
   paste the .kube/config from ec2 machine

   modify the api-server hostname to kind-control-plane

6. local workstation 
   sudo vi /etc/hosts # add below line
   <public-ip-address-of-vm> kind-control-plane

7. k9s 
8. kubectl version
   kubectl get nodes -o wide
   kubectl get pods -A