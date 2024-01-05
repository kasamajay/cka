#1. Linode cloud, create three VMs
   VM1: Ubuntu 22.04, London, 2 CPU, 4GB (linode name: master)
   VM2: Ubuntu 22.04, London, 1 CPU, 1GB (linode name: node01)
   VM3: Ubuntu 22.04, London, 1 CPU, 1GB (linode name: node02)

#2. (repeat this on master, node01, node02)
    ssh to master  
    git clone <ajaykasam, cka repo>
    cd cka
    sh install.sh

#3  (repeat this on master, node01, node02)
    rename hosts 
    remove the older containerd config
    create new default containerd config, change systemdcgroup true
    ```
    cd /etc/containerd
    echo > config.toml
    containerd config default > config.toml
    systemctl daemon-reload
    systemctl restart containerd
    ```

 #4. kubeadm init # on master node
     # run weavenet pod-network (overlay) addon
     ```
     kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
     ```
 #5. kubeadm join # with token and other args, run on worker nodes



    
