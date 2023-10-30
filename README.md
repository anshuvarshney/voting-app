# voting-app
voting-app-using-k8s

# Example Voting App

A simple distributed application running across multiple Docker containers.

## Architecture
Through this architecture we can understand the concept of this application.

![architecture excalidraw](https://github.com/anshuvarshney/POCs/assets/115215127/08bb579f-82af-4dc0-8b7a-2785c1201d76)
 - A front-end web app in Python which lets you vote between two options
- A Redis which collects new votes
- A .NET worker which consumes votes and stores them in…
- A Postgres database backed by a Docker volume
- A Node.js web app which shows the results of the voting in real time
## Getting started

Before starting, you will need to check the Docker is running on our machine or not.  
    
     
          sudo systemctl status docker
    

## Step-1:
A front-end web app in Python which lets you vote between two options
 
- first create a directory for this project and next, change the directory to your project:

    ```bash
        mkdir example-voting-app
        cd example-voting-app
    ```
- Clone the code  
    ```bash
        git clone https://github.com/anshuvarshney/voting-app.git
    ```
- Create pod of each pod file  
    ```bash
        kubectl create -f postgres-pod.yml
        kubectl create -f redis-pod.yml
        kubectl create -f voting-app-pod.yml
        kubectl create -f worker-app-pod.yml
        kubectl create -f result-app-pod.yml
    ```
- Create service of each service   
    ```bash
        kubectl create -f redis-service.yml
        kubectl create -f result-app-service.yml
        kubectl create -f voting-app-service.yml
    ```
- List all pods and services
    ```bash
        kubectl get all
    ```
    
- Now, check voting-service url   
    ```bash
        minikube service voting-service --url
    ```  
  ![Screenshot from 2023-10-30 11-34-09](https://github.com/anshuvarshney/voting-app/assets/115215127/145f419c-d377-4d84-aa3e-821be083e666)

- Now, check result-service url
    ```bash
        minikube service result-service --url
    ```

    ![Screenshot from 2023-10-30 14-45-29](https://github.com/anshuvarshney/voting-app/assets/115215127/fb54b15f-fcc8-4d00-bb52-ea03529fa091)

   

