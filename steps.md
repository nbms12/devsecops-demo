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


