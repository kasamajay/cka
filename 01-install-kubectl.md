# install kubectl

1. Install from package repository (apt repo, yum repo etc)
2. Install from git release (this isn't part of the assets on git releases)
3. download using curl/wget with links from kubernetes.io
   tasks > install tools > install kubectl
    
   curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
   curl -LO https://dl.k8s.io/release/v1.30.0/bin/linux/amd64/kubectl

   chmod +x kubectl
   sudo mv kubectl /usr/local/bin/
   kubectl version
   kubectl version --client=true

   how to know the different versions available?
     git clone https://github.com/kubernetes/kubectl
     cd kubectl 
     git tags -l | grep "1.2x" # x is based on 1.26 or 1.27 etc
    
  what version of kubectl is compatible with kubernetes cluster?
  ans. kubernetes.io > search > version skew 
  https://kubernetes.io/releases/version-skew-policy/#kubectl

4. kubectl commands

 kubectl version
 kubectl config 
 kubetctl config <sub-commands>
 kubectl config get-clusters
 kubectl config get-contexts
 kubectl set-context <>

 check the configuration for kubectl at $HOME/.kube/config
 set kubectl configuration to your desired value export  KUBECONFIG=$HOME/.kube/config

 
 

