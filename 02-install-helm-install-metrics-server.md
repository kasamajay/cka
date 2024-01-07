Installed helm on control-plane node (Official Helm documentation)
https://helm.sh/docs/intro/install/

<details>

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

</details>

Installing metrics-server using helm (its a verified helm chart, Charts page of Helm Official documentation)

<details>

```
https://artifacthub.io/packages/helm/metrics-server/metrics-server
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/
helm upgrade --install metrics-server metrics-server/metrics-server
```

</details>

Problems:
1. metrics-server pod not-ready
2. weave pod crashing
3. kube-proxy pod crashing

Problem is resolved by editing the metrics-server deployment
added --kubelet-insecure-tls flag to the command
https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/troubleshooting-kubeadm/#cannot-use-the-metrics-server-securely-in-a-kubeadm-cluster
