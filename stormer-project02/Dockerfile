FROM ubuntu 
RUN apt update  
ARG DEBIAN_FRONTEND=noninteractive
RUN apt install curl wget vim git unzip  ansible gnupg ansible-lint -y
RUN curl -fsSL -o get_helm.sh \
     https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 &&  \
     chmod 700 get_helm.sh && \
     ./get_helm.sh
RUN  apt-get update -y  && \
     git clone https://github.com/ahmetb/kubectx /usr/local/kubectx && \
     ln -s /usr/local/kubectx/kubectx /usr/local/bin/kubectx  && \
     ln -s /usr/local/kubectx/kubens /usr/local/bin/kubens
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \ 
    unzip awscliv2.zip && \
       ./aws/install
RUN  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" && \ 
       curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"  && \ 
       echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check && \ 
       install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl  && \ 
       chmod +x kubectl && \ 
       mkdir -p ~/.local/bin  && \ 
       mv ./kubectl ~/.local/bin/kubectl  
