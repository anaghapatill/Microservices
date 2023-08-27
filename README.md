## Problem Statement
Microservices are an architectural and organizational approach to software development where software is composed of small independent services that communicate over well-defined APIs. Microservices architectures make applications easier to scale and faster to develop, enabling innovation and accelerating time-to-market for new features.
Docker and Kubernetes are almost synonymous to 'microservices' as they help package and manage the different components of a project/ application, thereby easing up the implementation of a microservices architecture.

**In this project, Docker and Kubernetes has been used to make an easily deployable and portable blogging web-app using Flask and MongoDB.**  

The microservices architecture will deploy a Kubernetes cluster with a mongodb server pod fronted with a web admin interface and a pod to run the flask app.

## File Structure
```
.
|-- README.md
|-- app
|   |-- app.py
|   |-- requirements.txt
|   `-- templates
|       |-- base.html
|       |-- create-post.html
|       |-- edit-post.html
|       `-- home.html
|-- configmap.yaml
|-- deployments.yaml
|-- flask-app-image.dockerfile
|-- secret.yaml
`-- services.yaml
```
The `app` directory contains all the code pertaining to the flask app. 
The `flask-app-image.dockerfile` should specifies the insructions to assemble the docker image for the flask app.  
The `.yaml` files in the root directory specify the kubernetes manifests that will bring up the microservices deployment.


## Bringing it all together
Bring up all the microservices.
Once all the microservices are up and running,
1. Inside the flask-app pod, a python script is run to insert records into the mongodb database.
2. Run `app.py` inside the pod. Visit `http://localhost:<port>/` to view the Blog App. The Home Page should display the records inserted into the database in the previous step.
3. You can view the database frontend exposed by mongo-express. To do so, on your browser, navigate to`EXTERNAL_IP:port` exposed by the mongo-express service. 
