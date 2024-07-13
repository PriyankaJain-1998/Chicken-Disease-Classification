# Chicken Disease Classification Project

This project involves classifying healthy and diseased chicken images using the VGG16 pretrained model. The project uses DVC to track and implement the machine learning pipeline and provides a user app for image classification, which is deployed using Docker and AWS/Azure CI/CD pipelines.

## Workflows

1. Update `config.yaml`
2. Update `secrets.yaml` [Optional]
3. Update `params.yaml`
4. Update the entity
5. Update the configuration manager in `src/config`
6. Update the components
7. Update the pipeline
8. Update `main.py`
9. Update `dvc.yaml`

## How to Run?

### Steps to Setup and Run the Project

1. **Clone the Repository**

   ```bash
   git clone https://github.com/entbappy/Chicken-Disease-Classification--Project
   cd Chicken-Disease-Classification--Project

2. Create a Conda Environment

    ```bash
    conda create -n cnncls python=3.8 -y
    conda activate cnncls

3. Install the Requirements
   ``` bash
   pip install -r requirements.txt

4. Run the Application
   ``` bash
   python app.py

5. Open Your Local Host and Port


## DVC Commands
1. Initialize DVC
   ```bash
   dvc init

2. Reproduce the Pipeline
   ```bash
   dvc repro

3. Visualize the DVC DAG
   ```bash
    dvc dag

## AWS CI/CD Deployment with GitHub Actions
1. Login to AWS Console

2. Create IAM User for Deployment with the following access:
    - EC2 access: Virtual machine
    - ECR: Elastic Container Registry to save your Docker image in AWS
  
### Deployment Steps
1. Build Docker Image of the Source Code

2. Push Your Docker Image to ECR

3. Launch Your EC2 Instance

4. Pull Your Image from ECR in EC2

5. Launch Your Docker Image in EC2

## IAM Policies
1. AmazonEC2ContainerRegistryFullAccess
2. AmazonEC2FullAccess

## ECR Repository
1. Create an ECR repo to store/save the Docker image.
2. Save the URI: 566373416292.dkr.ecr.us-east-1.amazonaws.com/chicken

## EC2 Setup
1. Create an EC2 Machine (Ubuntu)
   
2. Open EC2 and Install Docker
   ```bash
    sudo apt-get update -y
    sudo apt-get upgrade
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh
    sudo usermod -aG docker ubuntu
    newgrp docker
   
3. Configure EC2 as Self-Hosted Runner
    - Go to Settings > Actions > Runners > New self-hosted runner
    - Choose OS and run the provided commands one by one.
  
4. Setup GitHub Secrets
   ```bash
    AWS_ACCESS_KEY_ID=
    AWS_SECRET_ACCESS_KEY=
    AWS_REGION=us-east-1
    AWS_ECR_LOGIN_URI=566373416292.dkr.ecr.ap-south-1.amazonaws.com
    ECR_REPOSITORY_NAME=simple-app

## Azure CI/CD Deployment with GitHub Actions
### Save pass:
    ########################################

### Run from terminal:

    docker build -t chickenapp.azurecr.io/chicken:latest .

    docker login chickenapp.azurecr.io

    docker push chickenapp.azurecr.io/chicken:latest


## Deployment Steps

1. Build the Docker image of the Source Code
2. Push the Docker image to Container Registry
3. Launch the Web App Server in Azure
4. Pull the Docker image from the container registry to Web App server and run
   
