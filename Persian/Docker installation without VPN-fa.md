نصب داکر بدون قندشکن از مخازن چین

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


داکر با موفقیت نصب شد.


حالا، مخازن hub.docker.com را به مخازن روسی تغییر میدهیم.
برای انجام این کار از دستورات زیر استفاده میکنیم.


> cat > /etc/docker/daemon.json <<EOF
> { "registry-mirrors" : [ "https://https://dockerhub.firstvds.ru", "https://dockerhub.timeweb.cloud", "https://huecker.io", "https://mirror.gcr.io", "https://c.163.com", "https://registry.docker-cn.com", "https://daocloud.io" ] }
> EOF


حالا، سرویس داکر را مجددا راه اندازی میکنیم 
> sudo systemctl restart docker

مخازن داکر هاب با موفقیت تغییر یافت.
برای تست از دستور زیر استفاده میکنیم

 
> sudo docker run hello-world
