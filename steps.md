
NOTE : ALL THIS PROEJJCT CODES / SAMPLES / DATA ARE FORKED FROM   iam-veeramalla/devsecops-demo ( OWNER ) . ALL CREDITS GOES TO HIM . I AM JUST ADDING IMPORTANT STEPS TO MAKE UNDERSTAND MYSELF THE  PROCESS OF IMPLEMETING THIS DEVSECOPS PROJECT. 

THANKS TO ALL DEVOPS COMMUNITY AND LEARNERS.

steps: 


1. install depenencies of proejct

2. run app using > npm run dev

   ![image](https://github.com/user-attachments/assets/31b5f001-bb9b-41b4-b107-5ae1fb9171fd)



3.install docker in your host machine 


4. build image from docker file use > docker build -t tictactoe:v1 .

5. verify ur image using docker ps command

6. we can also run docker image locally using > docker run -d -p 5998:80 tictactoe:v1

7.Analyse github actions yml file ( ci-cd.yml ) , we must generate classic tokens and use them as secrets in specific any  projects 
here we use into this project to store our image in ghcr ( github container registry ) .


settings >devloper settings >  personal access token > classic token > 

![image](https://github.com/user-attachments/assets/86f9832b-8d1e-42b3-b69e-2be042e75e99)


8. under tis project add env secret, add same token value earlier created.

   ![image](https://github.com/user-attachments/assets/d23d58b0-9500-4aab-b31f-1a93ece12280)


9. docker login ghcr.io  ( login ghcr , password as token )

10. once pipeline is finished executing all jobs we can verify two images will be present .> local one and ghcr generated one.

11. Launch EC2 instance of type t2.medium/large with size of 25gb ( as we require for cluster , docker setup , argoCD )

12. instaall docker

13. run docker image on instance with desired port number an with ghcr generated image

14. open app with public ip ( check security group inbound rules for access )

15. login  ghcr > docker login ghcr.io ( usernamme and pwd as token value )

16. install kind ( tool for running local Kubernetes clusters using Docker container nodes )

    
[

For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.27.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.27.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind


]


17. create cluster > kind create cluster --name= qa-cluster-demo

18. install kubectl


     18.1   Install kubectl binary with curl on Linux

      curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"


     18.2   sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl



19.  Install Argo CD
    

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


20. kubectl get svc -n argocd

21. port forward argocd-server to some port number

    kubectl port-forward svc/argocd-server 9000:80 -n argocd --address 0.0.0.0
