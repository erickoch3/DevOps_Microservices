[![CircleCI](https://circleci.com/gh/erickoch3/DevOps_Microservices/tree/master.svg?style=svg)](https://circleci.com/gh/erickoch3/DevOps_Microservices/tree/master)

## Project Overview

This project operationalizes a Machine Learning Microservice API. 

We use a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can find more information about this dataset on sklearn, but the dataset will soon be deprecated. 

This project deploys a Python flask app, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

Here, we containerize the app (a prediction model), and we push the container to dockerhub. We then set up a local kubernetes cluster using minikube and deploy the container into a pod with kubectl.

### Project Objectives

The project goal is to operationalize this machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. We will do the following:
* Test the project code using linting
* Use a Dockerfile to containerize the application
* Deploy the containerized application using Docker and make a prediction
* Log application actions
* Configure Kubernetes and create a Kubernetes cluster
* Deploy the container using Kubernetes and make a prediction
* Integrate with CircleCI to start a CI pipeline

---

## Setup the Environment

* Create a virtualenv with Python 3.7 or higher activate it.
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv ~/.devops
source ~/.devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
    - `minikube start`
* Create Flask app in Container
* Run via kubectl

### Files Explanation
* .circleci
    - Contains the configuration for our CircleCI pipeline.
* model_data
    - Contains the data used to train the model.
* output_txt_files
    - Contains the logging output from docker and kubernetes for validation.
* app.py
    - The python app that makes predictions from the model.
* Dockerfile
    - Manifest that describes actions to build docker image.
* make_prediction.sh
    - Bash script to send a json POST to our prediction server
* Makefile
    - Automates common commands we need locally
* requirements.txt
    - List of dependencies for our application.
* run_docker.sh
    - Builds and runs our docker container.
* run_kubernetes.sh
    - After building the docker container, deploys it using kubernetes.
* upload_docker.sh
    - Uploads our docker container to dockerhub.
