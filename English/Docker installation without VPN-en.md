For installation Docker without VPN use Chinese repository 

> sudo apt-get update

> sudo apt-get install -y \
>     apt-transport-https \
>     ca-certificates \
>     curl \
>     software-properties-common

> curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -

> sudo add-apt-repository \
>    "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
>    $(lsb_release -cs) \
>    stable"

> sudo apt-get update

> sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin


Docker install successfully. 


Now we have to replace hub.docker.com with (Russian) repo.  To do this, just run the following command in the terminal.


> cat > /etc/docker/daemon.json <<EOF
> { "registry-mirrors" : [ "https://https://dockerhub.firstvds.ru", "https://dockerhub.timeweb.cloud", "https://huecker.io", "https://mirror.gcr.io", "https://c.163.com", "https://registry.docker-cn.com", "https://daocloud.io" ] }
> EOF


Restart Docker with the following command. 

> sudo systemctl restart docker


Docker Hub repositories successfully changed. 
For container testing, we run the following

 
> sudo docker run hello-world
