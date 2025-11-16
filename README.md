<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create Kubernetes Manifests

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks3)

**Author:** siddharthpk nextwork  
**Email:** siddharthpknextwork@gmail.com

---

## Create Kubernetes Manifests

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks3_b01876555)

---

## Introducing Today's Project!

In this project, I will create Kubernetes manifest files to define how my backend application is deployed and exposed within my EKS cluster. This will deepen my understanding of Kubernetes deployment mechanisms and how applications interact within the cluster, building on my previous experience deploying to EKS.

### Tools and concepts

I used Amazon EKS, eksctl, ECR, and kubectl to deploy my backend application to a Kubernetes cluster. Key concepts include using Deployment and Service manifests to define the desired state of my application, managing container images in ECR, and understanding how replicas, Pods, selectors, and matchLabels work together to ensure my application runs reliably and is accessible.

### Project reflection

I chose to do this project today because I wanted to deepen my understanding of Kubernetes deployment and how applications are packaged and managed within a cluster, especially after focusing on Deployment and Service manifests. Something that would make learning with NextWork even better is more interactive explanations or visual aids for complex Kubernetes concepts, or perhaps more projects that integrate advanced AI topics like Retrieval Augmented Generation (RAG) with Kubernetes deployments.

This project took me approximately 2 hours The most challenging part was initially articulating the precise definitions and interconnections of Kubernetes manifests, Deployments, and Services, especially understanding how selector and matchLabels tie everything together. My favourite part was seeing my backend application successfully deployed to the EKS cluster and gaining a much deeper understanding of how the Deployment and Service manifests orchestrate the application's lifecycle and exposure.

---

## Project Set Up

### Kubernetes cluster

o set up today's project, I launched a Kubernetes cluster. Steps I took to do this included using eksctl to create an Amazon EKS cluster, configuring IAM access entries for permissions, and launching EC2 instances to serve as the cluster's nodes. CloudFormation was also involved in provisioning the underlying AWS resources.

### Backend code

I retrieved the backend that I plan to deploy by installing Git and cloning the GitHub repository. The backend is the core logic of the application, responsible for processing user requests and managing data. This code is essential for building the container image and subsequently deploying the application to Kubernetes.

### Container image

Once I cloned the backend code, I built a container image because Kubernetes needs to pull the application from a container image to deploy it. I used the docker build command to create the image from the Dockerfile.

I also pushed the container image to a container registry, because Kubernetes needs to pull images from a central location for deployment, and Amazon ECR provides this secure storage. To push the image to ECR, I used the provided push commands, which included logging in, tagging the image, and then executing the docker push command.

---

## Manifest files

Kubernetes manifests are like blueprints that tell Kubernetes how to run your application in a cluster. They define the desired state of your app, including which container images to use and how to make your app available. Manifests are helpful because they make deployment simple, clear, and consistent, ensuring your app runs the same way every time without manual configuration.

A Kubernetes Deployment manages how your application runs, specifying details like the container image to use, the number of replicas, and resource limits, ensuring your app stays healthy and available. The container image URL in your Deployment manifest tells Kubernetes.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks3_b01876554)

---

## Service Manifest

A Kubernetes Service exposes your application to external traffic or other services within the cluster. You need a Service manifest to define how this exposure happens, specifying which pods to target and the ports to listen on, ensuring your app is accessible.

My Service manifest sets up a traffic controller that exposes my application to external traffic. It defines how to route this traffic to the pods labeled app:nextwork-flask-backend on port 8080, making my app accessible.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks3_b01876555)

---

## Deployment Manifest

Annotating the Deployment manifest helped me understand its precise structure and how each section, like replicas and the container image URL, directly instructs Kubernetes on managing my application's lifecycle and ensuring the desired number of Pods are running.

A notable line in the Deployment manifest is the number of replicas, which means Kubernetes will maintain that many identical copies of my application running in the cluster. Pods are relevant to this because each replica corresponds to a Pod, which is the smallest deployable unit in Kubernetes and contains my application's containers. The Deployment ensures the specified number of Pods are always healthy and running.

One part of the Deployment manifest I still want to know more about is the selector and matchLabels because I want to understand more deeply how Kubernetes uses these to identify and manage the specific Pods associated with this Deployment, and how this connection is maintained when a Service routes traffic.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-compute-eks3_6aae73e71)

---

---
