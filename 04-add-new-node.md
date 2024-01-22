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
    # rename hosts
    hostnamectl set-hostname nodeNN # node01, node02
    sh install.sh
    ```
    
    </details>

3. `containerd` config changes (repeat this on master, node01, node02)

    <details>

      ```
       
       # remove the older containerd config
       cd /etc/containerd
       echo > config.toml
       # create new default containerd config, change systemdcgroup true
       containerd config default > config.toml
       # vi config.toml # edit tehe systemdcgroup = true
       # restart the containerd service
       systemctl daemon-reload
       systemctl restart containerd
      ```
    
     </details>

     
 4. Join the worker nodes to cluster
      <details>

      ```
      # if kubeadm join command lost
      # kubeadm token create --print-join-command # run on master
      
      kubeadm join # with token and other args, run on worker nodes
      ```
      </details>



    
