# Deloitte-devops

```

ami :
ubuntu : Ubuntu Server 20.04 LTS (HVM), SSD Volume Type


inst type : t2.micro


created a keypair


-- instance created 

terminal :

moba xterm
cmd
gitbash
powershell


try to connect to instance with ssh-client

hostnamectl set-hostname docker


----

docker installation :

apt-get update -y

https://docs.docker.com/engine/install/ubuntu/


history :

 clear
    2  apt-get update -y
    3  clear
    4  sudo apt-get update
    5  sudo apt-get install     ca-certificates     curl     gnupg
    6  sudo mkdir -m 0755 -p /etc/apt/keyrings
    7  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    8  echo   "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    9  sudo apt-get update
   10  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   11  docker -v
   12  systemctl status docker
   13  docker -v
   14  history




----
 docker ps
   19  docker ps -a
   20  ps -ef | grep docker
   21  docker -h
   22  clear
   23  docker images
   24  docker run -dt httpd
   25  docker ps
   26  docker images
   27  docker run -h
   28  docker run --help
   29  clear
   30  docker run -it httpd
   31  clear
   32  docker run -it --name c1 centos:7
   33  docker ps
   34  docker ps -a
   35  docker restart c1
   36  docker ps
   37  docker run -dit --name c2 centos:7
   38  docker ps
   39  docker run -dt --name c3 centos:7
   40  docker ps
   41  docker attach c3
   42  docker ps
   43  docker run -d --name c4 centos:7
   44  docker ps
   45  docker ps -a
   46  docker start c4
   47  docker ps
   48  docker run -d --name c5 httpd
   49  docker ps
   50  history
    docker ps
   52  docker attach c5
   53  docker ps
   54  docker ps -a
   55  docker start c5
   56  docker ps
   57  docker exec -it c5 /bin/bash
   58  clear
   59  docker ps
   60  docker ps -a
   61  docker create -dt --name c6 centos:7
   62  docker create -t --name c6 centos:7
   63  docker ps
   64  docker ps -a
   65  clear
   66  docker ps -a
   67  docker stop c5
   68  docker ps -a
   69  docker rm -f c6
   70  docker ps -a
   71  docker run -it --name c7 ubuntu
   72  docker ps -a

docker run -dit --name c1 ubuntu
  108  docker ps
  109  docker run -dit --name c2 --hostname ramancontainer ubuntu
  110  docker ps
  111  docker exec -it c2 /bin/bash
  112  docker ps
  113  docker inspect c1
  114  ip a
  115  docker inspect c2
  116  clear
  117  docker ps
  118  docker rm -f `docker ps -aq`
  119  clear
  120  docker run -dit --name httpd httpd
  121  docker ps
  122  docker inspect httpd
  123  curl 172.17.0.2
  124  curl 172.17.0.2:80
  125  curl 172.31.23.145
  126  docker ps
  127  docker run -dit --name c2 -p 81:80 httpd
  128  docker ps
  129  docker inspect c2
  130  curl 172.31.23.145
  131  curl 172.31.23.145:81

```

```

Docker network and port mapping :

 docker rm -f `docker ps -aq`
  119  clear
  120  docker run -dit --name httpd httpd
  121  docker ps
  122  docker inspect httpd
  123  curl 172.17.0.2
  124  curl 172.17.0.2:80
  125  curl 172.31.23.145
  126  docker ps
  127  docker run -dit --name c2 -p 81:80 httpd
  128  docker ps
  129  docker inspect c2
  130  curl 172.31.23.145
  131  curl 172.31.23.145:81
  132  history
  133  docker ps
  134  docker images
  135  clear
  136  ip -a
  137  ip a
  138  clear
  139  docker run -dit --name webserver --network=host httpd
  140  docker ps
  141  docker run -dit --name webserver2 --network=host nginx
  142  docker ps
  143  docker ps -a
  144  docker logs webserver2
  145  clear
  146  docker ps
  147  docker exec -it webserver /bin/bash
  148  clear
  149  ls
  150  curl 172.31.23.145:80
  151  docker network ls
  152  docker network create --help
  153  docker network create --subnet 10.0.0.0/20 -d bridge raman-net
  154  docker network ls
  155  docker inspect raman-net
  156  docker ps
  157  docker ps -a
  158  docker rm -f `docker ps -aq`
  159  clear
  160  docker network ls
  161  docker run -dit  --name c1 --hostname webserver  --network raman-net nginx
  162  docker ps
  163  docker inspect c1
  164  clear
  165  docker ps
  166  docker run -dit -p 8081:80 --name c2 httpd
  167  docker ps
  168  docker rm -f c1
  169  docker ps
  170  docker run -P --name c2 nginx
  171  docker ps -a
  172  docker run -dit -P --name c2 nginx
  173  docker ps
  174  docker run -dit -P --name c1 nginx
  175  docker ps
  176  clear
  177  docker ps
  178  docker exec -it c2 /bin/bash

```

```

DOCKER VOLUMES AND TROUBLESHOOTING :
docker exec -it c2 /bin/bash
  182  docker ps
  183  docker ps -a
  184  'docker images

  185  clear
  186  docker ps
  187  cd /var/lib
  188  ls
  189  cd ..
  190  ls
  191  cd lib
  192  ls
  193  cd conainerd
  194  cd containerd
  195  l
  196  cd ..
  197  ls
  198  cd docker
  199  ls
  200  cd network/
  201  ls
  202  cd files
  203  ls
  204  cd ..
  205  ls
  206  cd ..
  207  ls
  208  cd image
  209  ls
  210  cd overla2
  211  cd overlay2
  212  ls
  213  ca repositories.json
  214  cat repositories.json
  215  docker images
  216  ls
  217  cd ..
  218  ls
  219  cd ..
  220  ls
  221  cd volumes
  222  ls
  223  cd tmp
  224  cd ..
  225  ls
  226  cd mp
  227  cd tmp
  228  ls
  229  cd ..
  230  clear
  231  cd /home/
  232  ls
  233  cd /root/
  234  ls
  235  mkdir app
  236  ls
  237  cd app/
  238  ls
  239  touch hostfile
  240  ls
  241  docker ps -a
  242  docker run -dit --name c3  -v /home/app:/data -h
  243  pwd
  244  docker run -dit --name c3  -v /root/app:/data centos:7
  245  docker ps
  246  docker attach c3
  247  docker ps
  248  docker ps -a
  249  docker sar c3
  250  docker start c3
  251  docker ps -a
  252  ls
  253  cat hostfile
  254  docker stop c3
  255  docker ps
  256  ls
  257  cat hostfile
  258  clear
  259  docker run -dit -P --name ramanweb -v /root/app:/var/tmp/www/index.html
  260  docker run -dit -P --name ramanweb -v /root/app:/var/tmp/www/index.html httpd
  261  docker ps
  262  ls
  263  docker run -dit -P --name ramanweb2 -v /root/app:/var/tmp/www/ httpd
  264  docker ps
  265  ls
  266  rm -rf hostfile
  267  vi index.html
  268  docker ps
  269  docker attach ramanweb2
  270  docker ps
  271  docker start ramanweb2
  272  docker exec -it ramanweb2 /bin/bash
  273  docker ps
  274  touch index2
  275  docker exec -it ramanweb2 /bin/bash
  276  clear
  277  docker ps -a
  278  docker logs ramanweb2
  279  docker logs -f c3
  280  docker logs -f c1
  281  docker stats
  282  docker top  ramanweb2
  283  docker top  c2
  284  docker top  c1
  285  clear
  286  docker system df
  287  docker system prune
  288  docker system df
  289  docker system prune -a
  290  docker system df

```
```
CUSTOM IMAGES :

custom images using commit method :


running container : commit : done some scripting : image-raman


docker host : nginx is not there
old docker container : c1: no nginx    >>   modufied the container (created raman dir and installed nginx ) >>>  custom image 


history of inside constainer :

 apt-get install nginx-light
   14  dpkg -l | grep -i httpd
   15  dpkg -l | grep -i nginx
   16  ls
   17  pwd
   18  mkdir raman
   19  ls
   20  cd raman/
   21  touch testfile
   22  ls
   23  nginx
   24  dpkg -l | grep -i nginx


custom image created : ramanubuntu:v1   >>> newcontainer with updated application


history of docker host :

docker images
  295  clear
  296  docker rm -f `docker ps -aq`
  297  clear
  298  docker images
  299  clear
  300  httpd
  301  dpkg -l | grep -i httpd
  302  docker run -dit --name c1 ubuntu
  303  docker ps
  304  docker images
  305  clear
  306  docker ps
  307  docker exec -it c1 /bin/bash
  308  clear
  309  docker ps
  310  docker ps -a
  311  docker images
  312  docker commit -m " added nginx and made some changes to base image" -a " RamanKhanna" c1 ramanubuntu:v1
  313  docker ps
  314  docker images
  315  docker rm -f c1
  316  docker ps -a
  317  docker images
  318  docker rmi -f httpd
  319  docker rmi -f nginx
  320  docker rmi -f ubuntu
  321  docker ps
  322  docker images
  323  clear
  324  docker run -dit --name customapp ramanubuntu:v1
  325  docker ps
  326  docker exec -it customapp
  327  docker exec -it customapp /bin/bash
  328  docker images
  329  docker image history tamanubuntu:v1
  330  docker image history ramanubuntu:v1
  331  docker events

```

```
1. Dockerfile

root@docker:~/app/app1# cat Dockerfile
FROM centos:7
RUN yum update -y
RUN yum -y install httpd


mkdir app1
  348  ls
  349  cd app1/
  350  vi Dockerfile
  351  cat Dockerfile
  352  docker images
  353  docker ps
  354  ls
  355  docker build -t custom1 .
  356  ls
  357  docker images
  358  docker image history custom1
  359  docker ps -a
  360  docker run -dit --name c1 custom1
  361  docker ps
  362  clear
  363  ls
  364  docker image
  365  docker images


```

```
2. Dockerfile :


root@docker:~/app/app2# cat Dockerfile
FROM centos:7
MAINTAINER  Raman Khanna raman.khanna@TechLanders.com
RUN mkdir /data
RUN yum update -y
RUN yum -y install httpd   php
RUN echo " TechLanders Solutions Deals in DevOps and Cloud" > /var/www/html/index.html
EXPOSE 80
VOLUME  /data
RUN echo "httpd" >> /root/.bashrc
CMD ["/bin/bash"]




cd app2
  374  ls
  375  vi Dockerfile
  376  cat Dockerfile
  377  cd ..
  378  ls
  379  cd app1
  380  ls
  381  cat Dockerfile
  382  history
  383  clear
  384  cd ..
  385  ls
  386  cd app2/
  387  ls
  388  cat Dockerfile
  389  docker build -t custom2 .
  390  docker ps -a
  391  docker images
  392  docker run -dit -P --name c2 custom2
  393  docker ps
  394  clear
  395  cat Dockerfile
  396  docker exec -it c2 /bin/bash


```

```
3. Dockerfile 

root@docker:~/app/app3# cat Dockerfile
FROM centos:7
RUN yum update -y
RUN yum install -y httpd
COPY ./index.html /var/www/html/index.html
EXPOSE 80
WORKDIR /var/www/html
CMD ["httpd","-D","FOREGROUND"]





root@docker:~/app/app3# cat index.html
 Raman from Deloitte






 mkdir app3
  405  ls
  406  cd app3
  407  ls
  408  vi Dockerfile
  409  ls
  410  cat Dockerfile
  411  ls
  412  docker build -t custom3 .
  413  docker ps
  414  docker images
  415  docker run -dit -P --name c3 custom3
  416  docker ps
  417  ls
  418  cat index.html
  419  vi index.html
  420  docker build -t custom4 .
  421  docker images
  422  docker run -dit -P --name c4 custom4
  423  docker ps

```
```
Dockerhub :
docker images
  436  docker push custom1
  437  docker login
  438  docker push custom1:latest
  439  docker tag 083792b245d7 ramann123/myimage:version1
  440  docker images
  441  docker push ramann123/myimage:version1
  442  docker images
  443  clear
  444  docker images
  445  docker rm -f `docker ps -aq`
  446  docker rmi -f custom3
  447  docker rmi -f custom2
  448  docker rmi -f custom1
  449  docker images
  450  docker rmi -f ramann123/myimage:version1
  451  docker images
  452  clear
  453  docker images
  454  docker tag f073857df32c ramann123/myimage:raman'sApp

  455  docker tag f073857df32c ramann123/myimage:ramanapp
  456  docker images
  457  docker push ramann123/myimage:ramanapp
  458  docker images
  459  docker ps
  460  docker rmi -f `docker images`
  461  clear
  462  docker imageds
  463  docker images
  464  docker pull ramann123/myimage:ramanapp
  465  docker images

```
```

KUBERNETES :


kubernetes cluster using kubeadm tool : Ubuntu 20.04 LTS - Focal , t2.medium , 20 gb storage , sg (all traffic)
1 master node 
2 worker nodes 


login into all three using terminal

hostnamectl set-hostname master
bash

```


```
TERRAFORM :


Installed terraform on centos7

We installed aws cli :

aws configure
   61  yum install -y unzip
   62  yum install -y wget
   63  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   64  unzip awscliv2.zip
   65  sudo ./aws/install
   66  ln -s  /usr/local/bin/aws  /usr/bin/
   67  aws --version


---


```
```
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "ec2" {
  ami           = "ami-06e46074ae430fba6"
  instance_type = "t2.micro"
  availability_zone= "us-east-1a"
  tags = {
    Name = "Raman-server"
  }
}




 mkdir terraform
   76  cd terraform/
   77  ls
   78  vi ec2.tf
   79  clear
   80  cat ec2.tf
   81  ls -a
   82  terraform plan
   83  terraform validate
   84  vi ec2.tf
   85  terraform validate
   86  ls -a
   87  terraform init
   88  ls -la
   89  cd .terraform
   90  ls
   91  cd providers/
   92  ls
   93  cd registry.terraform.io/
   94  ls
   95  cd hashicorp/
   96  ls
   97  cat ec2.tf
   98  cd /root/
   99  cat ec2.tf
  100  cd terraform/
  101  cat ec2.tf
  102  terraform validate
  103  terraform plan
  104  terraform apply


```

```

WOrking with other providers :



provider "github" {
  token = "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"
}

resource "github_repository" "example" {
  name        = "raman-repo"
  description = "My awesome codebase"

  visibility = "public"

}








terraform init
terraform validate
terraform plan   >> refresh
terraform apply  >> refresh / terraform apply
terraform destroy


desired state : .tf    : t2.micro
terraform.tfstate : last known good configuration : t2.micro >> t2.nano
actual state : t2.micro >> t2.nano


remote backend : s3 : terraform.state ( 20 people )


terraform state lock dynamo db







history :

cat ec2.tf
  106  history
  107  clear
  108  ls
  109  vi git.tf
  110  ls
  111  terraform validate
  112  vi git.tf
  113  terraform validate
  114  terraform init
  115  ls -a
  116  cd .terraform
  117  ls
  118  cd providers/
  119  ls
  120  cd registry.terraform.io/
  121  ls
  122  cd hashicorp/
  123  ls
  124  cd /root/
  125  cd terraform/
  126  ls
  127  terraform plan
  128  vi git.tf
  129  terraform plan
  130  terraform apply
  131  terraform destroy
  132  clear
  133  ls
  134  vi az.tf
  135  ls
  136  terraform show
  137  ls
  138  mv git.tf git
  139  ls
  140  cat terraform.tfstate
  141  terraform apply
  142  cat terraform.tfstate
  143  clear
  144  cat ec2.tf
  145  cat terraform.tfstate | grep type
  146  terraform refresh
  147  cat terraform.tfstate | grep type
  148  cat ec2.tf
  149  teraaform apply -auto-approve
  150  terraform apply -auto-approve


```
```
OUTPUT :



[root@ip-172-31-94-181 terraform]# cat ec2.tf
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "ec2" {
  ami           = "ami-06e46074ae430fba6"
  instance_type = "t2.micro"
  availability_zone= "us-east-1a"
  tags = {
    Name = "Raman-server"
  }
}

output "myawsserver-publicip" {
  value = [aws_instance.ec2.public_ip]
}

output "myawsserver-type" {
  value = [aws_instance.ec2.instance_type]
}

output "my-s3-bucket" {
  value = [aws_s3_bucket.example.bucket]
}

output "my-Eip" {
  value = [aws_eip.lb.public_ipv4_pool]
}

resource "aws_eip" "lb" {
 vpc =true
}

resource "aws_s3_bucket" "example" {
  bucket = "my-tf-test-buckettttttttttttttttttttttttttttttttttttttttsss"

  tags = {
    Name        = "My bucket raman"
    Environment = "Dev"
  }
}







terraform destroy -target aws_instance.ec2
  169  terraform destroy
  170  clear
  171  terraform show
  172  ls
  173  rm -rf git.tf
  174  vi ec2.tf
  175  terraform validate
  176  vi ec2.tf
  177  clear
  178  cat ec2.tf
  179  terraform validate
  180  terraform plan
  181  vi ec2.tf
  182  terraform plan
  183  vi ec2.tf
  184  terraform plan
  185  terraform apply -auto-approve
  186  vi ec2.tf
  187  terraform plan
  188  vi ec2.tf
  189  terraform plan
  190  terraform apply -auto-approve
  191  terraform destroy
  192  terraform show


```

```

VARIABLES CONCEPT :



[root@ip-172-31-94-181 terraform]# cat ec2.tf
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "ec2" {
  ami           = "ami-06e46074ae430fba6"
  instance_type = var.rk
  availability_zone= "us-east-1a"
  vpc_security_group_ids= [aws_security_group.raman-sg.id]
  tags = {
    Name = "Raman-server"
  }
}

resource "aws_security_group" "raman-sg" {
  name        = "raman-tfsg"
  description = "Allow TLS inbound traffic"
  vpc_id      = "vpc-0c06b56c732f0511a"

  ingress {
    description      = "TLS from VPC"
    from_port        = 443
    to_port          = 443
    protocol         = "tcp"
    cidr_blocks      = [var.cidr]
  }

  ingress {
    description      = "TLS from VPC"
    from_port        = 80
    to_port          = 80
    protocol         = "tcp"
    cidr_blocks      = [var.cidr]
  }

  ingress {
    description      = "TLS from VPC"
    from_port        = 22
    to_port          = 22
    protocol         = "tcp"
    cidr_blocks      = [var.cidr]
  }

  ingress {
    description      = "TLS from VPC"
    from_port        = 3389
    to_port          = 3389
    protocol         = "tcp"
    cidr_blocks      = [var.cidr]
  }

 ingress {
    description      = "TLS from VPC"
    from_port        = 8081
    to_port          = 8081
    protocol         = "tcp"
    cidr_blocks      = [var.cidr]
  }



  tags = {
    Name = "allow_tls"
  }
}









[root@ip-172-31-94-181 terraform]# cat variable.tf
variable "cidr" {
  default= "116.50.30.70/32"
}

variable "rk" {
  default= "t2.micro"
}






history :

terraform show
  197  vi ec2.tf
  198  terraform validate
  199  terraform plan
  200  terraform apply -auto-approve
  201  clear
  202  cat ec2.tf
  203  clear
  204  vi ec2.tf
  205  vi variable.tf
  206  cat variable.tf
  207  vi ec2.tf
  208  cat variable.tf
  209  ls
  210  vi variable.tf
  211  vi ec2.tf
  212  clear
  213  terraform validate
  214  cat ec2.tf
  215  terraform plan
  216  terraform apply -auto-approve
  217  vi ec2.tf
  218  vi variable.tf
  219  terraform validate
  220  terraform apply -auto-approve

```

```
Alias :


[root@ip-172-31-94-181 terraform]# cat ec2.tf
provider "aws" {
  region = "us-east-1"
}


resource "aws_instance" "ec2" {
  ami           = "ami-06e46074ae430fba6"
  instance_type = "t2.micro"
  availability_zone= "us-east-1a"
  tags = {
    Name = "Raman-server"
  }
}





[root@ip-172-31-94-181 terraform]# cat ec2new.tf
provider "aws" {
  region = "us-east-2"
 alias= "us2"
}


resource "aws_instance" "ec22" {
  ami           = "ami-0103f211a154d64a6"
  provider=aws.us2
  instance_type = "t2.micro"
  availability_zone= "us-east-2a"
  tags = {
    Name = "Raman-server"
  }
}


```
