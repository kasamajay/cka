# Steps to create k8s cluster with kubeadm tooling

1. Linode cloud, create three VMs
   <details>
      
   ```
      VM1: Ubuntu 22.04, London, 2 CPU, 4GB (linode name: master)
      VM2: Ubuntu 22.04, London, 1 CPU, 1GB (linode name: node01)
      VM3: Ubuntu 22.04, London, 1 CPU, 1GB (linode name: node02)
   ```
   
   </details>

2. install containerd, kubeadm, kubelet, kubectl (repeat this on master, node01, node02)
    <details> 
    
    ```
    ssh to master  
    git clone <ajaykasam, cka repo>
    cd cka
    sh install.sh
    ```
    
    </details>

3. `containerd` config changes (repeat this on master, node01, node02)

    <details>

      ```
       # rename hosts
       # remove the older containerd config
       # create new default containerd config, change systemdcgroup true
       hostnamectl set-hostname master # node01, node02
       cd /etc/containerd
       echo > config.toml
       containerd config default > config.toml
       # vi config.toml # edit tehe systemdcgroup = true
       systemctl daemon-reload
       systemctl restart containerd
      ```
    
     </details>

 4. kubeadm init & pod-network plugin (weavenet)
     <details>
        
     ```
     # run weavenet pod-network (overlay) addon

     https://kubernetes.io/docs/concepts/cluster-administration/addons/
     https://www.weave.works/docs/net/latest/kubernetes/kube-addon/
     
     kubeadm init # on master node
     kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
     ```
     
     </details>
     
 5. Join the worker nodes to cluster
      <details>

      ```
      # if kubeadm join command lost
      # kubeadm token create --print-join-command
      
      kubeadm join # with token and other args, run on worker nodes
      ```
      </details>



    
