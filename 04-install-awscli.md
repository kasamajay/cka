# install aws cli

1. install aws cli from package repo (apt , or yum or apk etc depending on the linux distribution you have)
2. install aws cli download the binary from the github releases (no binaries here)
https://github.com/aws/aws-cli
3. search for install aws cli
   link to aws official documentation pages
   https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

  aws cli binary is uploaded on to aws software distribution portal
  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
  unzip awscliv2.zip
  sudo ./aws/install
  ./aws/install -i /usr/local/aws-cli -b /usr/local/bin
  sudo ./aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update

  
