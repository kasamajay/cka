# upgrade cluster

1. Upgrade control-plane node

<details>

```  
edit apt source to 1.26
apt update
k drain control-plane node
apt-cache madison kubeadm

apt install kubeadm=1.26
kubeadm upgrade plan
kubeadm upgrade apply v1.26


apt install kubelet=1.26 kubectl=1.26
systemctl daemon-reload
systemctl restart kubelet

apt-mark hold kubeadm kubectl kubelet
k uncordon localhost
```

</details>


2. upgrade worker nodes

<details>

```  
repeat for node01 node02

edit apt source to 1.26
apt update
k drain node01
apt install kubeadm=1.26
apt install kubelet=1.26 kubectl=1.26
kubeadm upgrade node
systemctl daemon-reload
systemctl restart kubelet
```

</details>

k uncordon node01
