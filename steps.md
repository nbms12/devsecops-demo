
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

15. 
