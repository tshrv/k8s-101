# k8s-101
Getting started with Kubernetes


# Kubernetes
Learning basics from documentation at [https://kubernetes.io/docs/tutorials/kubernetes-basics/](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

# Module 1 - Create a Kubernetes cluster 

## Cluster up and running

We already installed minikube for you. Check that it is properly installed, by running the minikube version command:  
`minikube version`  
OK, we can see that minikube is in place.

Start the cluster, by running the minikube start command:  
`minikube start`  
Great! You now have a running Kubernetes cluster in your online terminal. Minikube started a virtual machine for you, and a Kubernetes cluster is now running in that VM.  


## Cluster version

To interact with Kubernetes during this bootcamp we’ll use the command line interface, kubectl. We’ll explain kubectl in detail in the next modules, but for now, we’re just going to look at some cluster information. To check if kubectl is installed you can run the kubectl version command:  
`kubectl version`  

OK, kubectl is configured and we can see both the version of the client and as well as the server. The client version is the kubectl version; the server version is the Kubernetes version installed on the master. You can also see details about the build.  

## Cluster details

Let’s view the cluster details. We’ll do that by running kubectl cluster-info:  
`kubectl cluster-info`  

During this tutorial, we’ll be focusing on the command line for deploying and exploring our application. To view the nodes in the cluster, run the kubectl get nodes command:  
`kubectl get nodes`  

This command shows all nodes that can be used to host our applications. Now we have only one node, and we can see that its status is ready (it is ready to accept applications for deployment).  


# Using kubectl to Create a Deployment

Objectives -
- Learn about application Deployments.
- Deploy your first app on Kubernetes with kubectl.  

## Kubernetes Deployments

Once you have a running Kubernetes cluster, you can deploy your containerized applications on top of it. To do so, you create a **Kubernetes Deployment configuration**. The Deployment instructs Kubernetes how to create and update instances of your application. Once you've created a Deployment, the Kubernetes control plane schedules the application instances included in that Deployment to run on individual Nodes in the cluster.

Once the application instances are created, a Kubernetes Deployment Controller continuously monitors those instances. If the Node hosting an instance goes down or is deleted, the Deployment controller replaces the instance with an instance on another Node in the cluster. **This provides a self-healing mechanism to address machine failure or maintenance.**

In a pre-orchestration world, installation scripts would often be used to start applications, but they did not allow recovery from machine failure. By both creating your application instances and keeping them running across Nodes, Kubernetes Deployments provide a fundamentally different approach to application management. 

A Pod is the basic execution unit of a Kubernetes application. Each Pod represents a part of a workload that is running on your cluster.  


## kubectl basics

Like minikube, kubectl comes installed in the online terminal. Type `kubectl` in the terminal to see its usage. The common format of a kubectl command is: `kubectl action resource`. This performs the specified action (like create, describe) on the specified resource (like node, container). You can use `--help` after the command to get additional info about possible parameters (`kubectl get nodes --help`).

Check that kubectl is configured to talk to your cluster, by running the kubectl version command:  
`kubectl version`

OK, kubectl is installed and you can see both the client and the server versions.  
To view the nodes in the cluster, run the kubectl get nodes command:  
`kubectl get nodes`  

Here we see the available nodes (1 in our case). Kubernetes will choose where to deploy our application based on Node available resources.  
